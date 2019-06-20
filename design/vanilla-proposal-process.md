---
title: Vanilla proposal process
description: What to do when proposing a new or updating an existing Vanilla component
---

This document describes and illustrates the process of proposals to Vanilla.

## Proposal process

When creating a proposal for Vanilla we have a process flow to guide you through to find out your requirements, and whether your proposal is valid to be pushed up into Vanilla:

**Component already exists**

- Does it fulfil all requirements?
- Can it be amended to suit your new requirements while still fulfilling existing requirements?

**Component doesn't already exist**

- Does something similar already exist?
- Is this something that can be reused in more than one site or application?
- Can you make it more generic?

### Flow diagram

An illustrative example to understand the process flow better.

![](https://raw.githubusercontent.com/canonical-web-and-design/design-vanilla-framework/master/Process%20diagram/Vanilla%20Proposal%20Process.png)

## Step-by-step guide

Create a GitHub [issue](https://github.com/canonical-web-and-design/vanilla-framework/issues/new?template=propose-new-pattern.md) following our proposal template and adding the label "WG: Proposal".

- 1. Proposal discussed in bi-weekly working group meeting
- 2. Discarded if invalid. If validated it's marked "WG: Validated" label and it's placed in the backlog. If design is not finalised, the issue will be moved to design-vanilla-framework repo until the design spec is created.
- 3. Once development starts it passes through a Code review and it's then merged to master branch.
- 4. When Design QA is complete, it's cleared for release.

## Working group

This is a bi-weekly meeting to discuss new and existing Vanilla components, look at proposals in the GitHub project and discuss any other issues or questions regarding our framework.

You should attend this meeting if you:

- Are working on any new patterns that you think would be important to discuss
- Have submitted a new component proposal
- Have a component proposal that is in development
- Have any other Vanilla-related topics you want to discuss or want to be up-to-date on Vanilla
