# React coding standards

This document outlines our standards for writing React applications.

## Starter Project

[canonical-webteam/react-starter](https://github.com/canonical-webteam/react-starter) provides a codified
example of our standards for react projects (Prettier, AirBnB style).

As much as possible, this project should reflect our standards for React applications. Please make pull requests
to this project if you feel something should change.

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
