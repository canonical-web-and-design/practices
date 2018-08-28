# React coding standards

This document outlines our standards for writing React components.

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

* Ensure you use [immutable patterns](https://redux.js.org/recipes/structuringreducers/immutableupdatepatterns) for updating the redux store. Using
the object spread operator is recommended, but requires a [babel polyfill](https://babeljs.io/docs/en/babel-plugin-transform-object-rest-spread.html).
