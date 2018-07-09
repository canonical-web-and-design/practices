# JS code standards
This document outlines the rules for writing Javascript documents and fragments across all of our codebases.

## Style
Js should be written using [AirBnB](https://github.com/airbnb/javascript) style. New projects can adhere to this by selecting 'AirBnB' during `eslint init`, and existing projects can find the relevant eslint config in [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb).

## Progressive Enhancement
JavaScript should progressively enhance a page.

On all publicly accessible websites, core content and functionality should still be available without JavaScript. JavaScript applications written for a more specific audience which won't be indexed by search engines may be more lax, but should still treat progressive enhancement as a guiding principle.

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
- [http://eloquentjavascript.net/](http://eloquentjavascript.net/)
