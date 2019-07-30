---
title: Project interface
description: The standard interface for our projects - package.json and entrypoint
---

Our projects should all include [a `package.json` file](https://yarnpkg.com/lang/en/docs/package-json/) at the top-level of the project, which defines the standard ways the project should be run.

The `package.json` file should define some [`scripts`](https://yarnpkg.com/lang/en/docs/package-json/#toc-scripts), and (usually) some [`dependencies` and `devDependencies`](https://yarnpkg.com/lang/en/docs/package-json/#toc-dependencies).

## scripts

These defined `scripts` can be run either with `yarn run {script-name}` or through [our local development tooling](https://canonical-web-and-design.github.io/practices/project-structure/the-run-script.html).

Our standard script names:

- `start`: The standard entrypoint for local development. It should run any required watchers for rebuilding files as they change, and run any local development servers etc..
  - E.g.: `concurrently 'yarn run watch' 'yarn run serve'`
- `build`: Build all the required assets for the project to be published. This may simply run a number of other scripts per filetype, e.g.:
  - `build-js`: Build the JavaScript files
  - `build-css`: Build any SCSS files etc. into CSS
- `serve`: Run the a local webserver. This will typically use the same `./entrypoint` script as is used by the production Docker image (see below).
- `watch`: Watch for changes in any relevant files. Again, this may be split up into sup-scripts by filetype, e.g.:
  - `watch-js`: Watch for changes in JavaScript files and rebuild as needed.
  - `watch-css`: Watch for changes in SCSS files and rebuild CSS as needed.
- `test`: Run all tests. This may be split into sub-scripts by filetype, e.g.:
  - `test-js`: JavaScript tests.
  - `test-python`: Python tests.
  - `lint-js`: Check JavaScript format.
  - `lint-python`: Check Python format with `black` and `flake8`.
  - `lint-css`: Check CSS format.
- `format`: Reformat all files with our standard formatters. This may be split into sub-scripts by filetype, e.g.:
  - `format-python`: Format Python with `black --line-length 79`
  - `format-js`: Format JavaScript with Prettier
  - `format-css`: Format SCSS files with Prettier

Basically every project should define at least `start` and `build`. All website projects should define `serve`. Any project may define any number of further scripts, as needed.

## Publishing websites and `entrypoint`

We publish our website projects by building Docker images from them for deploying to our Kubernetes cluster. We build these images with e.g.:

```bash
yarn run build
docker build --build-arg TALISKER_REVISION_ID={build-id} .
```

To enable this, each website projects should contain a `Dockerfile` at the root of the project. This Dockerfile will typically be run a server through a file called `./entrypoint`, e.g.:

```dockerfile
# Setup commands to run server
ENTRYPOINT ["./entrypoint"]
CMD ["0.0.0.0:80"]
```

`package.json`, the `node_modules` folder and any other unused files should usually not be included or used in our published images, and should be ignored through `.dockerignore`.
