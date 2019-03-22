---
title: JS code standards
description: Code style standards for JavaScript
redirect_from:
  - "/coding/react"
  - "/coding/code-formatting"
---

This document outlines the rules for writing JavaScript across our codebase.

## Progressive Enhancement

JavaScript should progressively enhance a page.

On all publicly accessible websites, core content and functionality should still be available without JavaScript. JavaScript applications written for a more specific audience which won't be indexed by search engines may be more lax, but should still treat progressive enhancement as a guiding principle.

## Performance

- Cache DOM queries — only select an element once.
- Use event delegation as much as possible to reduce the number of events bound to the page
- Understand when you cause an element repaint and reduce inline style manipulations accordingly.
- If possible, always use CSS for element transforms and transitions.

## Element hooks

We should target page element in JavaScript using the `data-js` element attribute instead of using the `class` attribute. Classnames should be used for styling only.

e.g. `<a data-js="index-link" href="/index">Index</a>`.

## Tooling

### Build tools
[Webpack](https://webpack.js.org/) is the preferred build tool for applications, and [Rollup](https://rollupjs.org/guide/en) has generally been preferred for building
cross environment libraries (both the browser and ES modules environments) if the library in question uses ES6 modules. Rollup and Webpack for the most part have
feature parity now however (Webpack now has support for scope hoisting, and Rollup now supports code splitting), so this is mostly now a matter of taste and
convenience, given Rollup is easier to configure for library builds.

### Dependency management

We use [Yarn](https://yarnpkg.com/en) for dependency management.

### Testing

We use the [Jest](https://jestjs.io) unit test framework.

### Code style & formatting

To ensure code formatting consistency across our codebase, we use [Prettier](https://github.com/prettier/prettier).

JavaScript should also be written using [AirBnB](https://github.com/airbnb/javascript) style. New projects can adhere to this by selecting 'AirBnB' during `eslint init`, and existing projects can find the relevant ESLint config in [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb).

## React

### Starting a new project

When starting a new React application, we recommend [create-react-app](https://github.com/facebook/create-react-app) for bootstrapping the project. Avoid [ejecting](https://facebook.github.io/create-react-app/docs/available-scripts#npm-run-eject) as long as feasible to make updating dependencies easier.

### Preferred libraries

All projects should generally use the following:

- Style framework - [Vanilla](https://github.com/vanilla-framework/vanilla-framework)
- Component testing - [Enzyme](https://github.com/airbnb/enzyme)

If you require routing, or state management:

- Routing - [react-router](https://github.com/ReactTraining/react-router)
- Application state management - [Redux](https://redux.js.org)

#### Redux specific

- Selector composition and memoisation - [Reselect](https://github.com/reduxjs/reselect)
- Async/side-effects management (http, localstorage etc.) - [redux-saga](https://github.com/redux-saga/redux-saga)

If you'd like introduce a new library, or feel we should replace one of the above, please make a PR to start a discussion.

### Reference projects

[CRBS-UI](https://git.launchpad.net/~crbs/crbs/+git/crbs-ui/tree/), while under active development, probably best reflects our standards for React projects currently.

[build.snapcraft.io](https://github.com/canonical-websites/build.snapcraft.io) - a bit dated, but first fully React-centred project in the webteam. Our first use of React, server-side rendering, Redux, Enzyme, etc. While it doesn't fully follow our current standards, it may be a good place to check how some of these libraries were used.

[canonical-webteam/react-starter](https://github.com/canonical-webteam/react-starter) was created to provide a codified example of our standards for React projects (Prettier, AirBnB style). While potentially still a useful reference, it should mostly be considered deprecated as it may not accurately reflect some of the choices we've made in real-world projects.

### File naming conventions

- Component files should use CamelCase and match the name of the default export (e.g. `MyComponent.js`).
- Files containing JSX should still have a `.js` extension.
  (See [justification](https://github.com/facebook/create-react-app/issues/87#issuecomment-234627904) from Dan Abramov).

### Redux

#### General Principals

- Use Redux for state that is shared across multiple routes, or in deep component hierarchies where you find yourself passing `props` through multiple children. Favour local state otherwise. See [Do I have to put all my state in redux?](https://redux.js.org/faq/organizingstate#do-i-have-to-put-all-my-state-into-redux-should-i-ever-use-reacts-setstate)
- It is fine, and in fact more efficient, to connect components lower in the hierarchy (i.e. don't feel you can only connect a top level component). See [Should I only connect my top component, or can I connect multiple components in my tree?](https://redux.js.org/faq/reactredux#should-i-only-connect-my-top-component-or-can-i-connect-multiple-components-in-my-tree)

#### Reducers

- Ensure you use [immutable patterns](https://redux.js.org/recipes/structuringreducers/immutableupdatepatterns) for updating the Redux store.
  Using the object spread operator is recommended, but requires a [Babel polyfill](https://babeljs.io/docs/en/babel-plugin-transform-object-rest-spread.html). You might find [Dave Ceddia's Immutability in React and Redux: The Complete Guide](https://daveceddia.com/react-redux-immutability-guide/) helpful.
- [reduceReducers](https://github.com/redux-utilities/reduce-reducers) is a useful tool for combining reducers and removing boilerplate where you have many reducers with identical behaviour.

#### Selectors

- Use selectors to access state in your components, ideally with [Reselect](https://github.com/reduxjs/reselect) which provides memoisation. Selectors can be elegantly combined to create different views of state.

#### Testing

- Generally, it is best to test the component in its connected state, using [redux-mock-store](https://github.com/dmitry-zaets/redux-mock-store). In cases where you want to test the unconnected functionality of a connected component, it is okay to create a named export with a "Component" suffix. e.g. If your default export is `export default connect(mapStateToProps, mapDispatchToProps)(UserList)` you can also export `export { UserList as UserListComponent }` for testing.

## References

- [http://jstherightway.org/](http://jstherightway.org/)
- [http://eloquentjavascript.net/](http://eloquentjavascript.net/)
