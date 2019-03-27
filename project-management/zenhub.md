---
title: Working with ZenHub
description: How to use Zenhub in team squads
---

[ZenHub](https://zenhub.com/) is "agile project management within Github".
We use it for all squads in the design team.

[app.zenhub.com](https://app.zenhub.com) arguably has a much better board interface, however issues and pull requests can arguably be better handled within GitHub itself via the [ZenHub Chrome browser extension](https://chrome.google.com/webstore/detail/zenhub-for-github/ogcgkffhplmphkaahpmffcafajaocjbd?hl=en-GB).

Current squad boards:

- [Snappy squad tasks](https://app.zenhub.com/workspace/o/canonicalltd/snappy-design-squad/boards)
- [Web squad](https://app.zenhub.com/workspace/o/ubuntudesign/web-squad/boards)
- [MAAS design squad](https://app.zenhub.com/workspace/o/ubuntudesign/maas-design-squad/boards)
- [Juju squad](https://app.zenhub.com/workspace/o/ubuntudesign/juju-squad/boards)
- [Vanilla squad](https://app.zenhub.com/workspace/o/ubuntudesign/vanilla-squad/boards)

## Iterations

- Iterations are two weeks. They start on a Tuesday and finish on a Monday.
- Each iteration should be a milestone in ZenHub in the format `Iteration [startyear]-[startweek] [startdate] [startmonth] - [enddate] [endmonth]`.

For example `Iteration 18-27 3rd July - 16th July` followed by `Iteration 18-29 - 17th July - 30th July`.

## Epics

- Each milestone (iteration) should include all epics to be worked on.
- Epics should have everyone who will be working on it assigned.
- Epics should be in the `Iteration Epics` pipeline.
- Epics should have a description explaining the goal.

## Issues

- Issues for the current milestone should start in the `Current Iteration` pipeline.
- There should be one issue per person in the `In Progress` pipeline.
- Issues should have one assignee at any one time. If an issue requires multiple people at different stages it should be handed over and the assignee changed at the appropriate time. When reassigned, issues should be moved back into the `Current Iteration` pipeline.
- Issues that are part of an epic should have an estimate based on [the fibonacci estimation guide](https://github.com/canonical-webteam/practices/blob/master/project-management/fibonacci-estimation-guide.md).
- If for some reason you move to a different issue before completing your current issue, that issue should be labelled as “blocked”.
- Issues should have a description if the title isn't obvious.
- Issues do not need to be part of an epic, but most should.

## Pipelines

These are the lanes/ columns/ groups of issues and epics on ZenHub. Generally issues move from left to right as they progress.

### New Issues

Where issues are born. This is a general bucket of all the issues that have been and will be that have yet to be scoped or agreed on.

### Triaged

Issues that are scoped and ready to be picked up at some point in a future iteration/ if there's time left at the end of an iteration.

It's of utmost importance that triaged issues are prioritised.

### Iteration Epics

At the end of an iteration these should be either closed (if all issues are complete) or moved to the next milestone.

### Current Iteration

Issues waiting to be picked up in the current iteration. These are either issues that are yet to be started, have been reassigned or are on hold.

### In Progress

Issues being actively worked on.

Only one issue per person in the squad should be here. As much as we'd like, we can't work on 5 things at once.

If you're waiting for something/ someone to continue work on an issue, label it as “blocked”.

If you need to move on to something with a higher priority move any issue you're assigned but not working on back to `Current Iteration`.

### Review/ QA

Any issue that is deemed code/ UX/ design complete but requires a review or QA.

### Closed

Anything that is complete. The final resting place for issues and epics.
