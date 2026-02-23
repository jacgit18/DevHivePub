---
tags:
  - CodingProblem
  - pattern
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Memoization more in-depth.
Status: Done
Started: 
EditDate: 2024-02-29
Relates: "[[Dynamic programming Patterns]]"
Peer Reviewed: 0
dg-publish:
---
![[Memoization.gif]]

Memoization is a valuable technique in computer science and Dynamic Programming Pattern. It involves caching and storing previously computed results of expensive function calls so that you can reuse them in future calls. This can significantly improve the performance of recursive or repetitive algorithms.


Here is an example of a memoization decorator function in TypeScript that can handle multiple parameters:

```typescript
const memoize = (fn: (...args: any[]) => any) => {
  const cache: { [key: string]: any } = {};

  return (...args: any[]) => {
    const key = JSON.stringify(args);

    if (key in cache) {
      // If you want to verify that the result comes from the cache, you can log it
      console.log(cache);
      return cache[key];
    }

    const result = fn(...args);
    cache[key] = result;
    return result;
  };
};
```

In this example, the `memoize` function is a decorator that takes a function (`fn`) as its argument. It returns a new function that performs memoization for the given function.

Here's how you can use it:

```typescript
// Define a function that you want to memoize
function expensiveOperation(x: number, y: number): number {
  // Simulate a time-consuming calculation
  return x + y;
}

// Create a memoized version of the function
const memoizedExpensiveOperation = memoize(expensiveOperation);

// Call the memoized function
console.log(memoizedExpensiveOperation(3, 4)); // This result will be cached
console.log(memoizedExpensiveOperation(3, 4)); // This result will be retrieved from the cache
console.log(memoizedExpensiveOperation(5, 6)); // This result will be cached separately
```

![[FibClosureMemiozation.png]]

With memoization, you can save the results of expensive function calls and retrieve them quickly when the same inputs occur again, reducing computation time and improving overall performance.


