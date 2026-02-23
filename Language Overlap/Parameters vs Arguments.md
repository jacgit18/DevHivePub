---
tags:
  - languageOverlap
  - functionCalls
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the distinction between parameters and arguments.
Status: Done
Started: 2024-03-02
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
While commonly used interchangeably, "parameters" and "arguments" have distinct meanings in the context of programming:

1. **Parameters:**
   - **Definition:** Parameters are variables or placeholders in a function's definition or declaration.
   - **Location:** They are part of the function signature.
   - **Purpose:** Parameters serve as placeholders for values that will be passed into the function when it is called.
   - **Example:**
     ```javascript
     function add(a, b) {
       // 'a' and 'b' are parameters
       return a + b;
     }
     ```

2. **Arguments:**
   - **Definition:** Arguments are the actual values or expressions passed into a function when it is called.
   - **Location:** They are the values provided when invoking the function.
   - **Purpose:** Arguments are the concrete data or variables that fulfill the role of the parameters during a function call.
   - **Example:**
     ```javascript
     let result = add(3, 5);
     // 3 and 5 are arguments
     ```

In the example above, `a` and `b` in the function `add` are parameters. When calling `add(3, 5)`, `3` and `5` are the arguments provided to the function.

In summary, parameters are placeholders in the function definition, and arguments are the actual values or expressions passed to the function when it is called.