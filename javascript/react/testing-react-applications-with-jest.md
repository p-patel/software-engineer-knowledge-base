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









