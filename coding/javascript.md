---
title: JS code standards
description: Code style standards for JavaScript
redirect_from:
  - "/coding/react"
  - "/coding/code-formatting"
---

This document outlines the rules for writing JavaScript across our codebase.

## General Principles

### Progressive Enhancement

JavaScript should progressively enhance a page.

On all publicly accessible websites, core content and functionality should still be available without JavaScript. JavaScript applications written for a more specific audience which won't be indexed by search engines may be more lax, but should still treat progressive enhancement as a guiding principle.

### Performance

- Cache DOM queries — only select an element once.
- Use event delegation as much as possible to reduce the number of events bound to the page
- Understand when you cause an element repaint and reduce inline style manipulations accordingly.
- If possible, always use CSS for element transforms and transitions.

### Element hooks

We should target page element in JavaScript using the `data-js` element attribute instead of using the `class` attribute. Classnames should be used for styling only.

e.g. `<a data-js="index-link" href="/index">Index</a>`.

## TypeScript

### TypeScript vs JavaScript

For any medium-large JavaScript applications, consider using TypeScript in preference to JavaScript, as it offers a better developer experience, and increased safety. See [Transitioning to TypeScript](https://docs.google.com/document/d/1yXNI_biuKwoHBk2goLEksZayV_MGAkQxukvSNLCDtnE/edit#heading=h.yij8xaij9lcy) for more details.

Remember that TypeScript gives you the ability to _progressively_ type your project; it isn't an all or nothing commitment. If you like, you can convert JavaScript files to TypeScript one at a time, if migrating an existing project.

TypeScript is currently used in the following projects:

- [maas-ui](https://github.com/canonical-web-and-design/react-components/)
- [juju-dashboard](https://github.com/canonical-web-and-design/jaas-dashboard)
- [ubuntu.com](https://github.com/canonical-web-and-design/ubuntu.com)
- [react-components](https://github.com/canonical-web-and-design/react-components/)

### Patterns

#### Importing types

You can use the `type` keyword when importing a type, e.g.:

`import type { ReactNode } from "react"`;

This makes it clear that a type has been imported, rather than a component or class, and also provides some minor build optimisation via [type erasure](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-8.html#type-only-imports-and-exports).

#### How do I type that?

NPM now displays a link beside the project name in the header with a direct link to the "Definitely Typed" types for the project. Sometimes however, you'll still have difficulty finding the appropriate type. A handy escape hatch you can make use of when starting out, is to declare a placeholder type called `TSFixMe`, aliased to `any`. Using this type means that the object in question is effectively untyped, however it is easily grepable for later improvement.

```ts
export type TSFixMe = any;
```

usage:

```ts
type Props = {
  name: string;
  confusingThing: TSFixMe; // to be typed later
};
```

Similarly `ts-ignore` can be used as a last ditch escape hatch, but it's use is strongly discouraged:

```ts
if (false) {
  // @ts-ignore: Unreachable code error
  console.log("boom");
}
```

#### Typing react components

##### Props

Typically you'll want to provide a type for `props` and a return type.

`props` should be typed in the same file as the component, and typically a functional component will have the return type `JSX.Element`. TypeScript will infer a react component's type as `JSX.Element` so you do not need to explicitly include it.

```typescript
type Props = {
  name: string;
  age: number;
}

const Person = ({ name, age }: Props): JSX.Element => ()
```

Add types for any functions defined in the same module as you see fit.

##### Destructured props with `...rest`

A common pattern in react is to spread `...rest` into a child component, allowing you to pass attributes to children without manually defining the props in the parent component.

Typically, these props will be spread into either an html element, or another react component. The following are some helpful patterns for managing this with TypeScript:

When typing `...rest` for an html child, React helpfully provides the `HTMLAttributes` and `HTMLProps` generics which you can provide with a specific HTML element type. Some html elements that only inherit global attributes, like `<aside>`, have no specific type, and can be typed with `HTMLElement`. If you're using an IDE with good TypeScript support, you should find auto-completions for these types when typing `HTML`...

It can be helpful to rename `...rest` (e.g. `...divProps`) to reflect which component the props are spread into.

```tsx
// html child
import type { HTMLAttributes } from "react";

type Props = {
  colour: string;
} & HTMLAttributes<HTMLDivElement>;

const Car = ({ colour, ...divProps }: Props): JSX.Element => (
  <div {...divProps}>`My car is ${colour}.`</div>
);
```

```tsx
// react child

// Wheels.tsx
export type Props = {
  spinners: boolean;
}

export const Wheels = ({ spinners }: Props): JSX.Element => {
  if (spinners) {
    return (
      <>My car is gangsta.</>
    )
  }
  return <>My car is boring.</>
};

// Car.tsx
import { Wheels } from "./Wheels";
import type { Props as WheelsProps } from "./Wheels";

type Props = {
  colour: string;
} & WheelsProps;

const Car = ({ colour, ...wheelProps }: Props): JSX.Element => (
  <p>
    `My car is ${colour}.`
    <Wheels {...wheelProps} />
  </p>
)

// In use
<Car colour="red" spinners={false} />

// renders => "<p>My car is red. My car is boring.</p>"
```

For a real world example of this, have a look at the [Accordion component](https://github.com/canonical-web-and-design/react-components/blob/master/src/components/Accordion/Accordion.tsx#L37) in react-components.

#### Other resources

[React+Typescript Cheatsheets](https://github.com/typescript-cheatsheets/react-typescript-cheatsheet)

## Tooling

### Build tools

[Webpack](https://webpack.js.org/) is the preferred build tool for applications, and [Rollup](https://rollupjs.org/guide/en) is preferred for libraries.

Rollup and Webpack for the most part have feature parity, so this is mostly a matter of taste and convenience, given Rollup is easier to configure for library builds.

### Dependency management

We use [Yarn](https://yarnpkg.com/en) for dependency management.

### Packaging

#### Use the npm files array

Use the package.json `files` array to allowlist files for inclusion in your package. This is the safest approach, as it is explicit; using `.npmignore` is potentially dangerous, as you may end up packaging files unintentionally (credentials in a .env file being the worst case scenario!).

See [Publishing what you mean to publish](https://blog.npmjs.org/post/165769683050/publishing-what-you-mean-to-publish) for further details.

### Testing

We use the [Jest](https://jestjs.io) unit test framework.

#### General Testing Advice

- Don't test external code/libraries.
- [Test your user contract](https://fromanegg.com/post/2020/01/01/testing-your-user-contract/).
- Use factories to generate shared application state across tests with [Fishery](https://github.com/thoughtbot/fishery).

#### Testing React

- Tests should be collocated with their component in the same directory (MyComponent.tsx should have a corresponding MyComponent.test.tsx)
- If a component seems difficult to test, it might indicate that it needs to be further decomposed into smaller components.
- Unittests should test component behaviour, rather than explicit rendering. Typically you want to test state changes,
  that handlers are called with appropriate arguments, and any internal logic.
- [Jest snapshots](https://jestjs.io/docs/en/snapshot-testing) should be avoided for complex outputs as they require updating any time a layout change is made even if there is no difference in functionality. A snapshots should be small and only used when testing the important output attributes is tedious or otherwise undesirable. Snapshot tests should compliment unit tests rather than replace them, as unit tests better describe the intended behaviour and output of a component.
- Use the testing libraries `mount` methods over `shallow` where possible to ensure you're testing the full component stack.

##### Redux

- Connected components (redux containers) should be tested using [redux-mock-store](https://github.com/dmitry-zaets/redux-mock-store).
- Containers that dispatch actions should test that component behaviours dispatch the expected actions.
- [redux-saga-test-plan](https://github.com/jfairbank/redux-saga-test-plan) is a helpful tool if you're using sagas.
- Reducers, action creators and selectors should all have simple functional tests.
- Test composed Reselect selectors in isolation with [resultFunc](https://github.com/reduxjs/reselect#q-how-do-i-test-a-selector).

### Code style & formatting

To ensure code formatting consistency across our codebase, we use [Prettier](https://github.com/prettier/prettier).

### Commenting code

As a general rule, human-readable code is preferred over brevity.

Inline comments should be provided where logic or behaviour is unexpected or required due to external factors. If not explicitly clear, adding a comment to answer the "Why did they do this" can greatly help debugging in the future.

If library code, [JSDoc](http://usejsdoc.org/) comments should be provided as appropriate.

## React

### Starting a new project

When starting a new React application, we recommend [create-react-app](https://github.com/facebook/create-react-app) for bootstrapping the project. Avoid [ejecting](https://facebook.github.io/create-react-app/docs/available-scripts#npm-run-eject) as long as feasible to make updating dependencies easier.

We recommend new projects use the [hooks API](https://reactjs.org/docs/hooks-intro.html) rather than class based components. Hooks generally make components simpler, allow reuse of stateful non-visual code, and [perform better](https://reactjs.org/docs/hooks-faq.html#are-hooks-slow-because-of-creating-functions-in-render).

### Preferred libraries

All projects should generally use the following:

- Style framework - [Vanilla](https://github.com/vanilla-framework/vanilla-framework)
- Component testing(New) - [React Testing Library](https://github.com/testing-library/react-testing-library)
- Component testing(Existing) - [Enzyme](https://github.com/airbnb/enzyme)

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
- Redux toolset - [Redux Toolkit](https://redux-toolkit.js.org/)

### Reference projects

[jaas-dashboard](https://github.com/canonical-web-and-design/jaas-dashboard) - project uses the hooks API and reflects current standards.

[maas-ui](https://github.com/canonical-web-and-design/maas-ui) - project uses the hooks API and reflects current standards.

[crbs-ui](https://github.com/canonical-web-and-design/crbs-ui) (aka RBAC) - generally reflects current standards, but class based.

### File naming conventions

- Component files should use PascalCase and match the name of the default export (e.g. `MyComponent.tsx`).
- Avoid the use of non-inclusive language such as: _whitelist_, _blacklist_. A full list of non-inclusive terms can be found [here](https://github.com/canonical-web-and-design/Inclusive-naming/blob/main/config.yml).

### Variable/function naming conventions

- Variables should use camelCase and describe their use (e.g. `initialState`)
- Avoid the use of non-inclusive language such as: _whitelist_, _blacklist_. A full list of non-inclusive terms can be found [here](https://github.com/canonical-web-and-design/Inclusive-naming/blob/main/config.yml).

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
