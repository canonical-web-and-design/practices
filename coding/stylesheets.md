---
title: BEM coding standard
description: Code style standards for CSS and Sass
---

For a quick recap on BEM, it works by breaking down all classes in a
codebase into one of three groups:

-   Block: The sole root of the component.

-   Element: A component part of the Block.

-   Modifier: A variant or extension of the Block.

The point of BEM is to give a lot more transparency and clarity to your
markup. BEM informs developers how classes relate to each other, which
is particularly useful in complex or deep pieces of DOM.

There are a number of common problems when working with CSS at scale,
but the major two that this document aims to solve are clarity and
confidence:

> **Clarity**: How much information can we glean from the smallest
> possible source? Is our code self-documenting? Can we make safe
> assumptions from a single context? How much do we have to rely on
> external or supplementary information in order to learn about a
> system?

> **Confidence**: Do we have enough knowledge about a system to be
> able to safely interface with it? Do we know enough about our code
> to be able to confidently make changes? Do we have a way of
> knowing the potential side effects of making a change? Do we have
> a way of knowing what we might be able to remove?

Naming convention
-----------------

#### Format

`.block__element--modifier`

#### Example

`.user__name--long`

Always encapsulate a component in a component name and all elements of
the component is prefixed with the component name. For example:

```
<div class="user">
    <img class="user__image" src="/jeff.jpg" />
    <p class="user__name">Jeff</p>
</div>
```

New code should be written using the full class names, to enable findability and to lower the cognitive load of navigating a medium to large partial. For example:

```
.user {
    …
}

.user__image {
    …
}

.user__image--small {
    …
}

```


Targeting elements
------------------

As a developer you should only target elements in the core part of your
css styles. Such as the reset and typography. This results in all
elements that have component styling need a class attached.

Utility class
-------------

#### Format

`.u-utility-name`

#### Example

`.u-no-border`

Utility classes are styling patterns that are used across the entire
site and can be applied to modify components. We should strive to keep
this to a minimum as they lead to a lot of single style overrides.

Semantic naming
---------------

### Components

Naming components can be difficult as the name should be based on the
reasoning for the styling and not on the style being applied. Styling
can change which makes the name incorrect and confusing. Component names
can contain more than one word which are separated by a single hyphen:

`.component-name`

### Elements

When naming an element use a word or words that best describe the
content of the element. Again these can contain more than one word
separated by a single hyphen:

```
<ul class="list">
    <li class="list__item"></li>
</ul>
```

### Modifier

Modifiers should describe the reason to have overriding styling. Again
these can contain more than one word separated by a single hyphen:

#### Do not:

`<div class="row--grey"></div>`

#### Do:

`<div class="row--billboard"></div>`

Nesting elements
----------------

You may find you start to nest elements inside a component. This should
be done with semantically named elements. You should only have one
element name for each DOM element. For example:

#### Do not:

`<li class="nav__list__item"></div>`

#### Do:

`<li class="nav__list-item"></li>`

If you find you are having trouble naming an element due to over
nesting. Consider splitting that component into smaller components that
when combined become result in the desired organism.

Example of a component with nested elements:

```
<nav class="nav">

    <ul class="nav__list">

        <li class="nav__list-item">
            <a href="#" class="nav__link">Link</a>
        <li>

        <li class="nav__list-item">
            <a href="#" class="nav__link--promo">Promo</a>
        </li>

    </ul>

</nav>
```

State classes
-------------

is-, has-: Signify that the piece of UI in question is currently styled
a certain way because of a state or condition. It tells us that the DOM
currently has a temporary, optional, or short-lived style applied to it
due to a certain state being invoked.

#### Format

`.[is|has]-state {}`

#### Example

`.is-active`

`.has-dropdown`

This allows interactive scripts to simple toggle these classes with
confidence only state styles will be effect. Leaving component styles
unaffected.

JavaScript namespacing
----------------------

A piece of the DOM has some behaviour acting upon it, and that
JavaScript binds onto it to provide that behaviour. If you’re not a
developer working with JavaScript, leave these well alone.

#### Format

`.js-functionality`

#### Example

`.js-open`

The idea is that -- in order to properly separate our concerns, we
should never have styling and behaviour bound to the same classes.


Code Formatting
===============
To ensure consistency across our codebase, we use [Prettier](https://github.com/prettier/prettier) for formatting sass.
