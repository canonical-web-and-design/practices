---
title: UX/design proposals, sharing process & feedback convention
description: How to share UX & design proposals and guidelines on feedback convention
---

This document outlines the guidelines on our tools (e.g. Miro, Zeplin, GitHub) across the different disciplines and the different phases of a project.

## Table of content

- [Feedback convention (across tools)](#feedback-convention)
  - [Start your comment with](#start-your-comment-with:)
- [When do we comment?](#when-do-we-comment)
- [Resolving comments](#resolving-comments)
- [What tools do we use?](#what-tools-do-we-use)
  - [Miro](#miro)
  - [Docs and Specs](#docs-and-specs)
  - [Zeplin](#zeplin)
  - [General direction](#general-direction)
- [Zeplin/Miro status convention](#zeplin-miro-status-convention)
  - [Must haves](#must-haves)
  - [Status and tags](#status-and-tags)
  - [Status terminology](#status-terminology)
  - [Projects name](#projects-name)
  - [Sections name](#sections-name)
- [30:60:90 Method](#30:60:90-method)
  - [30% A rough idea](#30%-A-rough-idea)
  - [60% A first draft of a set concept](#60%-A-first-draft-of-a-set-concept)
  - [90% A last check before development](#90%-A-last-check-before-development)
- [Links to specs/docs/epics](#links-to-specs-docs-epics)
- [Who is it for?](#who-is-it-for)
- [Inviting people to projects](#inviting-people-to-projects)

## Feedback convention

Problems: time zones, semantic gap, hard to categorise the feedback, need a way to receive feedback that we can work with and understand the motivation behind the feedback.

When there are engineers working in different time zones, it can be cumbersome to get explanation and clarification the next day or in some cases when the new design is ready and we realise that what we understood was entirely wrong. This delay can cost the entire team in terms of productivity.

###Start your comment with:
**1. “+1” or “I like…”
(tag a green colour on the Zeplin comment)**
The purpose is to highlight what is agreed or what fits the requirements.

- For components that you like and that we should keep it.
- Good to go, agreed and signed off (in relation to the context the comment is on)

**2. “I wish… because” or “I think… because”
(tag a yellow colour on the Zeplin comment)**
The purpose is to get to the point and provide explanation/reasoning behind it.
For components that you think:

- Can be improved
- Propose an alternative behaviour
- Disagree with and would like to propose an alternative behaviour
- Would like to patternized
- Need clarification (express which part is confusing)
- Add context and explanation of the reason

Add “because…” if your comment needs elaborating or add context on what could be improved.
Examples:

- “I wish this component has x, because for z users, this can be confused with another component.”
- “I wish this is clearer, because when I’m going through this component, I’m thinking x….,y….,z….”
- “I think this interaction could be clearer”
- “I think this component should stand out more because the user may miss it”
- “I think this should use X component or pattern”
- “I think these icons should be aligned because they are aligned in other products”
- “I think you’ve used the wrong logo/colour/icon”

**3. “Info”
(tag a purple colour on the Zeplin comment)**
When you don’t want to express an opinion, but would like to share information, caveat, or references that I might have missed or overlooked in the prototype/wireframe.
Examples:

- “[INFO] we use a very similar component elsewhere, please have a look at this…”
- “[INFO] the API cannot return this information right now, we don’t have an endpoint, needs further discussions and planning in order to implement this”
- “[INFO] we have a pattern that fits this use case”

**4. “What if…” or “I wonder...”
(tag a blue colour on the Zeplin comment)**
The purpose is to propose an alternative solution (what would be good). Depending on the stage of the project this could be on a discovery, UX, visual or implementation level.
**The ideal comment would also add reasoning to the proposal**, or add “because…” if your comment needs elaborating or add context on what could be improved.
Examples:

- “What if we add x colour to this component? I think it will be easier to capture our users’ attention.”
- “What if we optimise this with a ‘clear all’ function? This way users could start from scratch”
- “I wonder if this is exploration includes the use cases we discussed, because I don’t see when users can do X”
- “I wonder if using a modal window here is the right approach because I remember the CLI allows users to act contextually at the same time”

### When do we comment?

**General: peer review metaphor**
Soliciting feedback from our peers (other designers) should be more about asking "what haven't I thought of", rather than "do you approve of my solution" - and more akin to a peer review than a critique.
As feedback-givers we should think twice before pressing "post" on an item of feedback and ask ourselves "does this comment further the goal of improving the end-user's experience?"
There should be a level of mutual respect and trust, sufficient that comments are left (and read) with the best possible intentions and aimed solely at improving the end-user experience.
As design professionals we should feel empowered to consider feedback and then incorporate or disregard it as we see fit. Of course, we shouldn't dismiss all feedback but we should aim to strike a balance.

**Directions**
If there are comments which are more fundamental about the feature, we should ping each other as opposed to leaving comments as this would lead to more confusion.

**Does it need a comment?**
Wonder whether it needs to be a comment at all, or if the matter requires a quick chat or a deeper understanding cross-discipline.
Add comments that use the feedback convention above to help the author understand your comments

### Resolving comments

We should not resolve comments, let’s keep track of comments whenever possible.
When a comment is addressed and completed we can then add ‘done’ to keep record of when things are closed, instead of resolving the comment.
Uploading new screens on different sessions will let comments stay where they originally were added: try to upload new screens into new sections when the changes are enough to justify a new iteration of the work. Let’s not replace screens (except for quick fixes and typos) when working on a new version of the iteration.

## What tools do we use?

### Miro

Miro is very valuable especially during the discovery and definition phase. You might want to consider starting in Miro during the definition and the initial stage of the project with core engineers instead of Zeplin.

### Doc and Specs

Spec docs with core engineers are also very important for the definition of the feature and to start a conversation around API, user stories and functionality.

### Zeplin

When ready for wireframes it can then move to Zeplin. Use tags and naming convention in a way that reflects the status of the project.

### General direction

We should work more on documents/specs and/or Miro to discuss things first, back and forth with engineers to discuss sketches about scope before moving to Zeplin for further feedback.

## Zeplin/Miro status convention

### Must haves

- Project name in the project title
- Stage of work, e.g. “Sketch”, “Wireframe” or “Design”
- Feature, section, page (etc) name
- Iteration number
- Direction on the type of feedback you’re looking for, and who from
  - This could be text on your Sketch artboard or comments on the board
  - “Please comment on this component”
  - “I’m not sure about this design treatment”

### Status and tags

The phase and status of a project, along with tags can help team members know what type of feedback is required.
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
- Wireframes (iteration 1, 2 etc)
- Final UX proposal (last wireframe to conclude UX)

**Visual**

- Visual design (iteration 1, 2 etc)
- Final visual design
- Feedback on the visual

**Development**

- This is ready to be implemented
- Highlight implementation specs, annotation

**Optional tags**

- Can be added for review stages
- Reflecting the tag-naming convention from GitHub when asking for a certain type of feedback:
  - Review: UX needed
  - Review: design needed
  - Review: QA needed

## Projects name

Name your projects this way, using the year and the month of the cycle the project refers to: “YY.MM Product - Project”, e.g. : “20.04 Snap - Progressive release”.

## Sections name

- Name your sections and your artboards so they make sense to others. And to you, in 6 months time.
- Others need to know the step or phase, what they’re looking at, and what kind of thing it is: “Iteration N. - Stage - thing”, eg:
  “1 - User flow - sharpies sketch from Warsaw workshop”
  “4 - List and details - wires”
  “Option B1 - Payment flow - visuals”
- Add the status also to the title of the sections:
  “[STATUS NAME] Iteration N - name-of-the-feature”
  e.g. : “[EXPLORATION] Iteration III - Model detail views + add controller”
- Try to upload new screens into new sections when the changes are enough to justify a new iteration of the work, let’s not replace screens (except for quick fixes and typos) when working on a new version of the iteration.

## 30:60:90 Method

The 30:60:90 method is a way to set expectations for your design/feedback. A designer may include this number on their section names to define which stage this design is in.

### 30% A rough idea

At 30% is a rough concept that may or may not be a viable solution to solve a user / business problem. At 30% the designer has not put much time, effort and thought into the concept. It is easy to pivot or throw this away. At this stage I’m looking for:
Ideas, tips or impressions on the idea

- Whether or not this is something we should do
- If this is the right direction
- How to move the concept forward
- Go / no go of this idea

### 60% A first draft of a set concept

At 60% we have a first draft of the concept. We’ve spent a lot of time and effort to get to this point, so we don’t want to be changing direction drastically unless there is a very good reason to do so (which we should have figured out at the 30% stage). At this stage I’m looking for:

- Whether the 30% critique was addressed adequately
- Visual / graphic feedback
- Feedback on interactive components
- Ways to expand the concept

### 90% A last check before development

At 90% we are about to hand over to development. By now, we should have tested the design with real users and made updates to address any usability issues found. There should be no drastic changes at this point. This is a final check where we want to be focusing on the minutiae:

- Was 60% critique addressed
- Nitty gritty grammar
- Finalizing copy

## Links to specs/docs/epics

Do put links to specs, docs or issues/epics in the description field, so people can find their way back to the spec, and to the associated cards.

## Who is it for?

What feedback do you want? UX input, visual input, front-end input, engineering input etc.
When uploading, think about the status of the project, what would you like feedback on may affect who you want to share it with it.

## Inviting people to projects

Consider you can invite people at different times. You want to focus more on getting feedback on functionality, user experience, visual? It doesn’t mean to invite these disciplines only, but to be clear on the status/phase of the project.
Remember you can always use webteam@lists.canonical.com and design@lists.canonical.com to share and ask for feedback.
