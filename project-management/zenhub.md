# Working with ZenHub

[ZenHub](https://zenhub.com/) is "agile project management within Github".
We use it for all squads in the design team.

Use [app.zenhub.com](https://app.zenhub.com), it's much nicer :).

Current squad boards:

- [Snappy squad tasks](https://app.zenhub.com/workspace/o/ubuntudesign/snappy-squad-tasks/boards)
- [Web squad](https://app.zenhub.com/workspace/o/ubuntudesign/web-squad/boards)
- [MAAS design squad](https://app.zenhub.com/workspace/o/ubuntudesign/maas-design-squad/boards)
- [Juju squad](https://app.zenhub.com/workspace/o/ubuntudesign/juju-squad/boards)
- [Vanilla squad](https://app.zenhub.com/workspace/o/ubuntudesign/vanilla-squad/boards)

## 1. Iterations

- Each iteration should be a milestone in ZenHub in the format `Iteration [Iteration number]-[enddate].[endmonth]`.

 For example `Iteration 9-20.10` followed by `Iteration 10-3.11`.

## 2. Epics

- Each milestone (iteration) should include all epics to be worked on.
- Epics should have everyone who will be working on it assigned.
- Epics should always be in the `Iteration Epics` pipeline (see 4.3).
- Epics should have a description explaining the goal.

## 3. Issues

- Issues for the current milestone should start in the `Current Iteration` pipeline (see 4.4).
- There should be only one issues per person in the `In Progress` pipeline (see 4.5).
- Issues should only have one assignee at any one time. If an issue requires multiple people at different stages it should be handed over and the assignee changed at the appropriate time. When reassigned, issues should be moved back into the `Current Iteration` pipeline.
- Issues should have an estimate based on [the fibonacci estimation guide](https://github.com/canonical-webteam/practices/blob/master/project-management/fibonacci-estimation-guide.md).
- If for some reason you move to a different issue before completing your current issue, that issue should be moved in to either the `Current Iteration` or `Blocked` pipelines.
- Issues should have a description if the title isn't obvious.
- Issues do not need to be part of an epic, but most should.

## 4. Pipelines

These are the lanes/ columns/ groups of issues and epics on ZenHub. Generally issues move from left to right as they progress.

### 4.1 New Issues

Where issues are born. This is a general bucket of all the issues that have been and will be that have yet to be scoped or agreed on.

### 4.2 Triaged

Issues that are scoped and ready to be picked up at some point in a future iteration/ if there's time left at the end of an iteration.

### 4.3 Iteration Epics

As the name suggests, the current iterations epics. Nothing more, nothing less.

At the end of an iteration these should be either closed (if all issues are complete) or moved to the next milestone.

### 4.4 Current Iteration

Issues waiting to be picked up in the current iteration. These are either issues that are yet to be started, have been reassigned or are on hold, but not blocked.

Any issue moving from `In Progress` to `Current Iteration` would ideally have a comment explaining why the issue has been moved.

### 4.5 In Progress

Issues being actively worked on.

Only one issue per person in the squad should be here. As much as we'd like, we can't work on 5 things at once.

If you're waiting for something/ someone to continue work on an issue, move it to the `Blocked` pipeline.

If you need to move on to something with a higher priority move any issue you're assigned but not working on back to `Current Iteration`.

### 4.6 Blocked

Issues that are blocked for any reason. All blocked issues should have a comment explaining why they're blocked.

### 4.7 Review/ QA

Any issue that is deemed code/ UX/ design complete but requires a review or QA.

### 4.8 Closed

Anything that is complete. The final resting place for issues and epics.
