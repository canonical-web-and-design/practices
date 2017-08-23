# JS code standards
This document outlines the rules for writing Javascript documents and fragments across all of our codebases.

## General rules
- Javascript should progressively enhance a page. Core content and functionality should still be available without Javascript.
- Variable names should be camelCase
- Avoid abbreviated or deliberately short names (choose `query` over `q`).
- Your code should be sufficiently eloquent that it doesn't need comments to describe its purpose, however, if comments are required, they should be inline.
- Javascript code should be indented by two spaces.

## Element hooks
We should target page element in Javascript using the `data-js` element attribute instead of using the class attribute. Classnames should be used for styling only.

e.g. `<a data-js="index-link" href="/index">Index</a>`

## Performance
  - Cache DOM queries—only select an element once.
  - Use event delegation as much as possible to reduce the number of events bound to the page
  - Understand when you cause an element repaint and reduce inline style manipulations accordingly. If possible, always use CSS for element transforms and transitions.
