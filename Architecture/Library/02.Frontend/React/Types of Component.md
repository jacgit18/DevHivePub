---
tags:
  - web
  - frontend
  - library
  - react
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses type of components.
Status: Done
Started: 
EditDate: 2024-02-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Components in React:

In React, components play a vital role in translating raw data into rich HTML. Understanding the distinction between props and state is crucial as they collectively form the input data for the `render()` function of a component.

#### Stateless Functional Component:

- A stateless functional component is a general JavaScript function that takes props as a parameter and returns JSX or an HTML tag.
- It is simple, easy to follow, and focuses on rendering UI based on the provided props.
- Stateless components are sometimes referred to as "dumb components" because they don't manage any state.
- Ideal for small, reusable, and presentational components.

#### Stateful Class Component:

- A stateful class component extends the component class and contains a `render` method that returns JSX.
- Stateful components maintain their own private data or state, making them suitable for complex UI logic.
- They provide lifecycle hooks and handle client-server communication and user events.
- Also known as "smart" or "container" components.

### Planning State in React:

React emphasizes one-way data flow, and planning the state for each component is crucial. Follow these steps to determine where each piece of state should live:

1. Identify every component that renders something based on that state.
2. Draw out the component tree to visualize the hierarchy.
3. Determine which component mutates or owns this state.

### React.PureComponent:

React.PureComponent is similar to React.Component but implements `shouldComponentUpdate` with a shallow prop and state comparison. It provides a performance boost when the `render` result remains the same for the same props and state.

- Use `React.PureComponent` for components where the rendering result depends only on props and state.
- Implements shallow comparison to optimize rendering.

### State in Functional Components with Hooks:
**Use functional components more for smaller reusable components **

```javascript
const Person = () => {
  const [name, setName] = useState('Andrew');

  return (
    <div>
      <h1>{name}</h1>
    </div>
  );
};
```

### State in Class Components:
**Use class component for robust dynamic components **

```javascript
class Person extends React.Component {
  constructor(props) {
    super(props);
    this.state = { name: "Andrew" };
  }

  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
        {/* If no state object */}
        <h1>{this.props.name}</h1>
      </div>
    );
  }
}
```

### Modifying State:

- Never modify state directly. The only place to assign `this.state` is the constructor.
- Use `setState` for state updates, and ensure correct state values by using the updater function.

```javascript
this.setState((prevState, props) => ({
  count: prevState.count + 1
}), () => console.log(`Callback Val ${this.state.count}`));
```

### Component Structure:

- Use div when applying CSS position properties like flexbox or grid.
- Utilize React fragments (`<> </>`) for conditional rendering or when using keys.
- Prefer arrow functions for smaller components, and regular functions for export or multi-line functions.

```javascript
export const test = () => {
  // Just no default export
};
```

By following these best practices, you can create well-structured React components with clear state management and efficient rendering.