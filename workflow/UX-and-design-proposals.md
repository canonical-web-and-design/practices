---
title: UX/design proposals, sharing process & feedback convention
description: How to share UX & design proposals and guidelines on feedback convention
---

This document outlines the guidelines on our tools (e.g. Miro, Zeplin, GitHub) across the different disciplines and the different phases of a project. 

## Table of content

- [Feedback convention (across tools)](#feedback-convention)
- [What tools do we use?](#what-tools-do-we-use)
  - [Miro](#miro)
  - [Docs and Specs](#docs-and-specs)
  - [Zeplin](#zeplin)
  - [General direction](#general-direction)
- [Zeplin/Miro status convention](#zeplin-miro-status-convention)
  - [Status and tags](#status-and-tags)
  - [Projects name](#projects-name)
  - [Sections name](#sections-name)
  - [Links to specs/docs/epics](#links-to-specs-docs-epics)
- [Who is it for?](#who-is-it-for)
- [Inviting people to projects](#inviting-people-to-projects)
- [When do we comment?](#when-do-we-comment)
  - [Directions](#directions)
  - [Does it need a comment?](#does-it-need-a-comment)
- [Resolving comments](#resolving-comments)


## Feedback-convention

Problems: semantic gap, hard to categorise the feedback,  need a way to receive feedback that can help us redesign the wireframes better and understand the motivation behind the feedback.
 
Start your comment with:

**1. I like… (tag a green colour on the Zeplin comment)**
For components that you like and that we should keep it.
 
**2. I wish… (tag a yellow colour on the Zeplin comment)**
For components that you think
- Can be improved
- Disagree with and would like to propose an alternative behaviour
- Would like to patternised
- Need clarification (express which part is confusing)
- If you have a question, please formulate it as "I wish...", this will be really helpful to learn about what you have in mind.
 
**3. INFO: (tag a purple colour on the Zeplin comment)**
- When you don’t want to express an opinion, but would like to share information, caveat, or references that might have been missed or overlooked in the prototype/wireframe.


## What tools do we use?

### Miro
Miro is very valuable especially during the discovery and definition phase. You might want to consider starting in Miro during the definition and the initial stage of the project with core engineers instead of Zeplin.

### Doc and Specs
Spec docs with core engineers are also very important for the definition of the feature and to start a conversation around API, user stories and functionality.

### Zeplin
When ready for wireframes it can then move to Zeplin. Use tags and naming convention in a way that reflects the status of the project.

### General direction
We should work more on documents/specs to discuss things first, back and forth with engineers to discuss sketches about scope before moving to Zeplin for further feedback.


## Zeplin/Miro status convention

### Status & tags
Status can be used to display the phase of the project so that people know you are looking for feedback reflecting that status, e.g.: ‘explorations’ (UX phase, asking for UX and scoping type of feedback, including implementation constraints and feasibility).

### Status terminology:
**Discovery**
- Work on specs
- Definition phase
- Conceptual work
- User interviews
- Core engineers and stakeholders sync
- Personas, user stories
- Use cases, scenarios

**Exploration**
- First iterations of sketches/wireframes after spec & definition
- Final UX proposal (last wireframe to conclude UX)

**Visual**
- Design stage
- Feedback on the visual

**Development**
- This is ready to be implemented
- Highlight implementation specs, annotation

### Proposed tags, to be added for review stages
We discussed reflecting the tag-naming convention from GitHub when asking for a certain type of feedback:
- Review: UX needed
- Review: Design needed
- Review: QA needed


## Projects name

Name your projects this way, using the year and the month of the cycle the project refers to:  “YY.MM Product - Project”, e.g. : “20.04 Snap - Progressive release”.

## Sections name

- Name your sections and your artboards so they make sense to others. And to you, in 6 months time.
- Others need to know the step or phase, what they’re looking at, and what kind of thing it is:
  “Iteration N. - Stage - thing”,  eg:
  “1 - User flow - sharpies sketch from Warsaw workshop”
  “4 - List and details - wires”
  “Option B1 - Payment flow - visuals”
- Add the status also to the title of the sections:
  “[STATUS NAME] Iteration N - name-of-the-feature”
	e.g. : “[EXPLORATION] Iteration III - Model detail views + add controller”
- Always upload new screens into new sections, let’s not replace screens (except for quick fixes and typos).

## Links to specs/docs/epics

Do put links to specs, docs or issues/epics in the description field, so people can find their way back to the spec, and to the associated cards.


### Who is it for?

What feedback do you want? UX input, visual input, front-end input, engineering input etc.
When uploading, think about the status of the project, what would you like feedback on may affect who you want to share it with.


## Inviting people to projects
Consider you can invite people at different times. You want to focus more on getting feedback on functionality, user experience, visual? It doesn’t mean to invite these disciplines only, but to be clear on the status/phase of the project.
Remember you can always use webteam@lists.canonical.com and design@lists.canonical.com to share and ask for feedback.


## When do we comment?

### Directions

If there are comments which are more fundamental about the feature, we should ping each other as opposed to leaving comments as this would lead to more confusion.

### Does it need a comment?

Wonder whether it needs to be a comment at all, or if the matter requires a quick chat or a deeper understanding cross-discipline.


## Resolving comments

We should not resolve comments, let’s keep track of comments
When a comment is addressed and completed we can then add ‘done’ to keep record of when things are closed, instead of resolving the comment.
Uploading new screens on different sessions will let comments stay where they originally were added.
