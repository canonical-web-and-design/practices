---
title: The basic structure of our projects
description: The basic structure for our projects
---

Each of our projects follow a similar overall structure, intending to follow [our philosophy for projects](project-philosophy):

- [A `./run` script](https://github.com/canonical-webteam/practices/blob/master/local-development/the-run-script.md) which will install dependencies and run the project using [Docker](https://docs.docker.com/install/) containers
- A `package.json` which defines the basic entry point and `scripts` to run the project in local development - this is used by the `./run` script, or can be used directly with `yarn run {command}`. It should define the following commands:
  - `serve`: Get the site running
  - `test`: Run any tests or linters associated with the project
  - `build`: Run any build steps needed ready for packaging up the project for release
  - `watch`: Run watchers to dynamically build any files as they change, for use in local development
  - `clean`: Return the project to its basic state by deleting any built or temporary files
- HTML files or templates for the website, either in the root of the project or in a `templates` directory
- A directory of `scss` files, to be built into `css` files on `build` or `watch`, for styling our websites
- A dependency on [vanilla-framework](https://vanillaframework.io/), our `scss` library for styling our websites

Within this overall structure, we can then [set up our application](server-side-frameworks).