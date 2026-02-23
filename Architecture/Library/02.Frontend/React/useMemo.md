---
tags:
  - web
  - frontend
  - library
  - react
  - hooks
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses useMemo hook.
Status: Done
Started: 
EditDate: 2024-02-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
## Memoization with `useMemo` and `React.memo` in React

### `useMemo` Hook:

The `useMemo` hook in React is employed for optimization purposes, allowing you to cache the result of a function and memoize it based on a set of dependencies. It takes an array of dependencies as its second parameter.

```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

The key distinction between `useMemo` and `useCallback` lies in their caching behavior. While `useCallback` caches the provided function instance itself, `useMemo` invokes the function and caches its result. If you need to cache a function, use `useCallback`; if you need to cache the result of an invoked function, use `useMemo`.

### `React.memo`:

`React.memo` is a higher-order component that can be applied to functional components. It performs a shallow comparison of the previous and new props and re-renders the child component only if the props have changed. This mechanism can provide a performance boost in scenarios where the component renders the same result given the same props.

```jsx
const MemoizedComponent = React.memo(MyComponent);
```

#### Best Practices and Caveats:

1. **Avoid Wrapping Components with Children:**
   - Do not wrap a child component with `React.memo` if the child itself has children elements. `React.memo` is most effective when applied to leaf components without children.

2. **Careful Usage with Impure Components:**
   - Exercise caution when using `React.memo` with impure components. An impure component may have props and state that remain the same while the component itself undergoes changes (e.g., a component with time or a random function used in calculations). In such cases, consider using `useCallback` to address potential issues.

3. **Understanding `React.memo` Limitations:**
   - `React.memo` only checks for prop changes. If a function component wrapped in `React.memo` utilizes `useState`, `useReducer`, or `useContext` Hooks, it will still re-render when state or context changes.

4. **Custom Comparison Function:**
   - You can provide a custom comparison function as the second argument to `React.memo` for more control over the comparison process, especially when dealing with complex objects within the props.

```jsx
const MemoizedComponent = React.memo(MyComponent, (prevProps, nextProps) => customComparison(prevProps, nextProps));
```

By understanding these nuances and best practices, you can effectively leverage `useMemo` and `React.memo` to optimize your React components and enhance performance where necessary.