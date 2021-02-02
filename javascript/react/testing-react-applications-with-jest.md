# Testing React Applications with Jest
https://app.pluralsight.com/course-player?courseId=80470d27-55fc-400c-ab36-fe429af6938a

## Course Overview
- 

## Course Introduction

### Why Take This Course?
- Also see the course 'Isomorphic React' https://app.pluralsight.com/courses/isomorphic-react

### Get the Course Files Here
- https://github.com/danielstern/isomorphic-react

### Course Roadmap
- General understanding of testing and related architecture
- Jest, test running and detailed api analysis
- Mocking
- Unit, component and snapshot testing

## Understanding Testing
...

## Introduction to Jest
### Introduction
- Jest team includes members from the React team

### The Jest Testing Ecosystem
- Enzyme is another test tool and can be used with Jest
- test runner organises tests into "describe" and "it" blocks
- Jest is built on top of Jasmine and Mocha
- Jest adds snapshot testing, mocking and other features
- Jest adds a superior assertion library and CLI
- Enzyme (from AirBnb) expresses component output as HTML (like React Test Renderer)

### Jest vs. Mocha
- Both test runners
- Both can run asynchronous tests
- Jest includes spies, snapshot testing and module mocking

### Jest Versions
- Jest and Jest CLI

### Jest and React - What's the Connection?
- Jest is a test suite that is recommended by the React
- Jest is the tool of choice for testing many other applications

### Practical Jest Usage
- Watcher is triggered by NPM on development start script
- CI suite runs tests and rejects failings PRs on integration server
- Devs review coverage reports and CI hooks

### Common Jest Pitfalls
...

### Summary
...

## Test Running With Jest
### Jest Installation
...

### Jest Installation - Demo
- install `npm i -g jest-cli`
- run `jest`
- install locally `npm install --save jest`

### Running Tests
- `jest` runs jest CLI
- add to scripts in package.json:
`"test: jest`

### Creating Test Files
- Any files dir `__tests__/*.js` will be attempted to be run by Jest
- ...also `*.spec.js` and `*.test.js` files

### Jest Globals
- `Describe()` and `It()` globals

### Jest Globals - Demo
...

### Watching for Changes
- watch mode - only tests relating to changed files are run
- Jest detects changes automatically
- `jest --watch` runs Jest in watch mode

### Setup and Teardown
- `BeforeEach()`, `BeforeAll()` and `AfterEach()`, `AfterAll()` globals

### Setup and Teardown - Demo
...

### Skipping and Isolating Tests
- `it.only()` to isolate a test
- `it.skip()` to skip a test

### Async Testing
- 3 methods: callback, Promise, async/await
- callback:
```
it("callback test", done => setTimeout(done, 100));
```
- Promise:
```
it("promise test", () => return new Promise(resolve => setTimeout(1000)));
```
- async/await:
```
it("async/await test", async () => await delay(100));
```

## Mocking Functions and Modules
### Why Mocking?
...

### What Is Mockng?
...

### The Mocking Process
Mocks meet the contract of the mocked object, adding spies into the object's function calls

### Mock Functions
- Implemented as spies - count function calls, load with return values

### Creating Mock Files
- Appropriately named NPM mocks are loaded automatically
- Convention is to place mocks in a `__mocks__` (dunder) folder next to the mocked module
- Both NPM and local modules can be mocked

### Mocking - Demo
- `jest.fn()` - Jest spy function
- `expect(x).toHaveBeenCalledWith(y)` asserts

### Automatic and Manual Mocking
- Jest can be configured to generate any required mocks automatically
- Manual mocks will be automatically be used for NPM modules (but not local modules)

## Snapshot Testing
### What Is a Snapshot?
- JSON-based record of component's output
- Snapshots are committed to the repo with the tests

### How Snapshot Testing Works
- `expect(tree.toJSON()).toMatchSnapshot();` - on the first call the snapshot it taken, on subsequent calls the component's output is compared to the snapshot
- render a component as JSON and compare to the saved snapshot

### Snapshot Testing Demo
- `npm i --save react-test-renderer` - install component renderer
- `renderer.create(<TagsList tags={['css', 'html', 'go']} />).toJSON();`

### Advantages and Disadvantages of Snapshot Testing
**Advantages**
- Quick and easy
**Disadvantages**
- Protects only against regression

### Updating Snapshots
- `jest --update` or `jest -u` updates snapshot

### Updating Snapshots Demo
...

## Testing Components
### Introduction
- Verify output has not regressed
- Verify edge/corner cases produce the correct output
- Verify component side effects occur without generating them
- Verify user interactions are handled as expected

### Building Testable Components
- Types of components: with/without lifecycle handlers, with/without internal state, may/may not generate side effects, may get state from arguments or from external dependencies
- No internal state, no side-effects, no lifecycle hooks = component easier to test

### React Redux and Jest
- In React Redux, components don't generate side effects
- Component consists of logical display and container components
- Components do not have internal state
Approach:
- Test Container and Display elements separately
- Use unit tests to verify methods and properties passed by the container are correct
- Use snapshots to verify the output of the display component, passing props directly

### React Redux Container Testing Demo
- Snapshot regression tests Display element of a React Redux component
- Unit test Container element of the same component
- Combined, these provide good component coverage
- assert component state using `const componentState = mapStateToProps(appState, ownProps);`

### React Redux Display Testing Demo
- render Display using React Test Renderer and assert html output using `expect(tree.toJSON()).toMatchSnapshot();`

### React Renderer vs. Enzyme
React Renderer:
- Takes a React component and outputs the resulting HTML without a DOM
- Useful for getting the output HTML of t component for snapshot tesing
- Built by React team and recommended by the Jest team
Enzyme:
- Also takes a React component and outputs the resulting HTML without a DOM
- From the respected AirBnB team
- Useful for testing a variety of interactions including click, keyboard input and more
- Has a variety of open bugs (as of 2018)

### Testing React Components
- Mock dependencies, then test them
- Use spies to verify side-effects
- Refactor logic from lifecycle to services
- Use snapshots to prevent regression
- Inject values by writing mocks for services
- Make stateless components, where possible (for new components and rewriting old components)

### Building a Stateful React Component
...

### Testing a Stateful React Component
- create local module mock in a `__mocks__` directory next to real module
- create `__helperFunction()` (dunder prefixed) functions in mock for mock setup functions such as `__setCount()`
- to use a mock of a local module in a test file, use `jest.mock('../path/to/local/mocked/module');`
- to import the service mock use `const notificationService = require('../path/to/local/mocked/module').default` (after `jest.mock()` and the `require()` does not get hoisted

## Advanced Jest Matchers
### What Is a Matcher?
- also known as an assertion or expectation
