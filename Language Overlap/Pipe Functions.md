---
tags:
  - javascript
  - FunctionTypes
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Pipe functions.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: "[[Algorithm Most Common Built in Functions]]"
Peer Reviewed: 0
dg-publish: false
---
### Composition Function (Right-to-Left)

To implement a composition function that processes values from right to left, we can use the `reduceRight()` method in JavaScript. This method applies a function iteratively against an accumulator and each element of the array, starting from the right and moving towards the left, ultimately reducing the array to a single value.

Here is an example implementation using the `reduceRight()` method:

```javascript
const comp = (...fns) => val => fns.reduceRight((prev, fn) => fn(prev), val);

const compRes = comp(multiplyBy5, sub1, add2)(4); // Returns 25
```

### Pipe Function (Left-to-Right)

To create a pipe function that processes values from left to right, we can use the `reduce()` method in JavaScript. This method executes a user-supplied reducer callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result is a single value.

Here is an example implementation using the `reduce()` method:

```javascript
const pipe = (...fns) => val => fns.reduce((prev, fn) => fn(prev), val);

const pipeRes = pipe(add2, sub1, multiplyBy5)(5); // Returns 30
```

### Debugging and Custom Functionality

For debugging purposes, a custom `pipe` function is introduced, allowing for inspection of intermediate values during the execution of the pipe.

```javascript
pipe = (...functions) => (value) => {
  debugger;
  return functions.reduce((currentValue, currentFunction) => {
    debugger;
    return currentFunction(currentValue);
  }, value);
};
```

### Pointer-Free and Curry Functions

Demonstrating a pointer-free approach where unary parameters are not explicitly seen between each function call. Additionally, a curried function example is provided for dividing by a constant.

```javascript
const divideBy = (divisor, num) => num / divisor;

const pipeRes3 = pipe(
  add2,
  sub1,
  multiplyBy5,
  x => divideBy(2, x)
)(5); // Returns 15

const divBy = divisor => num => num / divisor;
const divideBy2 = divBy(2);

const pipeRes4 = pipe(
  add2,
  sub1,
  multiplyBy5,
  divideBy2
)(5); // Returns 15
```

### Word Count Example

An example of reusable pipe functionality is demonstrated by counting words in a string.

```javascript
const lorem = "dad ada dij wdwh eicv dsc dacas cscs iihi";

const splitOnSpace = string => string.split(' ');
const count = array => array.length;

const wordCount = pipe(
  splitOnSpace,
  count
);

wordCount(lorem); // Returns 9
```

### Palindrome and Cloning Examples

Combining functions to check for palindromes and three approaches to cloning an object are demonstrated.

```javascript
const pal1 = "taco cat";
const pal2 = "UFO tofu";
const pal3 = "Dave";

const split = string => string.split(' ');
const join = string => string.join('');
const lower = string => string.toLowerCase();
const reverse = array => array.reverse();

const fwd = pipe(
  splitOnSpace,
  join,
  lower
);

const rev = pipe(
  fwd,
  split,
  reverse,
  join
);

fwd(pal1) === rev(pal1); // true
fwd(pal2) === rev(pal2); // true
fwd(pal3) === rev(pal3); // false
```

### Pure Function with Clear Dependencies

Finally, emphasizing the importance of writing pure functions with clear dependencies for positive code maintainability. Highlighting the negative aspect of non-unary functions in a pipe/compose chain, which can make the code less readable and harder to debug.







