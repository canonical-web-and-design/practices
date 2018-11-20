---
layout: base
---

# React coding standards

This document outlines our standards for writing React applications.

## Starting a new Project
We recommend [create-react-app](https://github.com/facebook/create-react-app) for bootstrapping a new project, and avoid ejecting as long as feasible.

### Preferred libraries
* routing - [react-router](https://github.com/ReactTraining/react-router)
* app state management - [redux](https://redux.js.org)
* component testing - [enzyme](https://github.com/airbnb/enzyme)
* code formatting - [prettier](https://prettier.io) - We realise that not everyone will agree on the choices that Prettier makes, however feel consistency is ultimately more valuable. As has been said in the golang community, "gofmt's style is no one's favorite, yet gofmt is everyone's favorite".
* linting - [eslint & airbnb](https://www.npmjs.com/package/eslint-config-airbnb)

If you'd like introduce a new library, or feel we should replace one of the above, please make a PR to start a discussion.

### Reference projects
[CRBS-UI](https://git.launchpad.net/~crbs/crbs/+git/crbs-ui/tree/), while under active development, probably best reflects our standards for react projects currently.

[canonical-webteam/react-starter](https://github.com/canonical-webteam/react-starter) was created to provide a codified
example of our standards for react projects (Prettier, AirBnB style), and while potentially still a useful reference, may not accurately reflect some of the choices we've made in real-world projects.

## File Naming Conventions

* Component files should use CamelCase and match the name of the default export (e.g. MyComponent.js).
* Files containing jsx should still have a `.js` extension. 
(See [justification](https://github.com/facebook/create-react-app/issues/87#issuecomment-234627904) from Dan Abramov).

## Redux

### General Principals
* Use redux for state that is shared across multiple routes, or in deep component hierachies where you find yourself passing props through multiple children. Favour local state otherwise. See [Do I have to put all my state in redux?](https://redux.js.org/faq/organizingstate#do-i-have-to-put-all-my-state-into-redux-should-i-ever-use-reacts-setstate)
* It is fine, and in fact more efficient, to connect components lower in the hierarchy (i.e. don't feel you can only connect a top level component). See [Should I only connect my top component, or can I connect multiple components in my tree?](https://redux.js.org/faq/reactredux#should-i-only-connect-my-top-component-or-can-i-connect-multiple-components-in-my-tree)

### Reducers
* Ensure you use [immutable patterns](https://redux.js.org/recipes/structuringreducers/immutableupdatepatterns) for updating the redux store. Using
the object spread operator is recommended, but requires a [babel polyfill](https://babeljs.io/docs/en/babel-plugin-transform-object-rest-spread.html). You might find [Dave Ceddia's Immutability in React and Redux: The Complete Guide](https://daveceddia.com/react-redux-immutability-guide/) helpful.
* [reduceReducers](https://github.com/redux-utilities/reduce-reducers) is a useful tool for combining reducers and removing boilerplate where you have many reducers with identical behaviour.

### Selectors
* Use selectors to access state in your components, ideally with [reselect](https://github.com/reduxjs/reselect) which provides memoisation. Selectors can be elegantly combined to create different views of state. 

### Testing
* In cases where you want to test the unconnected functionality of a connected component, it is okay to create a named export with a "Component" suffix. e.g. If your default export is: 
    ```export default connect(mapStateToProps, mapDispatchToProps)(UserList)```
    you can also export
    ```export { UserList as UserListComponent }``` for testing.
