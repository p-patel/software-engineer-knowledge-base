# Building Applications with React and Redux
https://app.pluralsight.com/library/courses/00454b2e-e8d2-43c1-9424-aa542d120404/table-of-contents

## Course Overview
- Redux - de-facto Flux implementation
- What other libraries should I use with React to be complex real-world applications?
- How to tie all these libraries and tools together

## Intro
### Course Outline
...

### Who Is This Course For?
- For gettig started with React see Building Applications with React and Flux - https://app.pluralsight.com/library/courses/react-flux-building-applications/
- You don't need to know Flux (can see the Flux module in above course)
- Learn modern JS - ES6, ES7, ES8, ES9

### How Is This Different form the React and Flux Course?
React and Flux course
- for React beginners
- uses CRA
- introduces React Router

React and Redux course
- for developers with experience using React (more advanced course)
- build a custom dev environments (without CRA, using webpack, babel etc.)
- assumer React Router knowledge
- covers testing

### Why Redux?
- Flux, Redux and many more...
- A single store / single object graph
- Reduced boilerplate (no dispatcher)
- Isomorphic friendly
- Immutable store
- Hot reloading
- Time-travel debugging
- Small (~2kB)
- Boilerplate vs. "magic" (conventions) trade-off. Less boilerplate than Flux.

## Environment Build
### Intro
- Custom React app environment alternative to create-react-app
Features:
- Compile JSX
- Transpile JS
- Linting
- Generate index.html
- Reload on save
- All with one command!
Using:
- Node
- Webpack
- Babel
- ESLint
- npm scripts

...

## React Component Approaches
### Intro
- React component creation approaches
- Container vs Presentational components

### Four Ways to Create React Components
- createClass
- ES class
- function
- arrow function

### createClass component
- `React.creatClass()`

### Class component
- `class MyComponent extends React.Component { }`

### Function component
- `function HelloWorld(props) { }`

### Arrow function component
- `const HelloWorld = (props) => <h1>Hello World</h1>`

### Functional Component Benefits
- Preferred to class components
- Easier to understand and more concise
- Avoid `this` keyword and binding
- Less transpiled code when run through Babel
- Enhanced code completion / intellisence
- Easy to test - given props, assert function returns expected return value
- Performance (no class instance)
- Introduction of hooks means classes may be removed in future

### When to Use Class vs. Function Components
- Before React v16.8, class components have to be used for state, refs and lifecycle methods
- Since React v16.8 (React Hooks), class components are only needed for `componentDidError` and `getSnapshotBeforeUpdate`

### Container vs Presentation Components
Container (back-end for the front-end) component:
- Little or no markup
- Pass data and actions down
- Know about Redux
- Stateful
- AKA smart, stateful or controller view components

Presentation (front-end) component:
- Nearly all markup
- Receives data and actions via props
- Doesn't know about Redux
- Often no state
- Most React app components are Presentation components
- AKA dumb, stateless or view components

## Initial App Structure
### Create Home Page
- convention to put components in `src/components/`

### Create About Page
- arrow function component
- `<Link>` configures link to be handle by client-side routing

### Configure App Entry Point
- configure in index.js
- Use `<BrowserRouter>` from 'react-router-dom'

### Create App Entry Point
- set layout in `<App>` component

### Create Header
- convention to use `src/components/common/` for components that are not specific to a page
- header navigation
- use `NavLink` from 'react-router-dom' to create navigation links
- use `activeStyle` prop to set style for active link

### Create 404 Page
- create a `PageNotFound` component
- configure `Switch` and `Route` components to configure a route for `PageNotFound`. Add as the last route meaning if no other route matches, this component will be rendered

## Intro to Redux
### Intro
- Managing app data flows with Redux

### Do I Need Redux?
- React context vs React with Redux
- Can lift state to a common ancestor and pass data down through components - "prop drilling"
- Can use React context to extract global data and functions - context.Provider and context.Consumer
- A centralised store (a client-side db) with Redux.  Cannot change data directly, instead must dispatch actions. Components connected to the store receive the new data and re-render

### When Is Redux Helpful?
- Complex data flows
- Inter-component communication between non-parent/child components
- When there are many actions
- When using the same data in many places
- Start with stateful components and lift state as needed, try context or Redux when lifting state gets annoying

### 3 Core Redux Principles
- A single immutable store
- Actions trigger changes
- Reducers return updated state by taking the exiting state and action and returning the new state

### Flux vs. Redux
...

### Redux Flow Overview
- React Presentation Component, Actions, Reducers and Store
- Unidirectional data flow

## Actions, Stores and Reducers
### Actions
- In Redux, events are called Actions - plain objects containing a description of an event
- action object must contain a type property
- Typically created by Action Creator convenience functions
- Handled by a reducer

### Store
- Created using `let store = createStore(reducer)`
- An app contains a single store
Store api:
- `store.dispatch(action)`
- `store.subscribe(listener)`
- `store.getState()`
- `replaceReducer(nextReducer)`
- no action to change state directly, you must dispatch an action instead
### What Is Immutability?
...

### Why Immutability?
- Clarity - state is only changed in the reducer
- Performance - no need for object property-by-property check for changes; instead if previous state reference is different to the current state then the state must have changed.
- dev tools - time-travel debugging

### Handling Immutability
#### Enforce immutability
- trust
- warning/detect - `redux-immutable-state-invariant` package (in dev environments only)
- enforce - immer, immutable.js, seamless-immutable libraries

### Reducers
- `(state, action) => new_state`
- Reducers must be pure functions
- 1 store, multiple reducers
- slices of the store's state changes can be managed by multiple reducers
- each reducer is actually only passed the slice of state that it is responsible for
- all reducers are called on each dispatch, all reducers should return the existing state as the default action
- a reducer returns a new state based on the action passed to it
- "reducer compositon": Each action can be handled by multiple reducers. Each reducer can handle multiple actions.
...

## Connecting React to Redux
### Intro
#### React-Redux
- Provider - component wraps application so that the Redux store is available
- Connect - functions used to connect props and actions to your component
- "A Chat With Redux" model to understand how Redux works
### Container vs. Presentational Components
- aka smart vs. dumb components
- how things work vs. how things look
- aware of Redux vs. unaware of Redux
- subscribe to Redux state vs. read data from props
- dispatch Redux actions vs. invoke callbacks on props

### React-Redux Introduction
- `react-redux` companion library for Redux because Redux isn't exclusive to React
- connects React components to the Redux store
  - `Provider` component - attaches app to store (uses React's context)
  - `Connect` function - creates Presentation components











