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

We should target page element in Javascript using the `data-js` element attribute instead of using the class attribute. Classnames should be used for styling only.

e.g. `<a data-js="index-link" href="/index">Index</a>`.

## Tooling

### Dependency management

We use [yarn](https://yarnpkg.com/en) for dependency management.

### Testing

We use the [jest](https://jestjs.io) unittest framework.

#### General Testing Principals
  * Avoid setting up state in `beforeEach`. It should be clear from reading a test in isolation what state it is in.
  * Use test factories to reduce boilerplate for commonly instantiated objects.
  * Don't test external code/libraries.

#### Testing React
  * Tests should be collocated with their component in the same directory (MyComponent.js should have a corresponding MyComponent.test.js)
  * If a component seems difficult to test, it might indicate that it needs to be further decomposed into smaller components.
  * Unittests should test component behaviour, rather than explicit rendering. Typically you want to test state changes,
    that handlers are called with appropriate arguments, and any internal logic.
  * [Jest snapshots](https://jestjs.io/docs/en/snapshot-testing) are ideal for catching regressions in component output/rendering. If you are reviewing a branch, do take care to inspect the snapshot diffs. Snapshot tests should compliment unit tests rather than replace them, as unit tests better describe the intended behaviour and output of a component.
  * Favour testing components in isolation where possible (use enzyme's `shallow` over `mount` where possible).

##### Redux
  * Connected components (redux containers) should be tested using [redux-mock-store](https://github.com/dmitry-zaets/redux-mock-store).
  * Containers that dispatch actions should test that component behaviours dispatch the expected actions.
  * [redux-saga-test-plan](https://github.com/jfairbank/redux-saga-test-plan) is a helpful tool if you're using sagas.
  * Reducers, action creators and selectors should all have simple functional tests. 
  * Test composed Reselect selectors in isolation with [resultFunc](https://github.com/reduxjs/reselect#q-how-do-i-test-a-selector).

### Code style & formatting

To ensure code formatting consistency across our codebase, we use [Prettier](https://github.com/prettier/prettier).

JS should also be written using [AirBnB](https://github.com/airbnb/javascript) style. New projects can adhere to this by selecting 'AirBnB' during `eslint init`, and existing projects can find the relevant eslint config in [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb).

## React

### Starting a new project

When starting a new react application, we recommend [create-react-app](https://github.com/facebook/create-react-app) for bootstrapping the project. Avoid [ejecting](https://facebook.github.io/create-react-app/docs/available-scripts#npm-run-eject) as long as feasible to make updating dependencies easier.

### Preferred libraries

All projects should generally use the following:

* style framework - [vanilla](https://github.com/vanilla-framework/vanilla-framework)
* component testing - [enzyme](https://github.com/airbnb/enzyme)

If you require routing, or state management:

* routing - [react-router](https://github.com/ReactTraining/react-router)
* app state management - [redux](https://redux.js.org)

#### Redux specific

* selector composition and memoisation - [reselect](https://github.com/reduxjs/reselect)
* async/side-effects management (http, localstorage etc.) - [redux-saga](https://github.com/redux-saga/redux-saga)

If you'd like introduce a new library, or feel we should replace one of the above, please make a PR to start a discussion.

### Reference projects

[CRBS-UI](https://git.launchpad.net/~crbs/crbs/+git/crbs-ui/tree/), while under active development, probably best reflects our standards for react projects currently.

[build.snapcraft.io](https://github.com/canonical-websites/build.snapcraft.io) - a bit dated, but first fully React centred project in the webteam. Our first use of React, server-side rendering, Redux, Enzyme, etc. While it doesn't fully follow our current standards it may be a good place to check how some of these libraries were used.

[canonical-webteam/react-starter](https://github.com/canonical-webteam/react-starter) was created to provide a codified example of our standards for react projects (Prettier, AirBnB style). While potentially still a useful reference, it should mostly be considered deprecated as it may not accurately reflect some of the choices we've made in real-world projects.

### File naming conventions

* Component files should use CamelCase and match the name of the default export (e.g. MyComponent.js).
* Files containing jsx should still have a `.js` extension.
(See [justification](https://github.com/facebook/create-react-app/issues/87#issuecomment-234627904) from Dan Abramov).

### Redux

#### General Principals

* Use redux for state that is shared across multiple routes, or in deep component hierarchies where you find yourself passing props through multiple children. Favour local state otherwise. See [Do I have to put all my state in redux?](https://redux.js.org/faq/organizingstate#do-i-have-to-put-all-my-state-into-redux-should-i-ever-use-reacts-setstate)
* It is fine, and in fact more efficient, to connect components lower in the hierarchy (i.e. don't feel you can only connect a top level component). See [Should I only connect my top component, or can I connect multiple components in my tree?](https://redux.js.org/faq/reactredux#should-i-only-connect-my-top-component-or-can-i-connect-multiple-components-in-my-tree)

#### Reducers

* Ensure you use [immutable patterns](https://redux.js.org/recipes/structuringreducers/immutableupdatepatterns) for updating the redux store. Using
the object spread operator is recommended, but requires a [babel polyfill](https://babeljs.io/docs/en/babel-plugin-transform-object-rest-spread.html). You might find [Dave Ceddia's Immutability in React and Redux: The Complete Guide](https://daveceddia.com/react-redux-immutability-guide/) helpful.
* Reducers must be [pure functions](https://redux.js.org/basics/reducers#handling-actions) i.e. they should not mutate their arguments, call impure functions or create side-effects such as API calls.
* [reduceReducers](https://github.com/redux-utilities/reduce-reducers) is a useful tool for combining reducers and removing boilerplate where you have many reducers with identical behaviour.

#### Selectors

* Use selectors to access state in your components, ideally with [reselect](https://github.com/reduxjs/reselect) which provides memoisation. Selectors can be elegantly combined to create different views of state.

#### Testing

* Generally it is best to test the component in its connected state, using [redux-mock-store](https://github.com/dmitry-zaets/redux-mock-store). In cases where you want to test the unconnected functionality of a connected component, it is okay to create a named export with a "Component" suffix. e.g. If your default export is:
    ```export default connect(mapStateToProps, mapDispatchToProps)(UserList)```
    you can also export
    ```export { UserList as UserListComponent }``` for testing.

## References

- [http://jstherightway.org/](http://jstherightway.org/)
- [http://eloquentjavascript.net/](http://eloquentjavascript.net/)
