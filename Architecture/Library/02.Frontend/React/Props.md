---
tags:
  - web
  - frontend
  - library
  - react
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses react props.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
## What are Props(Properties)?

Props serve as a means to transmit data from a parent component to a child component, delivered through HTML attributes. They are immutable, preventing reassignment. In React, props and state are distinct: props are received by the component, analogous to function parameters, while state is managed within the component, akin to variables within a function.

Props serve as a component's configuration, resembling options that are passed down from a higher-level parent component. Once received, these props are treated as immutable within the recipient component, establishing a consistent and unalterable set of attributes for the component's behavior and rendering.

### Passing Props with Specific Names

Props can be passed using object brackets, and if a prop is named "props," it must be placed outside these brackets. Default props can be set to handle cases where a prop is not explicitly provided.

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}

Welcome.defaultProps = {
  name: "world",
};
```

### Props Should Not Change

Props are designed to be immutable; attempts to change them directly, which was possible with deprecated methods like setProps and replaceProps, are discouraged. A React component relying solely on props (not state) is considered "pure," consistently rendering the same output given the same input, facilitating testing.

### Prop-Drilling and Modification

1. **Prop-Drilling:**
   Prop-drilling involves passing values through multiple levels, such as Grandparent -> Parent -> Child.

2. **Modifying Props:**
   Props are read-only and cannot be directly altered. They must remain pure values and are not mutable.

### Higher Order Components (HOC) and Render Prop Pattern

- **Higher Order Components (HOC):**
  HOC is a pattern where a function takes a component as an argument and returns a new component. This allows sharing common functionality between components.

```javascript
const EnhancedComponent = higherOrderComponent(originalComponent);
```

- **Render Prop Pattern:**
  An alternative to HOC, it involves using a prop with the value of a callback function to share code between React components.

These patterns enhance component functionality and code reuse in different ways.


