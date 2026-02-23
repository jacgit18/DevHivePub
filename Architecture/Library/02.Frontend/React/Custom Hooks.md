---
tags:
  - web
  - frontend
  - CodebaseDecision
  - library
  - react
  - hooks
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what custom hooks are.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: "[[Hooks]]"
Peer Reviewed: 0
dg-publish:
---
A custom hook in JavaScript is essentially a function prefixed with "use." It has the flexibility to utilize other hooks as necessary. Custom hooks serve as a way to share logic between multiple components, offering an alternative to Higher-Order Components ([[Props#Higher Order Components (HOC) and Render Prop Pattern |HOCs]]) and Render Props.

Here's an example of a custom hook that manages a simple counter:

```javascript
import { useState, useEffect } from 'react';

const useCounter = (initialValue, step) => {
  const [count, setCount] = useState(initialValue);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  const increment = () => {
    setCount(count + step);
  };

  const decrement = () => {
    setCount(count - step);
  };

  return { count, increment, decrement };
};

// Example usage in a component:
const MyComponent = () => {
  const { count, increment, decrement } = useCounter(0, 1);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};
```

In this example, `useCounter` is a custom hook managing a counter state with increment and decrement functions. The component `MyComponent` then uses this custom hook to easily integrate the counter logic.

