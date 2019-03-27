---
title: Project philosophy
description: The guiding principles behind our code projects
---

We aim to always encourage participation in our projects from both within the company and the general public. We aim to support and grow the communities that surround our work. We do this by creating web applications that are [simple](https://en.wikipedia.org/wiki/KISS_principle) for everyone to understand and use.

Our work should be [available to the public](https://en.wikipedia.org/wiki/Open_by_default), and as easy as possible for anyone to [contribute to](https://en.wikipedia.org/wiki/Open_collaboration) or learn from. This philosophy should permeate everything we do, from the software we choose to how we write [READMEs](https://robots.thoughtbot.com/how-to-write-a-great-readme) and [our code](https://developer.gnome.org/programming-guidelines/stable/writing-good-code.html.en), to how we respond to pull requests and issues.

We encourage [consistency](https://uxdesign.cc/design-principle-consistency-6b0cf7e7339f) and [building on what's gone before](https://en.wikipedia.org/wiki/Code_reuse), and so following one of our standard structures is recommended in the absence of other concerns. However, we also encourage [exploration](https://en.wikipedia.org/wiki/Exploratory_programming) and remaining open-minded to better ways to solve problems. This means that there may well be cases where a completely new stack or language may be chosen.

## In practice

Our web applications are designed as small, [focused](https://en.wikipedia.org/wiki/Unix_philosophy#Do_One_Thing_and_Do_It_Well), self-contained projects with only loose coupling to our other applications. Code should be shared between projects by writing open-source packages for inclusion in the relevant projects, and applications should share data through public APIs.

We keep our code in public GitHub repositories if possible. Each project should be simple to understand and get running without needing deep technical context or wider context about our other projects. As far as possible, no special credentials should be necessary to get the code running.

We always intend to choose straightforward technology stacks that are no more complex than they need to be for the application in question, just as the application itself should be as simple as possible.
