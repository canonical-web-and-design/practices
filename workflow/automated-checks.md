---
title: Automated checks
description: How we set up automated checks for our GitHub projects
---

Every official team project should be set up to [require a number of checks to pass](https://help.github.com/en/github/administering-a-repository/enabling-required-status-checks) before a pull request can be merged.

## Prefer GitHub workflows

These check should be written as [GitHub workflows](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow) if possible. If GitHub workflows aren't fit-for-purpose, our next choice should be [Circle CI](https://circleci.com/), and _only for the specific checks_ that can't be configured as GitHub workflows.

> ⓘ At the time of writing, the chief reason to create a check in Circle CI rather than GitHub workflows is because you need to run checks against forked branches that need secrets - e.g. [Percy checks](https://percy.io/). GitHub workflows [don't currently support this](https://github.community/t5/GitHub-Actions/Make-secrets-available-to-builds-of-forks/td-p/30678).

## What to check on pull requests

All the GitHub workflows that are run on pull requests should be kept in a file called `pr.yaml`.

All website projects should run as many of the following checks as make sense:

- `run-image`: Build the docker image from the `Dockerfile` and check it successfully runs the website
- `run-dotrun`: Check the `dotrun` command (the [dotrun snap](https://snapcraft.io/dotrun)) runs the development server successfully
- `lint-scss`: Check `.scss` files conform to [our formatting standards](https://canonical-web-and-design.github.io/practices/coding/stylesheets)
- `lint-js`: Check `.js` files conform to [our formatting standards](https://canonical-web-and-design.github.io/practices/coding/javascript)
- `lint-python`: Check `.py` files conform to [our formatting standards](https://canonical-web-and-design.github.io/practices/coding/python.html)
- `test-js`: Run JavaScript tests and upload code coverage to codecov.io
- `test-python`: Run any Python tests and upload code coverage to codecov.io

> ⓘ For example, [kuberflow-news.com](https://github.com/canonical-web-and-design/kubeflow-news.com/blob/master/.github/workflows/pr.yaml)

## Running checks against master

We may also want to run some checks against the master branch to check the integrity of the codebase. An example of this might be using [`linkchecker`](https://development.robinwinslow.uk/2013/10/03/linkchecker/) to check internal links, or [Cypress](https://www.cypress.io/) to check forms. These could either be run whenever something is merged into `master`, or [on a schedule](https://help.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events-schedule).

> ⓘ For example, [Cypress checks on ubuntu.com](https://github.com/canonical-web-and-design/ubuntu.com/blob/master/.github/workflows/cypress.yml)
