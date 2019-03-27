---
title: Commit guidelines
description: Some general guidelines to help you in writing good commits for collaboration and clarity.
---

This document was written as an overview of how an optimal commit should be written. But in the end it is still your decision , no Pull Request should be stuck in a review phase because its commits differ from the practices described below.
But if you are unsure of how to write them, this should give you a good starting point for great collaboration.

As a general guideline you can follow the idea that _a single commit should enclose a single problem/feature that has been fixed/added_.

This way of organizing your changes to the codebase makes is easy for reviewers and people who try to understand the history of a project to determine what has been happening in the project.

Here a both a good and a bad example of of commit message.

**Bad:**

```
fixes bug
```

**Good:**

```
Fixes bug where database gets deleted on POST request
```

## Breaking up large tickets

If your feature/ticket includes mutliple things that you have to complete in order to submit a pull request, these should all be seperate commit messages, according to the general guideline above. This will make it easy for the reviewer to understand what exactly has happened.
But make sure that this is a something that is done throughout your project. If another workflow is used, such as squashing all your commits together before you merge your branch into master this is not necessary. Just make sure that your commit message for the squash commit includes a detailed message of the changes. A great tool for this case is a multiline commit message.

For adding a new page in an example Project this could look like the following for separate commits:

```
Add the Person model
Configure the Views to use the new Person Model
Use the Data from the Views in the index template
```

and like this for a squashed multine commit:

```
Add Persons to the app

    - Add the Person model
    - Configure the Views to use the new Person Model
    - Use the Data from the Views in the index template
```

For more information about how to write good commit messages you can check out [this great article by Chris Beams](https://chris.beams.io/posts/git-commit/)

## Rebasing

If possible, you should try to rebase changes that are requested during the Code Review phase into your previous commits.
For more information on rebasing you can refer to the [official git documentation](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
