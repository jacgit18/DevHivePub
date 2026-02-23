---
tags:
  - javascript
author:
  - jacgit18
Purpose: This documentation discusses Enhanced object literals.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Exploring Enhanced Object Literals in JavaScript

Enhanced Object Literals in JavaScript provide a concise and readable syntax for defining objects, especially when including functions. Let's refine your example:

```javascript
// Example using Enhanced Object Literals
window.onload = function () {
  let name = "tom";
  let belt = 'black';

  // Enhanced Object Literal with properties and a function
  let ninja = {
    name,
    belt,

    // Function within the object
    chop(x) {
      console.log(`Chop ${x} times`);
    }
  };

  // Accessing and invoking properties and functions
  console.log(ninja.name);   // Output: tom
  console.log(ninja.belt);   // Output: black
  ninja.chop(5);             // Output: Chop 5 times
};
```

Key points:

- Enhanced Object Literals use a shorthand syntax for defining properties when the variable name matches the property name.
- Functions can be included directly in the object without using the `function` keyword, making the code more concise.
- Accessing properties and invoking functions within the object is straightforward.

Note: Corrected the typo in `console.log` and provided clearer comments for better understanding.