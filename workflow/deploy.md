# Deploying changes to projects

Methods and principles for deploying changes to our projects.

## Principles

Important guiding principles for deploying changes to any of our projects.

### A releasable master branch

The master branch of any Git project should always be kept in a releasable state, such that it is safe for anyone to roll out a deployment from the master branch at any point, without specific context about the project in question.

### Cautious Fridays

We aim to make releasing as light-weight and risk-free as possible. Therefore, it is fine to release content changes and regular application updates at any time, including Fridays or, if necessary, over the weekend.

However, we should be careful about significant changes to the way in which applications are run, and these riskier changes should only be released between Monday and Thursday. Examples of such changes include:

- Changes to the Dockerfile like adding apt packages or updating the Ubuntu version
- Changes to the server configuration (e.g. Talisker or NGINX)
- Updating the application to integrate with a new service (e.g. consume an API, integrate with Sentry or logstash)

## Creating a new webservice

This section will present how to deploy a new service to our instance of Kubernetes.

*To deploy a new website you need to be sure that you are **not** using `bower` and the the run script uses the version **1.** of yarn.*

### Create a dockerfile of your service

To deploy you service to Kubernetes you need to have an image of your project. You can have a look in the [Dockerfile](https://docs.docker.com/engine/reference/builder/) of the [www.ubuntu.com](https://github.com/canonical-websites/www.ubuntu.com/blob/master/Dockerfile)

### Create the Kubernetes configuration

All deployment configurations are saved in [the deployment-configs repository](https://github.com/canonical-webteam/deployment-configs/). To deploy new services and ingress create a pull request with the website you want to add.

We created a script to automatically create the configuration you need. Clone the deployment-config repository, and run the script `create-project`:

```bash
$ git clone https://github.com/canonical-webteam/deployment-configs.git
$ cd deployment-configs
$ python create-project <DNS_OF_THE_WEBSITE>
```

### Create jobs on Jenkins

In order to deploy to Kubernetes you will need to create 2 Jenkins jobs on the webteam [instance](https://jenkins.canonical.com/webteam/): one for staging and one for production.

Update the **apply** job:
* Go to the [configure page](https://jenkins.canonical.com/webteam/job/apply-production-deployment-configs/configure)
* Add these lines:
```bash
export TAG_TO_DEPLOY=$(kubectl get deployment <DNS_OF_THE_WEBSITE_WITH-DASHES> --namespace production --output jsonpath="{.spec.template.spec.containers[*].image}" | grep -P -o '(?<=:)[^:]*$')
envsubst < services/<DNS_OF_THE_WEBSITE>.yaml | kubectl apply --namespace production --filename -

[...]

kubectl apply --namespace production --filename ingresses/production/<DNS_OF_THE_WEBSITE>.yaml
```

Create the **staging** job:

 * Create a [New Item](https://jenkins.canonical.com/webteam/view/all/newJob):
   * Item name: *deploy-to-<STAGING_DNS>*
   * Copy from (at the bottom the page): *deploy-to-design.staging.ubuntu.com*
 * Change those parameters on the configuration page:
   * *General* -> *Github project*: insert the Github repository
   * *Source code management* -> *Repositories* -> *Repository URL*: insert the Github repository
   * *Build*: Update the script with the rights values
 * Save

Create the **production** job:

 * Create a [New Item](https://jenkins.canonical.com/webteam/view/all/newJob):
   * Item name: *deploy-to-<PRODUCTION_DNS>*
   * Copy from (at the bottom the page): *deploy-to-design.ubuntu.com*
 * Change those parameters on the configuration page:
   * *Build*: Update the script with the rights values
 * Save

#### Jobs examples

These examples are from the design.ubuntu.com project. Please adapt the sripts before using them:

##### Staging

```bash
#!/bin/bash --login

# Bash strict mode
set -euo pipefail

# Settings
export image_name="prod-comms.docker-registry.canonical.com/design.ubuntu.com:${GIT_COMMIT}"

# Build docker image
if ${clean}; then ./run clean; fi
./run build
docker build --pull --build-arg HTTPS_PROXY=${HTTPS_PROXY} --build-arg COMMIT_ID=${GIT_COMMIT} --tag ${image_name} .

# Push to registry
docker push ${image_name}

# Deploy the new image
kubectl set image deployment/design-ubuntu-com --namespace staging design-ubuntu-com=${image_name}

# Wait for the deployment to finish
kubectl rollout status deployment/design-ubuntu-com --namespace staging --watch

echo ""
echo "==="
echo "Image: ${image_name}"
echo "Deployed to https://design.staging.ubuntu.com"
echo ""
echo "To deploy to production, run:"
echo "https://jenkins.canonical.com/webteam/securityRealm/commenceLogin?from=%2Fwebteam%2Fjob%2Fdeploy-to-design.ubuntu.com%2Fparambuild%2F%3Fimage_tag%3D${GIT_COMMIT}"
echo "==="
```

##### Production

```bash
#!/bin/bash --login

# Bash strict mode
set -euo pipefail

# Settings
export base_image_name="prod-comms.docker-registry.canonical.com/design.ubuntu.com"

# Release the image
kubectl set image deployment/design-ubuntu-com --namespace production design-ubuntu-com=${base_image_name}:${image_tag}

# Wait for the deployment to finish
kubectl rollout status deployment/design-ubuntu-com --namespace production --watch

echo ""
echo "==="
echo "Image: ${base_image_name}:${image_tag}"
echo "Deployed to https://design.ubuntu.com"
echo "==="
echo ""

echo "Updating ${base_image_name}:latest:"
docker pull ${base_image_name}:${image_tag}
docker tag ${base_image_name}:${image_tag} ${base_image_name}:latest
docker push ${base_image_name}:latest

echo ""
echo "==="
echo "Image: ${base_image_name}:${image_tag}"
echo "Deployed to https://design.ubuntu.com"
echo "And pushed to ${base_image_name}:latest"
echo "==="
echo ""
```

### First deployment

For the first deployement go on the apply job and update the line you added previously. You need to change the variable `TAG_TO_DEPLOY` with the hash of the last commit in the project. 

Once this tag is updated you can run the job apply, then staging and if nothing fails production.

If the DNS is not ready yet add a line to your `/etc/hosts` with the ip of the Kubernetes instance and your DNS.

### Request new certificates

[Submit an RT](https://wiki.canonical.com/ProductStrategyTeam/WebDevelopment/CreatingRTs) to ask IS to create two new Kubernetes secrets:

- "example-ubuntu-com-tls": A kubernetes secret containing the TLS key, certificate and chainfile for the staging domain (e.g. example.staging.ubuntu.com)
- "example-ubuntu-com-tls": A kubernetes secret containing the TLS key, certificate and chainfile for the production domain (e.g. example.ubuntu.com)

### Request DNS update

[Submit an RT](https://wiki.canonical.com/ProductStrategyTeam/WebDevelopment/CreatingRTs) to update the DNS to point the new domains at our Kubernetes ingress at `prod-comms.kubernetes-ingress.canonical.com`
