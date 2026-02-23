---
tags:
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses currying.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: "[[Callback]]"
Peer Reviewed: 0
dg-publish: false
---
Currying is an advanced technique used in various programming languages, including JavaScript. It transforms a function from being callable as `f(a, b, c)` to `f(a)(b)(c)`.

Let's start with a basic example:

```javascript
function curry(f) {
  return function(a = 1) {
    return function(b = 2) {
      return f(a, b);
    };
  };
}

// Usage
function sum(a, b) {
  return a + b;
}

let curriedSum = curry(sum);

// Two function calls
alert(curriedSum(1)(2)); // 3
```

In this example, `curry(func)` returns a wrapper function, enabling both normal and partial function calls. [[Use of closure & composition |Closure]] is being used to pass the function `sum` to `curry` as a callback. 

More advanced implementations, like `_.curry` from the lodash library, provide additional flexibility:

```javascript
let curriedSum = _.curry(sum);

// Both normal and partial calls
alert(curriedSum(1, 2)); // 3
alert(curriedSum(1)(2)); // 3
```

**Practical Application: Logging Function**

Consider a logging function:

```javascript
function log(date, importance, message) {
  alert(`[${date.getHours()}:${date.getMinutes()}] [${importance}] ${message}`);
}

log = _.curry(log);

// Usage examples
log(new Date(), "DEBUG", "some debug");
log(new Date())("DEBUG")("some debug");

// Convenience functions for partial logs
let logNow = log(new Date());
logNow("INFO", "message");
let debugNow = logNow("DEBUG");
debugNow("message");
```

**Advanced Curry Implementation**

Here's an advanced curry implementation for multi-argument functions:

```javascript
function curry(func) {
  return function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args);
    } else {
      return function(...args2) {
        return curried.apply(this, args.concat(args2));
      };
    }
  };
}

// Usage examples
function sum(a, b, c) {
  return a + b + c;
}

let curriedSum = curry(sum);
alert(curriedSum(1, 2, 3)); // 6
alert(curriedSum(1)(2, 3)); // 6
alert(curriedSum(1)(2)(3)); // 6
```

**Currying Alt Syntax**

Using an alternative syntax for currying:

```javascript
function checkStock(stockID) {
  return warehouseID => stockDeduct => {
    // Check code
    if (err) {
      throw err;
    }
    return stockID + ' from ' + warehouseID + ' is reduced by ' + stockDeduct;
  };
}

// Usage example
let orderItem298 = checkStock('FN9382')('SOUTH')(3);
```

Currying can be powerful for elegant step-by-step function calls, but it should be applied selectively to avoid deep nesting.

**Additional Example: Building a Sandwich**

```javascript
const buildSandwich = ingredient1 => ingredient2 => ingredient3 =>
  `${ingredient1}, ${ingredient2}, ${ingredient3}`;

const mySandwich = buildSandwich("Bacon")("Lettuce")("Tomato");
console.log(mySandwich);

// Additional example with a curried multiplier function
const multiCurr = x => y => x * y;
const timeTen = multiCurr(10);

console.log(timeTen(8)); // 80

// Example with updating HTML elements
const updateElement = id => content => {
  document.querySelector(`#${id}`).textContent = content;
};

const updateHeaderText = updateElement('header');
updateHeaderText('Hello Dave');
```

These examples showcase the flexibility and usefulness of currying in various scenarios.






