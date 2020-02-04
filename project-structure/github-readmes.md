---
title: GitHub project README files
description: Guidelines for good GitHub README.md files
---

GitHub has a few special files that provide a nice introduction to a project for the developer audience. Additionally, other users might find these pages via search engines or in filing bugs on many of our websites. So it is important to provide some details about the project, the underlying software it might be marketing and other way finding helps.

## README.md

The `README.md` is the key file on GitHub that most users will see as it is rendered at the bottom of the repo's code listing. This is the main file that people might find via search engines as well.

Here is an annotated example of a good file.

### The title

The title should be simple but explain what the repo is for. If possible, it should include a small logo of the product, or use the Ubuntu or Canonical word mark.

#### Examples

# ![ubuntu](https://assets.ubuntu.com/v1/9f61b97f-logo-ubuntu.svg "Ubuntu").com codebase

# ![snapcraft.io](https://assets.ubuntu.com/v1/944b8760-snapcraft-logo-bird.svg?fmt=png&w=50 "Snapcraft") snapcraft.io codebase

**Markdown**

```markdown
# ![ubuntu](https://assets.ubuntu.com/v1/9f61b97f-logo-ubuntu.svg "Ubuntu").com codebase
```

```markdown
# ![snapcraft.io](https://assets.ubuntu.com/v1/944b8760-snapcraft-logo-bird.svg?fmt=png&w=50 "Snapcraft") snapcraft.io codebase
```

### Badges

Badges are optional, but useful to show others the health of the project. It is important to keep these up to date, but most of the CI tools we use will have them.

#### Example

[![CircleCI build status](https://circleci.com/gh/canonical-web-and-design/ubuntu.com.svg?style=shield)](https://circleci.com/gh/canonical-web-and-design/ubuntu.com) [![Code coverage](https://codecov.io/gh/canonical-web-and-design/ubuntu.com/branch/master/graph/badge.svg)](https://codecov.io/gh/canonical-web-and-design/ubuntu.com)

**Markdown**

```markdown
[![CircleCI build status](https://circleci.com/gh/canonical-web-and-design/ubuntu.com.svg?style=shield)](https://circleci.com/gh/canonical-web-and-design/ubuntu.com) [![Code coverage](https://codecov.io/gh/canonical-web-and-design/ubuntu.com/branch/master/graph/badge.svg)](https://codecov.io/gh/canonical-web-and-design/ubuntu.com)
```

### Description

The description of the project is first and most important thing a visitor will read. It should tell them exactly what the repo is and what the underlying product is. It gives us a chance to tell users:

- What the product the website is about
- Where to see the site the repo creates
- Who made the site and what tools we use to build it

Be proud, be concise and offer links.

#### Examples

**ubuntu.com's description**

> Ubuntu is an open source software operating system that runs from the desktop, to the cloud, to all your internet connected things. [Ubuntu.com](https://ubuntu.com) is the website that helps people learn about, download and get started with Ubuntu. This repo is the codebase and content for the [ubuntu.com](https://ubuntu.com) website.
>
> The site is largely maintained by the [Web and Design team](https://ubuntu.com/blog/topics/design) at [Canonical](https://canonical.com). It is a simple, database-less, informational website project based on [Flask](https://flask.palletsprojects.com/en/1.1.x/) and hosted on a [Charmed Kubernetes](https://ubuntu.com/kubernetes) cluster.

**snapcraft.io's description**

> Snaps are applications packaged with all their dependencies to run on all popular Linux distributions from a single build. They update automatically and roll back gracefully. This repo is the application for the [snapcraft.io](https://snapcraft.io) website.
>
> If you are interested in Snaps, Snapping and Snapcraft, there is an active [discourse forum](https://forum.snapcraft.io/) that we encourage developers to join.
>
> The site is largely maintained by the [Web and Design team](https://ubuntu.com/blog/topics/design) at [Canonical](https://www.canonical.com). It is a stateless website project based on [Flask](https://flask.palletsprojects.com/en/1.1.x/) and hosted on a [Charmed Kubernetes](https://ubuntu.com/kubernetes) cluster.

**Markdown**

```markdown
Ubuntu is an open source software operating system that runs from the desktop, to the cloud, to all your internet connected things. [Ubuntu.com](https://ubuntu.com) is the website that helps people learn about, download and get started with Ubuntu. This repo is the codebase and content for the [ubuntu.com](https://ubuntu.com) website.

The site is largely maintained by the [Web and Design team](https://ubuntu.com/blog/topics/design) at [Canonical](https://canonical.com). It is a simple, database-less, informational website project based on [Flask](https://flask.palletsprojects.com/en/1.1.x/) and hosted on a [Charmed Kubernetes](https://ubuntu.com/kubernetes) cluster.
```

### Bugs and issues

This section can do three important things:

1. Welcome feedback as well as bug reports
2. Suggest people actually offer code in the form of a Pull request
3. If the bug is on the product itself, how to find the bug tracker for the underlying product, rather than misfile on the website

#### Example

**ubuntu.com's 'Bugs and issues' section**

> ## Bugs and issues
>
> If you have found a bug on the site or have an idea for a new feature, feel free to [create a new issue](https://github.com/canonical-web-and-design/ubuntu.com/issues/new), or suggest a fix by [creating a pull request](https://help.github.com/articles/creating-a-pull-request/). You can also find a link to create issues in the footer of every page of the site itself.
>
> If you have found a bug in the Ubuntu OS itself, the please file it [here](https://bugs.launchpad.net/ubuntu/).

**snapcraft.io's 'Bugs and issues' section**

> ## Bugs and issues
>
> If you have found a bug on the site or have an idea for a > new feature, feel free to [create a new issue](https://> github.com/canonical-web-and-design/snapcraft.io/issues/> new), or suggest a fix by [creating a pull request](https://> help.github.com/articles/creating-a-pull-request/). You can > also find a link to create issues in the footer of every > page of the site itself.
>
> ### Bugs in snaps and tools
>
> If you have found a bug elsewhere in the snap world:
>
> - For issues with an individual **snap** - you can run `snap > info` and use the _contact information_ to find where you > can get help.
> - In the **snapcraft tool** - that builds and publishes > snaps, [file it here](https://bugs.launchpad.net/snapcraft)
> - In **Snapd**, the daemon that manages snaps on the client, > [file it here](https://bugs.launchpad.net/snapd)

**Markdown**

```markdown
## Bugs and issues

If you have found a bug on the site or have an idea for a new feature, feel free to [create a new issue](https://github.com/canonical-web-and-design/ubuntu.com/issues/new), or suggest a fix by [creating a pull request](https://help.github.com/articles/creating-a-pull-request/). You can also find a link to create issues in the footer of every page of the site itself.

If you have found a bug in the Ubuntu OS itself, the please file it [here](https://bugs.launchpad.net/ubuntu/).
```

### Local development section

It is useful to help users who might provide a pull request or even for our own developers to know how to run the site locally. For the `README` only include the basic overview. If it is any more complicated, please provide a `HACKING` file for more details. A good example is on the [ubuntu.com repo](https://github.com/canonical-web-and-design/ubuntu.com/blob/master/HACKING.md) and another on the [snapcraft.io repo])(https://github.com/canonical-web-and-design/snapcraft.io/blob/master/HACKING.md.

#### Example

> ## Local development
>
> The simplest way to run the site locally is to first [install Docker](https://docs.docker.com/engine/installation/) (on Linux you may need to [add your user to the `docker` group](https://docs.docker.com/engine/installation/linux/linux-postinstall/)), and then use the `./run` script:
>
> `./run`
>
> Once the containers are setup, you can visit <http://127.0.0.1:8001> in your browser.
>
> For more detailed local development instructions, see [HACKING.md](HACKING.md).

````markdown
## Local development

The simplest way to run the site locally is to first [install Docker](https://docs.docker.com/engine/installation/) (on Linux you may need to [add your user to the `docker` group](https://docs.docker.com/engine/installation/linux/linux-postinstall/)), and then use the `./run` script:

```bash
./run
```
````

Once the containers are setup, you can visit <http://127.0.0.1:8001> in your browser.

For more detailed local development instructions, see [HACKING.md](HACKING.md).

````
### License section

This is the same for all our repos.  Code is licensed under LGPLv3 and content under reative Commons Attribution-ShareAlike 4.0 International license.  You can just borrow this code.

```markdown
## License

The content of this project is licensed under the [Creative Commons Attribution-ShareAlike 4.0 International license](https://creativecommons.org/licenses/by-sa/4.0/), and the underlying code used to format and display that content is licensed under the [LGPLv3](http://opensource.org/licenses/lgpl-3.0.html) by [Canonical Ltd](http://www.canonical.com/).


With ♥ from Canonical
````
