---
tags:
  - web
  - frontend
  - library
  - react
  - hooks
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses useState hook.
Status: Done
Started: 
EditDate: 2024-02-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
### `useState` Hook in React

In React, the `useState` Hook is a function that allows functional components to manage state, providing a way to declare state variables and update them. Let's break down the key aspects:

1. **Declaring a State Variable:**
   ```javascript
   import React, { useState } from 'react';

   function Example() {
     // Declare a new state variable, called "count"
     const [count, setCount] = useState(0);
   }
   ```
   - `useState(0)` declares a state variable named `count` with an initial value of `0`.
   - `setCount` is a function that will be used to update the state.

2. **Preserving State Between Renders:**
   - React maintains state variables between renders, allowing them to persist.
   - State variables, like `count`, are preserved by React and provide a mechanism similar to `this.state` in class components.

3. **Usage of `useState`:**
   - `useState` returns a pair of values: the current state value (`count`) and a function (`setCount`) to update it.
   - Destructuring is commonly used to assign names to these values, as in `const [count, setCount] = useState(0)`.

4. **Initial State Argument:**
   - The argument passed to `useState` (in this case, `0`) sets the initial state value.
   - Unlike class components, the state doesn't have to be an object; it can be a number, string, or any primitive value.

5. **Updating State:**
   - To update the state, use the function provided by `useState`. For example, `setCount(newValue)` updates the `count` state with the new value.

### `setState` in React

In class components, `setState` is used to update the component's state. The primary method to update the user interface in response to events or server responses, `setState` is a request to React to re-render the component and its children with the updated state.

#### Key Points about `setState`:

1. **Asynchronous Nature:**
   - `setState` may not immediately update the state. React might delay or batch the update for better performance.
   - To ensure code runs after the update, use `componentDidUpdate` or a `setState` callback.

2. **Using Updater Function:**
   - The first argument to `setState` is often an updater function, with the signature `(state, props) => stateChange`.
   - `state` is a reference to the current state, and `props` are the current props. It should not be directly mutated.

3. **Shallow Merge:**
   - The output of the updater function is shallowly merged with the current state.
   - If you want to make changes based on the previous state, use the updater function.

4. **Optional Callback:**
   - The second parameter to `setState` is an optional callback function that runs after the component is re-rendered.

5. **Passing Object Directly:**
   - Instead of an updater function, you can pass an object directly to `setState` for a shallow merge.

### Conclusion

`useState` and `setState` are integral parts of React's state management in functional and class components, respectively. Understanding how to declare, update, and manage state is crucial for building dynamic and interactive React applications. The asynchronous nature of state updates and the use of updater functions are key concepts to grasp when working with state in React.