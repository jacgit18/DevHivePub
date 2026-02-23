---
tags:
  - functionCalls
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Hoisting.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: "[[Parameters vs Arguments]]"
Peer Reviewed: 0
dg-publish:
---
JavaScript Hoisting is a mechanism in which the interpreter appears to move the declarations of functions, variables, or classes to the top of their scope during the compilation phase, before the actual execution of the code. This enables functions to be safely referenced and used in the code before their formal declarations.

### Function Declaration Hoisting

Function declarations are hoisted, allowing them to be invoked before they are declared in the code. For example:

```javascript
catName("Tiger");

function catName(name) {
  console.log("My cat's name is " + name);
}

// Result: "My cat's name is Tiger"
```

Even when the function declaration is placed after the invocation, JavaScript hoisting ensures that the function can be called without any issues.

### Variable Hoisting

Variable and class declarations are also hoisted, but it's important to note that only the declarations are hoisted, not the initializations. For example:

```javascript
console.log(num); // Returns 'undefined' from hoisted var declaration (not 6)

var num; // Declaration
num = 6; // Initialization

console.log(num); // Returns 6 after the line with initialization is executed.
```

In this case, the variable `num` is hoisted, but its initialization happens later in the code.

### Variables with `let` and `const`

Variables declared with `let` and `const` are hoisted, but they are not initialized with default values. Accessing them before initialization results in a `ReferenceError`:

```javascript
console.log(num); // Throws ReferenceError exception as the variable value is uninitialized

let num = 6; // Initialization
```

### Function and Class Expressions

Unlike function declarations, function expressions and class expressions are not hoisted. The expressions themselves are not evaluated until the line in which they are defined is executed:

```javascript
// This will throw a ReferenceError
myFunction(); // Error: myFunction is not defined

var myFunction = function() {
  console.log("I am a function expression");
};
```

### Hoisting and Execution Phases

JavaScript has two phases: compilation and execution. During the compilation phase, space and memory are allocated for functions and variables, allowing hoisting to occur. However, hoisting does not work the same way when assigning functions to variables or using arrow functions.

It's essential to understand that hoisting relies on the order of code execution, not the order of code appearance in the source file. The code will succeed as long as the line initializing a variable is executed before any line attempting to access it.

In summary, hoisting in JavaScript facilitates the usage of functions and variables before their formal declarations, contributing to the flexibility and peculiar behavior of the language.