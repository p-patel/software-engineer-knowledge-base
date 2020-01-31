Rapid ES6 Training - https://app.pluralsight.com/library/courses/rapid-es6-training/table-of-contents

ES5 to review:
- hoisting
- closures
- this, bind() / call() / apply() - https://medium.com/@omergoldberg/javascript-call-apply-and-bind-e5c27301f7bb
- strict mode
- constructor function
- prototype property
- `window` is global scope / variable in browsers (cf. Node.js)


# Introduction
## Introduction
## An ES6 Compatibility Chart
- http://kangax.github.io/compat-table/es6/

# New ES6 Syntax
## Introduction
- let, const and block scoping
- arrow functions =>
- default function parameters
- rest and spread ...
- object literal extensions
- for...of loop
- octal and binary literals
- template literals
- destructuring

## let, const and block scoping
- `let` removes hoisting
- block scoping will remove let defined variables at the end of the block
- compare closure created in a loop iteration for `let i=0` vs `var i=0`
- `let` variables and `const` values are block scoped

## Arrow functions
- No parentheses required if only one parameter
- Parentheses required if zero or more than one parameter
- `return` required to return a value if block is used to defind arrow function
- in ES5, `this` in a function handling an event will evaluate to the object on which the event occurred, not the context of the function handling the event
- in ES6, `this` in an arrow function handling an event will evaluate to the context of the event handler function instead
- in ES5, `this` in an object's function will evaluate to the object
- in ES6, `this` in an object's arrow function will evaluate to the context in which the method was called!
- in ES6, cannot use `bind()` to change the context of an arrow function. `bind()` will be ignored silently. sames goes for `call()` and `apply()`.  With arrow functions you cannot change the value of `this`
- in ES6, arrow functions do not have a prototype field

## Default Function Parameters



# ES6 Modules and Classes
## Introduction and Setup
- ES6 transpilers - Traceur, Babel
- ES6 module loader
- `System.import(./base.js);` - no longer need to list every js file in the html file

## Module Basics
- using `import`, `export`:
```
import { projectValue } from 'project.js'; // in base.js
export let projectValue = 99 // in project.js
```
- import statements are hoisted and executed before other expressions in js files
- every module can have upto 1 default export and can be imported using `import` without `{}`:
```
import project from 'project.js`; // in base.js
export default let projectValue = 99; // in project.js
```
- import multiple exports from a module in a single statement:
`import { projectName, projectValue } from 'project.js'; // in base.js`
```
// in project.js
export let projectName = 'someProjectName';
export let projectValue = 99;
```
- can also use `{}` to specify an alias when importing a module default
- `import { project as proj } from 'project.js; // 'project' alias will now no longer work;`
- import all module exports as a single object
```
import * as projStuff from 'project.js' // in base.js
```

## Named Exports in Modules
- cannot update the value of a named exported variable
```
// in base.js
import { projectValue } from 'project.js' 
projectValue = 100; // error!

// in project.js
export let projectValue = 99;
```
- can change the value of a named exported object's property in base.js
```
// in base.js
import { project } from 'project.js' 
project.projectValue = 100;
console.log(project.projectValue);

// in project.js
export let project = { 
  projectValue = 99,
  projectName = "projectName"
  }
```
- can access the changed value of a named exported object's property in the module it was exported from
```
// in base.js
import { project } from 'project.js' 
project.projectValue = 100;
console.log(project.projectValue);
console.log(project.getProjectValue);

// in project.js
export let project = { 
  projectValue = 99,
  projectName = "projectName",
  getProjectValue = function() { return this.projectValue; }
  }
```
- can change the value of a named exported function in the module it was exported from and access the updated function using the named export in the calling module
```
// in base.js
import { project } from 'project.js' 
project.projectValue = 100;
console.log(project.projectValue);
console.log(project.getProjectValue);

// in project.js
export function showProject = function() { console.log("in original"); }
export updateFunction = function() { showProject = function() { console.log("in updated"); }; };
```

## Class Fundamentals
- new `class` keyword, new way to work with constructor functions and object prototypes
- `class` definition can be assigned to a variable and then called
```
let task = class Task { }
let newTask = new task();
```


- cannot use `,` between class member declarations (unlike ES5 object literals)
- cannot declare variables within a class definition (use properties, static properties)
- functions defined globally are defined on the `window` object, classes are not









