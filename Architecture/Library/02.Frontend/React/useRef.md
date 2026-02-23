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
Purpose: This documentation discusses useRef hook.
Status: Done
Started: 
EditDate: 2024-02-14
Relates: 
Peer Reviewed: 0
dg-publish:
---
## `useRef` Hook in React:

`useRef` is a React hook that returns a mutable ref object whose `.current` property is initialized to the passed argument (`initialValue`). The ref object persists for the full lifetime of the component, allowing you to store mutable values that persist across re-renders.

### Common Use Cases

```javascript
function TextInputWithFocusButton() {
  const inputEl = useRef(null);

  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };

  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

Here, `useRef` is utilized to create a reference (`inputEl`) to a text input element. The `onButtonClick` function is then used to focus on the input element imperatively.

### More on `useRef`:

- **Mutable Value Container:**
  - `useRef` is like a "box" that can hold a mutable value in its `.current` property.

- **Not Just for DOM Access:**
  - While commonly used for accessing the DOM, `useRef` is handy for keeping any mutable value around, similar to instance fields in classes.

- **Persistence Through Renders:**
  - The ref object persists through re-renders, and `useRef` gives you the same ref object on every render.

- **No Re-renders on Changes:**
  - Mutating the **.current** property doesn't cause a re-render. It's useful for storing values that shouldn't trigger additional renders.

- **Callback Refs:**
  - If you need to be notified when the ref content changes, consider using a [callback ref](https://reactjs.org/docs/hooks-faq.html#how-can-i-measure-a-dom-node).

### Use Cases:

- **DOM Node Reference:**
  - Used to store the reference of a DOM node, making it accessible using the `ref` attribute.

- **Mutable Value Storage:**
  - Can store any mutable value, and the value persists through re-renders without causing additional renders.

- **Instance Property Equivalent:**
  - Acts as a generic container for mutable values, similar to instance properties on a class component.

### Data Flow and Component Hierarchy:

- **Common Owner Component:**
  - Find a common owner component in the hierarchy, ideally a single component above others that need the state.

- **Ownership of State:**
  - Either the common owner or another component higher up in the hierarchy should own the state.

- **Creating a New Component:**
  - If no suitable component owns the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner.

### Refs for Direct DOM Access:

- **Accessing DOM Nodes:**
  - Refs are useful for direct access to DOM nodes, like focusing on a username field in a login page.

- **Typical Usage:**
  - Often created in the constructor, added as a ref property to a tag, and assigned to the ref from the constructor.

- **Event Handling:**
  - Refs can be used to access input values in event handlers, enhancing user interactions.

- **Functional Components:**
  - Unlike class components, refs in functional components persist between renders.

### Forwarding Refs:

- **Passing Refs:**
  - Forwarding refs involves passing a ref from a component to its child.

- **Enhanced Communication:**
  - This mechanism allows enhanced communication between parent and child components, especially when dealing with functional components.

These aspects showcase the versatility of `useRef` beyond DOM access, providing a powerful tool for managing mutable values and optimizing certain aspects of React applications.