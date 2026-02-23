---
tags:
  - web
  - frontend
  - library
  - react
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses componentWillUnmount() lifecycle method.
Status: Done
Started: 
EditDate: 2024-02-07
Relates: "[[Lifecycle methods]]"
Peer Reviewed: 0
dg-publish:
---
The `componentWillUnmount()` lifecycle method is called immediately before a React component is unmounted and destroyed. During this phase, you can perform cleanup operations, such as canceling network requests, removing event handlers, unsubscribing from any subscriptions, and invalidating timers created with `setTimeout` or `setInterval`. Importantly, it's crucial to note that you should never set state within the `componentWillUnmount()` method, as the component is about to be unmounted and any state changes would be ineffective.

Here's the refined explanation:

The `componentWillUnmount()` lifecycle method is invoked just before a React component is unmounted and removed from the DOM. This phase is ideal for cleanup tasks, including the cancellation of network requests, removal of event handlers, unsubscription from any subscriptions, and invalidation of timers created with `setTimeout` or `setInterval`. It's important to emphasize that modifying state within `componentWillUnmount()` is inappropriate, as the component is in the process of being unmounted, and any state changes won't have any impact.



```jsx
import React, { Component } from 'react';

class ExampleComponent extends Component {
  constructor(props) {
    super(props);
    this.timerId = null;
  }

  componentDidMount() {
    // Set up a timer when the component mounts
    this.timerId = setInterval(() => {
      console.log('Timer is ticking...');
    }, 1000);
  }

  componentWillUnmount() {
    // Cleanup operations before the component is unmounted
    console.log('Component will unmount. Cleaning up...');
    
    // Cancel network requests, remove event handlers, or unsubscribe from subscriptions
    // In this case, clear the interval timer
    clearInterval(this.timerId);
  }

  render() {
    return (
      <div>
        <p>Example Component</p>
      </div>
    );
  }
}

export default ExampleComponent;
```

In this example, the `componentDidMount()` method sets up an interval timer using `setInterval()`. The `componentWillUnmount()` method is then used to perform cleanup operations, such as clearing the interval timer with `clearInterval()` before the component is unmounted. This pattern is commonly employed for handling resource cleanup to avoid memory leaks in React applications.

