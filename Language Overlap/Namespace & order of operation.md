---
tags:
  - codeExecution
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses name space and order of the operations of code.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: "[[Flow of Control]]"
Peer Reviewed: 0
dg-publish:
---
### JavaScript Namespace and Scope:

A namespace in programming provides scope to identifiers, preventing collisions between names in different contexts. In JavaScript, which lacks native namespace support, we can emulate it by creating a global object containing functions and variables.

#### Scope Chain in JavaScript:

JavaScript's scope chain follows a hierarchy:

1. Global Scope: Accessible only to itself.
2. Outer Scope: Similar to a parent function, accessible to itself and the global scope.
3. Inner Scope: The lowest scope, accessing both outer and global scopes.

#### Variable Scoping Examples:

```javascript
// Function-scoped variable with 'var'
for (var i = 0; i < 5; i++) {
    console.log(i); // Outputs 0 to 4
}
console.log(i); // Outputs 5 since 'var' is function-scoped

// Blocked-scoped variable with 'let'
for (let j = 0; j < 5; j++) {
    console.log(j); // Outputs 0 to 4
}
// console.log(j); // Won't run, as 'let' is blocked-scoped

// 'const' is also blocked-scoped
const exampleConst = "Blocked Scoped";

// Order of Operation
console.log(typeof 1); // Outputs 'number'
console.log(typeof (typeof 1)); // Outputs 'string'
```

### Conclusion:

JavaScript lacks native namespace support, but we can emulate it by organizing functions and variables within a global object. Understanding scope chains and the differences between 'var,' 'let,' and 'const' is crucial for effective variable scoping in JavaScript. The examples showcase the impact of scoping on variables and the order of operations when using the `typeof` operator.