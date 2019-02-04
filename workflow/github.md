---
title: Working on GitHub
description: How to contribute to our GitHub projects
---

This document outlines the rules to contribute and to create issues to a project on the organisation [Canonical-websites](https://github.com/canonical-websites/)

## Table of content

- [Working on GitHub](#working-on-github)
  - [Table of content](#table-of-content)
  - [How can I contribute?](#how-can-i-contribute-)
    - [Report bugs](#report-bugs)
    - [Suggest enhancements](#suggest-enhancements)
    - [Work on an issue](#work-on-an-issue)
  - [Pull requests](#pull-requests)
    - [First contribution](#first-contribution)
    - [Styleguides](#styleguides)
    - [Merging process](#merging-process)
  - [Templates](#templates)
    - [Issues template](#issues-template)
    - [Pull request template](#pull-request-template)

## How can I contribute?

In the Canonical web-sites organisation we work with Github. All types of work are tracked as GitHub issues. You will find in this section how you can contribute to this organisation.

### Report bugs

Well done you have found a bug! Go to the corresponding project, it should be in the [Canonical websites organisation](https://github.com/canonical-websites/) and open an issue. These are the steps you need follow to add an issue:

- **Title:** should describe your feature/bug
- **Description:** fill this [template](#issues-template)
- **Add labels:** see [labels description](./labels.md)
- **Submit your issue:** we will try to fix it as soon as possible!

### Suggest enhancements

If you think details could change on our websites you can suggest enhancements by creating a new issue. These are the steps you need follow to suggest enhancements:

- **Title:** should describe your feature/bug
- **Description:** fill this [template](#issues-template)
- **Screenshots:** Don’t forget to add screenshots of suggestion designs to explain
- **Add labels:** see [labels description](./labels.md)
- **Submit your issue:** we will try to fix it as soon as possible!

### Work on an issue

You are welcome to pick up any unassigned issue on any of our projects - simply assign yourself to the issue, fork the project and start work. Once you finish your work open a [pull request](#pull-request).

## Pull requests

In this section you will find a description on how to create a pull request for a Canonical Web-sites project. These are the steps to create a pull request:

- Fill the [template](#pull-request-template)
- Make sure the tests are OK
- Make sure the [styleguides](#styleguides) are respected
- Add the [labels](./labels.md)

### First contribution

If you want to create a pull request you will need to fork the project you are working on. From your fork, create a branch and work on your issue.

### Styleguides

When making changes to any of our projects, please follow our styleguides:

- [HTML](../coding/html.md)
- [JavaScript](../coding/js.md)
- [stylesheets](../coding/stylesheets.md)
- [written content](https://github.com/canonical-webteam/practices/blob/master/content/copy-reviews.md#checklist)

Along with any common community standards (e.g. [Python's PEP8](https://www.python.org/dev/peps/pep-0008/)).

If we haven't written a styleguide for the language you're working in, please feel free to [suggest one](https://github.com/canonical-webteam/practices/blob/master/CONTRIBUTING.md).

### Merging process

Here are the steps that need to be completed before merging:

- All [review labels](./labels.md#review) have to be at +1
- Your pull request must be approved by at least one person
- Any automated checks must have passed
- The original author should merge a pull request
  - This can be overruled when necessary, only if the author is unavailable
  - Special care should be taken to ensure there have been no further changes requested

## Templates

### Issues template

```
## Summary

[please describe the issue]

## Process

[list the steps to replicate the issue]

## Current and expected result

[describe what happened and what you expected]

## Screenshot

[if relevant, include a screenshot]
```

### Pull request template

```
## Summary

[please describe the issue]

## Process

[list the steps to replicate the issue]

## Current and expected result

[describe what happened and what you expected]

## Screenshot

[if relevant, include a screenshot]

## Issues

[if relevant, include a list of issues that this pull request will have an impact on]
```
