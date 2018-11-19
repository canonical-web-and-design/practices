---
layout: base
---

# Choosing a framework for a web application
An outline of the philosophy and rationale behind our recommendations for choosing software and structures for [our website applications](https://github.com/canonical-websites/).

## Philosophy
We aim to always encourage participation in our projects from both within the company and the general public. We aim to support and grow the communities that surround our work. We do this by creating web applications that are [simple](https://en.wikipedia.org/wiki/KISS_principle) for everyone to understand and use.

Our work should be [available to the public](https://en.wikipedia.org/wiki/Open_by_default), and as easy as possible for anyone to [contribute to](https://en.wikipedia.org/wiki/Open_collaboration) or learn from. This philosophy should permeate everything we do, from the software we choose to how we write [READMEs](https://robots.thoughtbot.com/how-to-write-a-great-readme) and [our code](https://developer.gnome.org/programming-guidelines/stable/writing-good-code.html.en), to how we respond to pull requests and issues.

We encourage [consistency](https://uxdesign.cc/design-principle-consistency-6b0cf7e7339f) and [building on what's gone before](https://en.wikipedia.org/wiki/Code_reuse), and so following one of our standard structures is recommended in the absence of other concerns. However, we also encourage [exploration](https://en.wikipedia.org/wiki/Exploratory_programming) and remaining open-minded to better ways to solve problems. This means that there may well be cases where a completely new stack or language may be chosen.

### In practice
Our web applications are designed as small, [focused](https://en.wikipedia.org/wiki/Unix_philosophy#Do_One_Thing_and_Do_It_Well), self-contained projects with only loose coupling to our other applications. Code should be shared between projects by writing open-source packages for inclusion in the relevant projects, and applications should share data through public APIs.

We keep our code in public GitHub repositories if possible. Each project should be simple to understand and get running without needing deep technical context or wider context about our other projects.  As far as possible, no special credentials should be necessary to get the code running.

We always intend to choose straightforward technology stacks that are no more complex than they need to be for the application in question, just as the application itself should be as simple as possible.

## General structure
Each of our projects follow a similar overall structure:

- [A `./run` script](https://github.com/canonical-webteam/practices/blob/master/local-development/the-run-script.md) which will install dependencies and run the project using [Docker](https://docs.docker.com/install/) containers
- A `package.json` which defines the basic entrypoint `scripts` to run the project in local development - this is used by the `./run` script, or can be used directly with `yarn run {command}`. It should define the following commands:
  - `serve`: Get the site running
  - `test`: Run any tests or linters associated with the project
  - `build`: Run any build steps needed ready for packaging up the project for release
  - `watch`: Run watchers to dynamically build any files as they change, for use in local development
  - `clean`: Return the project to its basic state by deleting any built or temporary files
- HTML files or templates for the website, either in the root of the project or in a `templates` directory
- A directory of `scss` files, to be built into `css` files on `build` or `watch`, for styling our websites
- A dependency on [vanilla-framework](https://vanillaframework.io/), our `scss` library for styling our websites

Within this overall structure, we can then set up our application.

## Server-side options
These are our recommendations for the server-side technology to use for website applications in specific scenarios. The focus here is on keeping the application topology as simple as possible.

### Static site generators
For a basic website that doesn't require any dynamic processing on the server, using a [static site generator](https://davidwalsh.name/introduction-static-site-generators) is recommended. Flat HTML pages will be generated at build time, leading to a deployment payload that is simply a flat collection of HTML files to be served with a simple HTTP server - usually Nginx.

This simple structure has key benefits over a dynamic application in:

- Performance: There no dynamic processing needed to serve content
- Security: There's no logic processing on the server, or accessing of other systems like databases, so much less to hack
- Predictability: There are basically no moving parts inside the deployed application, so we can have confidence in it running as expected in production
- Simplicity: The direct serving of static files is easy to understand, and one can simply inspect the built files to discover exactly the content that is served to the user

#### Jekyll
[Jekyll](https://jekyllrb.com/) is our preferred static site generator, as it's by far the most common, leading to a much larger community and knowledge-base. It is simple to get started with, working sensibly with even just one plain `index.html` file. An added bonus is its use in [GitHub pages](https://pages.github.com/), which allows us to throw up quick prototypes of websites before setting up a full deployment pipeline.

*Projects using Jekyll: [cloud-init.io](https://github.com/canonical-websites/cloud-init.io); [conjure-up.io](https://github.com/canonical-websites/conjure-up.io); [design.ubuntu.com](https://github.com/canonical-websites/design.ubuntu.com); [microk8s.io](https://github.com/canonical-websites/microk8s.io); [netplan.io](https://github.com/canonical-websites/netplan.io); [vanillaframework.io](https://github.com/canonical-websites/vanillaframework.io); [mir-server.io](https://github.com/canonical-websites/mir-server.io)*

#### Hugo
[Hugo](https://gohugo.io/) is a very fast generator written in Go. It's much more complicated to understand and use than Jekyll, but it generates pages [20-60 times faster](https://forestry.io/blog/hugo-vs-jekyll-benchmark/).

We recommend using Hugo only when generator speed is an important consideration - e.g. when generating a very large number of files. Jekyll builds most sites within a few seconds, and so in most cases the benefit of keeping the application simple outweigh the importance of speeding up the build.

*Projects using Hugo: [usn.ubuntu.com](https://launchpad.net/usn.ubuntu.com)*

### Dynamic Python applications
When you need logical processing on the server, you'll need a dynamic application. Examples of websites that need dynamic processing:

- Websites with a database back-end (e.g. a CMS like [partners.ubuntu.com](https://partners.ubuntu.com))
- Websites that retrieve their core content from an API (e.g. [snapcraft.io](https://snapcraft.io), [blog.ubuntu.com](https://blog.ubuntu.com))

Many websites may needs to pull in related content from APIs - e.g. to show a list of related blog posts within a page. If the API content isn't central to the core application, this is usually best achieved with a client-side solution using JavaScript. This can gracefully degrade if the API cannot be reached without delaying or breaking the rest of the application. In these cases, you may not need a dynamic application.

For dynamic server-side applications, our preferred language is [Python](https://www.python.org/), a mature language with a clear focus on ease-of-use and friendliness and extensive support for web development. Our expertise is in Python, but we remain open to exploring other languages if sensible opportunities arise.

#### Flask for database-less applications
[Flask](http://flask.pocoo.org/) is a simple microframework for web development with sensible defaults. For web applications that don't require a database back-end, Flask is our recommended framework as it gives you the flexibility to add as much or as little extra logic as needed.

*Projects using Flask: [snapcraft.io](https://github.com/canonical-websites/snapcraft.io); [blog.ubuntu.com](https://github.com/canonical-websites/blog.ubuntu.com); [jaas.ai](https://github.com/canonical-websites/jaas.ai); [docs.snapcraft.io](https://github.com/canonical-websites/docs.snapcraft.io)*

#### Django for databases-backed applications
[Django](https://www.djangoproject.com/) is a very mature MVC framework that comes with a lot of features out-of-the-box. It is ideal for traditional CMS web applications, which require a database back-end. However, for simpler applications, the extra features can mean unnecessary complexity and bloat.

We currently use Django in many older projects without databases, where now we would choose Flask or Jekyll.

*Projects using Django: [partners.ubuntu.com](https://github.com/canonical-websites/partners.ubuntu.com); [360.canonical.com](https://github.com/ubuntudesign/360.canonical.com); [www.ubuntu.com](https://github.com/canonical-websites/www.ubuntu.com); [www.canonical.com](https://github.com/canonical-websites/www.canonical.com); [maas.io](https://github.com/canonical-websites/maas.io); [docs.ubuntu.com](https://github.com/canonical-websites/docs.ubuntu.com); [assets.ubuntu.com](https://github.com/canonical-websites/assets.ubuntu.com); [manager.assets.ubuntu.com](https://github.com/canonical-websites/manager.assets.ubuntu.com); [jp.ubuntu.com](https://github.com/canonical-websites/jp.ubuntu.com); [cn.ubuntu.com](https://github.com/canonical-websites/cn.ubuntu.com)*
