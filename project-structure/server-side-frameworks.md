---
title: Server-side framework suggestions
description: Guidelines for choosing the server-side technology for a new project
---

These are our suggested server-side technologies to use for website applications in specific scenarios, which should always sit within the usual [general project structure](general-structure). The focus here is on keeping the application topology [as simple as possible](project-philosophy).

## Static site generators

For a basic website that doesn't require any dynamic processing on the server, using a [static site generator](https://davidwalsh.name/introduction-static-site-generators) is recommended. Flat HTML pages will be generated at build time, leading to a deployment payload that is simply a flat collection of HTML files to be served with a simple HTTP server - usually [Nginx](https://nginx.org/en/).

This simple structure has key benefits over a dynamic application in:

- Performance: There no dynamic processing needed to serve content
- Security: There's no logic processing on the server, or accessing of other systems like databases, so much less to hack
- Predictability: There are basically no moving parts inside the deployed application, so we can have confidence in it running as expected in production
- Simplicity: The direct serving of static files is easy to understand, and one can simply inspect the built files to discover exactly the content that is served to the user

### Jekyll

[Jekyll](https://jekyllrb.com/) is our preferred static site generator, as it's by far the most common, leading to a much larger community and knowledge-base. It is simple to get started with, working sensibly with even just one plain `index.html` file. An added bonus is its use in [GitHub pages](https://pages.github.com/), which allows us to throw up quick prototypes of websites before setting up a full deployment pipeline.

*Projects using Jekyll: [cloud-init.io](https://github.com/canonical-websites/cloud-init.io); [conjure-up.io](https://github.com/canonical-websites/conjure-up.io); [design.ubuntu.com](https://github.com/canonical-websites/design.ubuntu.com); [microk8s.io](https://github.com/canonical-websites/microk8s.io); [netplan.io](https://github.com/canonical-websites/netplan.io); [vanillaframework.io](https://github.com/canonical-websites/vanillaframework.io); [mir-server.io](https://github.com/canonical-websites/mir-server.io)*

### Hugo

[Hugo](https://gohugo.io/) is a very fast generator written in Go. It's much more complicated to understand and use than Jekyll, but it generates pages [20-60 times faster](https://forestry.io/blog/hugo-vs-jekyll-benchmark/).

We recommend using Hugo only when generator speed is an important consideration - e.g. when generating a very large number of files. Jekyll builds most sites within a few seconds, and so in most cases the benefit of keeping the application simple outweigh the importance of speeding up the build.

*Projects using Hugo: [usn.ubuntu.com](https://launchpad.net/usn.ubuntu.com)*

## Dynamic Python applications

When you need logical processing on the server, you'll need a dynamic application. Examples of websites that need dynamic processing:

- Websites with a database back-end (e.g. a CMS like [partners.ubuntu.com](https://partners.ubuntu.com))
- Websites that retrieve their core content from an API (e.g. [snapcraft.io](https://snapcraft.io), [blog.ubuntu.com](https://blog.ubuntu.com))

Many websites may need to pull in related content from APIs - e.g. to show a list of related blog posts within a page. If the API content isn't central to the core application, this is usually best achieved with a client-side solution using JavaScript. This can gracefully degrade if the API cannot be reached without delaying or breaking the rest of the application. In these cases, you may not need a dynamic application.

For dynamic server-side applications, our preferred language is [Python](https://www.python.org/), a mature language with a clear focus on ease-of-use and friendliness and extensive support for web development. Our expertise is in Python, but we remain open to exploring other languages if sensible opportunities arise.

### Flask for database-less applications

[Flask](http://flask.pocoo.org/) is a simple microframework for web development with sensible defaults. For web applications that don't require a database back-end, Flask is our recommended framework as it gives you the flexibility to add as much or as little extra logic as needed.

*Projects using Flask: [snapcraft.io](https://github.com/canonical-websites/snapcraft.io); [blog.ubuntu.com](https://github.com/canonical-websites/blog.ubuntu.com); [jaas.ai](https://github.com/canonical-websites/jaas.ai); [docs.snapcraft.io](https://github.com/canonical-websites/docs.snapcraft.io)*

### Django for databases-backed applications

[Django](https://www.djangoproject.com/) is a very mature MVC framework that comes with a lot of features out-of-the-box. It is ideal for traditional CMS web applications, which require a database back-end. However, for simpler applications, the extra features can mean unnecessary complexity and bloat.

We currently use Django in many older projects without databases, where now we would choose Flask or Jekyll.

*Projects using Django: [partners.ubuntu.com](https://github.com/canonical-websites/partners.ubuntu.com); [360.canonical.com](https://github.com/ubuntudesign/360.canonical.com); [www.ubuntu.com](https://github.com/canonical-websites/www.ubuntu.com); [www.canonical.com](https://github.com/canonical-websites/www.canonical.com); [maas.io](https://github.com/canonical-websites/maas.io); [docs.ubuntu.com](https://github.com/canonical-websites/docs.ubuntu.com); [assets.ubuntu.com](https://github.com/canonical-websites/assets.ubuntu.com); [manager.assets.ubuntu.com](https://github.com/canonical-websites/manager.assets.ubuntu.com); [jp.ubuntu.com](https://github.com/canonical-websites/jp.ubuntu.com); [cn.ubuntu.com](https://github.com/canonical-websites/cn.ubuntu.com)*
