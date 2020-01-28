Rapid ES6 Training - https://app.pluralsight.com/library/courses/rapid-es6-training/table-of-contents

ES5 to review:
- hoisting
- closures
- bind()


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

- in ES5, `this` in a function handling an event will evaluate to the object on which the event occurred, not the context of the function handling the event
- in ES6, `this` in an arrow function handling an event will evaluate to the context of the event handler function instead
- in ES5, `this` in an object's function will evaluate to the object
- in ES6, `this` in an object's arrow function will evaluate to the context in which the method was called!
- in ES6, cannot use `bind()` to change the context of an arrow function. `bind()` will be ignored silently. sames goes for `call()` and `apply()`.  With arrow functions you cannot change the value of `this`
- in ES6, arrow functions do not have a prototype field












