# JS code standards
This document outlines the rules for writing Javascript documents and fragments across all of our codebases.

## General rules
 - Javascript should progressively enhance a page where possible and core content and functionality should still be available without Javascript. The exception to this, is in the case of non-isomorphic SPAs where this is not technically feasible.
- Variable names should be camelCase
- Avoid abbreviated or deliberately short names (choose `query` over `q`).
- If comments are required, they should be inline and above the Javascript they relate to.
- Javascript code should be indented by two spaces.

## Element hooks
We should target page element in Javascript using the `data-js` element attribute instead of using the class attribute. Classnames should be used for styling only.

e.g. `<a data-js="index-link" href="/index">Index</a>`

## Performance
  - Cache DOM queries — only select an element once.
  - Use event delegation as much as possible to reduce the number of events bound to the page
  - Understand when you cause an element repaint and reduce inline style manipulations accordingly.
  - If possible, always use CSS for element transforms and transitions.

### References
- [http://jstherightway.org/](http://jstherightway.org/)
- [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
- [http://eloquentjavascript.net/](http://eloquentjavascript.net/)
