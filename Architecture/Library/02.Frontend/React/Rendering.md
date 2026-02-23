---
tags:
  - web
  - frontend
  - library
  - react
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses rendering in react.
Status: Done
Started: 
EditDate: 2024-02-07
Relates: "[[Lifecycle methods]]"
Peer Reviewed: 0
dg-publish:
---
## React Rendering Process

When a React app runs, the component code undergoes a two-phase process: the render phase and the commit phase.

### Initial Render Process

During the Render phase:

- Starting from the root and traversing down the component tree, React invokes the `createElement` method for each component, converting JSX into React elements.
- The produced elements are handed over to the commit phase.
- Before committing changes, React performs reconciliation, comparing the old and new Virtual DOM trees. In the commit phase, the elements are then applied to the actual DOM using the `React DOM` package. This entire process ensures a structured and efficient rendering mechanism.

### Re-Render Process
> Note: React Strict Mode double renders in dev mode

As you go down the component tree there is a check that happens where components are flagged for re-render:

- Components can self-flag for an update by calling [[useState]] or [[useReducer]].
- React invokes `createElement` for flagged components, converting them to React elements and stores that render output.
- The new elements are compared with those from the last render.
- A list of changes to the DOM is created and handed to the commit phase for application.
- Rendering isn't the same as updating the Dom it  doesn't guarantee visible DOM changes; if a component renders the same element as in the previous render, no changes are applied. 
- React batches updates for efficiency during the commit phase, though rendering can be slow.

### State Immutability

In React, when updating state for objects or arrays, it's crucial to create a new copy rather than modifying the original directly. For objects, make a copy, update values, and then set state. Likewise, for arrays, clone the array, modify the copy, and use setState (with useState or useReducer). This approach ensures proper re-rendering and aligns with JavaScript's immutability principles, preventing unintended side effects.

this relates to [[Shallow Copy and Deep Copy(clone)]]

### Parent and Child Components

- Parent and child components render on page load.
- Re-render occurs if the new state differs from the old state.
- Child components might not re-render if state values remain the same.
- React recursively renders child components when a parent component renders.
- Optimization is achieved by referencing the same element from the previous render, avoiding unnecessary renders.

#### Example

```jsx
import React, { useState, useEffect } from 'react';

// Child Component
const ChildComponent = ({ data }) => {
  console.log('Child Component Rendered');
  return <div>{data}</div>;
};

// Parent Component
const ParentComponent = () => {
  const [state, setState] = useState({ value: 0 });

  useEffect(() => {
    console.log('Parent Component Rendered');
  }, [state]);

  const handleClick = () => {
    // Creating a new object to update state
    const newState = { ...state, value: state.value + 1 };
    setState(newState);
  };

  return (
    <div>
      <button onClick={handleClick}>Increment</button>
      <ChildComponent data={state.value} />
    </div>
  );
};

export default ParentComponent;
```

This example demonstrates a ParentComponent with a ChildComponent. The ChildComponent renders based on the `data` prop, and the ParentComponent updates its state with a new object to trigger a re-render when the button is clicked. The useEffect in the ParentComponent logs a message when it renders, showcasing the re-render behavior.

### Avoiding Unnecessary Renders with Same Element Reference

- Passing child components as props helps avoid unnecessary renders.
- React optimizes re-renders by recognizing the same element reference.
- Use `Same Element Reference` when the parent component re-renders due to state changes but not prop changes.
- Avoid using `React.memo` everywhere by using `Same Element Reference` strategically.

### When to Use Same Element Reference vs. React.memo

- Use `Same Element Reference` when the parent component re-renders due to state changes (yes) but not prop changes (no).
- If a component doesn't have props, use `Same Element Reference` to avoid widespread memoization.
- Opt for `Same Element Reference` when the child component is asked to re-render due to parent state changes that don't affect child props.
- `React.memo` isn't always ideal due to the cost of shallow comparisons and potential wasted renders. Choose wisely based on your app's specific needs.