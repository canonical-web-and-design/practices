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

[Webpack](https://webpack.js.org/) is the preferred build tool for applications, and [Rollup](https://rollupjs.org/guide/en) is preferred for libraries.

Rollup and Webpack for the most part have feature parity, so this is mostly a matter of taste and convenience, given Rollup is easier to configure for library builds.

### Dependency management

We use [Yarn](https://yarnpkg.com/en) for dependency management.

### Packaging

#### Use the npm files array

Use the package.json `files` array to whitelist files for inclusion in your package. This is the safest approach, as it is explicit; using `.npmignore` is potentially dangerous, as you may end up packaging files unintentionally (credentials in a .env file being the worst case scenario!).

See [Publishing what you mean to publish](https://blog.npmjs.org/post/165769683050/publishing-what-you-mean-to-publish) for further details.

### Testing

We use the [Jest](https://jestjs.io) unit test framework.

#### General Testing Advice

- Don't test external code/libraries.

#### Testing React

- Tests should be collocated with their component in the same directory (MyComponent.js should have a corresponding MyComponent.test.js)
- If a component seems difficult to test, it might indicate that it needs to be further decomposed into smaller components.
- Unittests should test component behaviour, rather than explicit rendering. Typically you want to test state changes,
  that handlers are called with appropriate arguments, and any internal logic.
- [Jest snapshots](https://jestjs.io/docs/en/snapshot-testing) are ideal for catching regressions in component output/rendering. If you are reviewing a branch, do take care to inspect the snapshot diffs. Snapshot tests should compliment unit tests rather than replace them, as unit tests better describe the intended behaviour and output of a component.
- Favour testing components in isolation where possible (use enzyme's `shallow` over `mount` where possible).

##### Redux

- Connected components (redux containers) should be tested using [redux-mock-store](https://github.com/dmitry-zaets/redux-mock-store).
- Containers that dispatch actions should test that component behaviours dispatch the expected actions.
- [redux-saga-test-plan](https://github.com/jfairbank/redux-saga-test-plan) is a helpful tool if you're using sagas.
- Reducers, action creators and selectors should all have simple functional tests.
- Test composed Reselect selectors in isolation with [resultFunc](https://github.com/reduxjs/reselect#q-how-do-i-test-a-selector).

### Code style & formatting

To ensure code formatting consistency across our codebase, we use [Prettier](https://github.com/prettier/prettier).

JavaScript should also be written using [AirBnB](https://github.com/airbnb/javascript) style. New projects can adhere to this by selecting 'AirBnB' during `eslint init`, and existing projects can find the relevant ESLint config in [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb).

### Commenting code

As a general rule, human-readable code is preferred over brevity.

Inline comments should be provided where logic or behaviour is unexpected or required due to external factors.

If library code, [JSDoc](http://usejsdoc.org/) comments should be provided as appropriate.

## React

### Starting a new project

When starting a new React application, we recommend [create-react-app](https://github.com/facebook/create-react-app) for bootstrapping the project. Avoid [ejecting](https://facebook.github.io/create-react-app/docs/available-scripts#npm-run-eject) as long as feasible to make updating dependencies easier.

We recommend new projects use the [hooks API](https://reactjs.org/docs/hooks-intro.html) rather than class based components. Hooks generally make components simpler, allow reuse of stateful non-visual code, and [perform better](https://reactjs.org/docs/hooks-faq.html#are-hooks-slow-because-of-creating-functions-in-render).

### Preferred libraries

All projects should generally use the following:

- Style framework - [Vanilla](https://github.com/vanilla-framework/vanilla-framework)
- Component testing - [Enzyme](https://github.com/airbnb/enzyme)

If you require routing, or state management:

- Routing - [react-router](https://github.com/ReactTraining/react-router)
- Application state management - [Redux](https://redux.js.org)

### Hooks

For hooks based projects, we recommend the following:

- Hooks based components should still follow the class based component's lifecycle ordering:
  1. computation/logic functions (typically best _outside_ the component)
  2. state (`useState`)
  3. side-effects (`useEffect`)
  4. event handlers
  5. render
- Use the [redux hooks API](https://react-redux.js.org/next/api/hooks) and consider `connect` deprecated.
- Use [ES6 default parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters) instead of `defaultProps`.
- For expensive functions passed down to child components, consider using the [`useCallback` hook](https://reactjs.org/docs/hooks-reference.html#usecallback).
- Hooks introduce some coupling which means you'll need to `mount` redux connected components when writing enzyme tests (previously you could export the unconnected component).

#### Redux specific

- Selector composition and memoisation - [Reselect](https://github.com/reduxjs/reselect)
- Immutable state management - [Immer](https://github.com/immerjs/immer)
- Async/side-effects management (http, localstorage etc.) - [redux-saga](https://github.com/redux-saga/redux-saga)

If you'd like introduce a new library, or feel we should replace one of the above, please make a PR to start a discussion.

### Reference projects

[jaas-dashboard](https://github.com/canonical-web-and-design/jaas-dashboard) - project uses the hooks API and reflects current standards.

[maas-ui](https://github.com/canonical-web-and-design/maas-ui) - project uses the hooks API and reflects current standards.

[crbs-ui](https://github.com/canonical-web-and-design/crbs-ui) (aka RBAC) - generally reflects current standards, but class based.

[build.snapcraft.io](https://github.com/canonical-websites/build.snapcraft.io) - a bit dated, but first fully React-centred project in the webteam. Our first use of React, server-side rendering, Redux, Enzyme, etc. While it doesn't fully follow our current standards, it may be a good place to check how some of these libraries were used.

### File naming conventions

- Component files should use CamelCase and match the name of the default export (e.g. `MyComponent.js`).
- Files containing JSX should still have a `.js` extension.
  (See [justification](https://github.com/facebook/create-react-app/issues/87#issuecomment-234627904) from Dan Abramov).

### Redux

#### General Principals

- Use Redux for state that is shared across multiple routes, or in deep component hierarchies where you find yourself passing `props` through multiple children. Favour local state otherwise. See [Do I have to put all my state in redux?](https://redux.js.org/faq/organizingstate#do-i-have-to-put-all-my-state-into-redux-should-i-ever-use-reacts-setstate)
- It is fine, and in fact more efficient, to connect components lower in the hierarchy (i.e. don't feel you can only connect a top level component). See [Should I only connect my top component, or can I connect multiple components in my tree?](https://redux.js.org/faq/reactredux#should-i-only-connect-my-top-component-or-can-i-connect-multiple-components-in-my-tree)
- For consistency, try to build action creators using [flux standard actions](https://github.com/redux-utilities/flux-standard-action#actions).

#### Reducers

- Use [immer](https://github.com/immerjs/immer) for easy immutable state management, removing a whole class of bugs. To understand why this is important, please read [Immutability in React and Redux: The Complete Guide](https://daveceddia.com/react-redux-immutability-guide/).
- [reduceReducers](https://github.com/redux-utilities/reduce-reducers) is a useful tool for combining reducers and removing boilerplate where you have many reducers with identical behaviour.

#### Selectors

- Use selectors to access state in your components, ideally with [Reselect](https://github.com/reduxjs/reselect) which provides memoisation. Selectors can be elegantly combined to create different views of state.

#### Testing

- Generally, it is best to test the component in its connected state, using [redux-mock-store](https://github.com/dmitry-zaets/redux-mock-store). In cases where you want to test the unconnected functionality of a connected component, it is okay to create a named export with a "Component" suffix. e.g. If your default export is `export default connect(mapStateToProps, mapDispatchToProps)(UserList)` you can also export `export { UserList as UserListComponent }` for testing.

## References

- [http://jstherightway.org/](http://jstherightway.org/)
- [http://eloquentjavascript.net/](http://eloquentjavascript.net/)
