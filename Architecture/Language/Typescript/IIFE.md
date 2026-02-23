---
tags:
  - FunctionTypes
  - javascript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Immediately Invoked Function Expression.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
IIFE, or Immediately Invoked Function Expression, is a JavaScript design pattern used to create a function and execute it immediately after its creation. It is a self-invoking anonymous function enclosed within parentheses.

#todo/Low/Dev 
- [ ] Look into https://dev.to/bytebodger/use-cases-for-iifes-5gdg

Here's a simple example:

```javascript
(function() {
    // Your code here
    console.log("IIFE executed!");
})();
```

Let's break it down:

1. **Enclosing Parentheses:** The function is wrapped in parentheses, turning it into an expression. This step is crucial for invoking the function immediately.

2. **Anonymous Function:** The function itself is anonymous, meaning it doesn't have a name. This is common in IIFE, as the function is usually created for a specific purpose and doesn't need to be referenced elsewhere.

3. **Invocation Parentheses:** Following the closing brace of the function, another pair of parentheses immediately invokes the function.

The primary benefits of IIFE include:

- **Isolation of Scope:** Variables declared inside the IIFE are not accessible from the outside. This helps avoid polluting the global scope.

- **Avoiding Naming Collisions:** Since the function is anonymous and self-contained, it reduces the risk of naming conflicts with other parts of the code.

- **Immediate Execution:** The function is executed as soon as it's defined, making it suitable for one-time initialization tasks.

Common use cases for IIFE include creating private variables, initializing modules, or setting up configurations.

## Advanced Implementation


1. Arrow function IIFE:
```javascript
(() => {
    // Your code here
})();
```

2. Async IIFE:
```javascript
(async () => {
    // Your code here
})();
```

3. Recursion using IIFE:
```javascript
(function myIIFFE () {
    ++num;
    console.log(num);
    return num !== 5 ? myIIFFE(num) : console.log("finish");
})(num = 0);
```

4. Module pattern using IIFE:
```javascript
const Score = (() => {
    let count = 0;

    return {
        current: () => count,
        increment: () => ++count,
        reset: () => count = 0
    };
})();
```

5. Module pattern variation:
```javascript
const Game = (() => {
    let count = 0;

    return {
        current: current,
        increment: increment,
        reset: reset
    };
})();
```

6. Namespace injection using IIFE:
```javascript
((namespace) => {
    namespace.count = 0;
    namespace.current = () => `App count is ${this.count}`;
    namespace.increment = () => { this.count++ };
    namespace.reset = () => { this.count = 0 };
})(window.App = window.App || {});
```

These snippets showcase the versatility of IIFE in different scenarios, demonstrating its usage in various contexts.