---
tags:
  - web
  - frontend
  - library
  - react
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the intricacies of using props and states together.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: "[[Props]]"
Peer Reviewed: 0
dg-publish:
---
Before distinguishing between props and state, let's identify their commonalities:

- Both props and state are plain JS objects.
- Changes to either trigger a render update.
- They are deterministic; If your Component generates different outputs for the same combination of props and state then you're doing something wrong. 

### Decision Guide:
> tl;dr: If a Component needs to alter one of its attributes at some point in time, that attribute should be part of its state, otherwise it should just be a prop for that Component. 

#### Props:
A component is unable to modify its props, yet it assumes the responsibility of assembling the props for its child components. 

When it comes to changing props:

- Props can receive an initial value and be modified by the parent component.
- Default values can be set inside the component, but any changes must occur externally.
- Initial values for child component props can be established, and modifications can be made within the child component.

Props essentially serve as a means of conveying data from parent to child, encapsulating information set by the parent component (with optional defaults) that remains immutable within the receiving component.

```javascript
// Example of using props in a child component
const ChildComponent = ({ propValue }) => {
  return <div>{propValue}</div>;
};
```

#### State:

The state is a snapshot with default values at component mount and undergoes mutations over time, primarily triggered by user events. It represents a serializable snapshot of a specific moment.
- In essence, state is comparable to a variable scoped to a function; the state object stores property values specific to the component. When the state changes, the component re-renders.
- Internally managed, a component handles its own state, maintaining a private nature except for setting the initial state. It is a mutable entity confined within the component, and its management differs between functional components using the `useState` hook and class components using `this.state`.

```javascript
// Example of using state in a functional component
const MyComponent = () => {
  const [count, setCount] = useState(0);

  const updateCount = () => {
    setCount(count + 1);
  };

  return (
    <button onClick={updateCount}>
      Clicked {count} times
    </button>
  );
};
```

#### Changing Props and State:
- Props in React have initial values that can be passed from a parent component to a child component, but once set, these values are immutable from the parent. The parent component cannot directly change the values of props in the child component after the initial rendering.
- Default values can be established within a Component and modified internally.
- In React, a parent component can pass initial state values to its child components through props. However, once the child component has its initial state set, it cannot be directly altered externally by the parent or any other component. The state is managed internally within the component that owns it.
- State encapsulates "private" information for a component's self-initialization, modification, and utilization.
- State is exclusively designated for interactivity, representing data that undergoes changes over time.
### Keeping Track of Data:

When a component necessitates the management of information across renderings, it can create, update, and utilize state internally. The initial data may be hardcoded or obtained from props.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  handleClick = () => {
    this.setState((prevState) => ({
      count: prevState.count + 1
    }));
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleClick}>Increment Count</button>
      </div>
    );
  }
}
```

In React, setState() enables the updating of state and triggers a re-render of the component automatically. It provides access to prevState within the callback, ensuring access to the previous state, even after state modifications elsewhere.

However, a common pitfall arises when attempting to update state directly like this.state.count = this.state.count + 1. This approach bypasses React's ability to monitor state changes, resulting in a failure to re-render the component. Always use setState() to update state values.

Two key warnings regarding setState():

1. **Avoid Direct Assignment:**
   It's tempting to directly modify state using `this.state.count = this.state.count + 1`, but this circumvents React's state management mechanism and prevents proper re-rendering. Always use `setState()`.

2. **State Updates May Be Asynchronous:**
   `setState()` may update state asynchronously, especially when it's called within event handlers or lifecycle methods. Thus, relying on the immediate state after calling `setState()` may yield unexpected results.


