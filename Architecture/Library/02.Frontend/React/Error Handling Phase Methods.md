---
tags:
  - web
  - frontend
  - library
  - errorHandling
  - react
  - bestPractices
author:
  - jacgit18
Purpose: This documentation discusses error handling phase in react life cycle.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
In React, error boundary methods like `static getDerivedStateFromError(error)` and `static componentDidCatch(error, info)` are used to handle errors that occur during the rendering phase. When errors happen in the lifecycle methods or the constructor of a child component, these methods provide a way to gracefully manage and recover from those errors.

`getDerivedStateFromError` is a static method that allows a component to catch JavaScript errors anywhere in its child component tree. It is primarily used to update the component's state in response to an error, allowing for rendering a fallback UI.

`componentDidCatch` is another error boundary method that works similarly. It is called after an error has been thrown during rendering but is only available in class components. This method receives information about the error and the component stack, providing an opportunity to log the error or perform other error-handling actions.

By implementing these error boundary methods, React applications can prevent the entire UI from crashing due to a single error. Instead, they enable developers to handle errors gracefully, improving the user experience and making it easier to diagnose and address issues in the application.


## Example

```jsx
import React, { Component } from 'react';

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false, error: null, errorInfo: null };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    this.setState({ error, errorInfo });
    // You can log the error or perform other error-handling actions here
    console.error(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      // Fallback UI when an error occurs
      return (
        <div>
          <h2>Something went wrong</h2>
          {/* You can customize the fallback UI as needed */}
        </div>
      );
    }

    // Render the child components if no error occurred
    return this.props.children;
  }
}

class MyComponent extends Component {
  render() {
    // Simulating an error in rendering
    if (Math.random() < 0.5) {
      throw new Error('Random error occurred!');
    }

    // Your component's normal rendering logic
    return <div>Rendered successfully!</div>;
  }
}

// Using the error boundary in your application
function App() {
  return (
    <ErrorBoundary>
      <MyComponent />
    </ErrorBoundary>
  );
}

export default App;
```

In this example, `ErrorBoundary` is a class component that implements `getDerivedStateFromError` and `componentDidCatch`. It catches errors thrown by its child components, allowing you to define a fallback UI and perform error-handling actions. The `MyComponent` component intentionally throws a random error during rendering to demonstrate the error boundary in action.