---
tags:
  - web
  - frontend
  - library
  - react
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Lifecycle methods.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
During the mounting lifecycle in React, invoked when a component instance is created and inserted into the DOM, the process begins with the constructor. Here, state is initialized, and event handlers are bound to the class instance or state. It's crucial to call `super(props)` in the constructor, invoking the base class constructor for access to the overall props.

Avoid making HTTP requests in the constructor. Instead, consider using lifecycle methods like `componentDidMount` for such operations.

The `getDerivedStateFromProps` static method, though seldom used, is employed when a component's state depends on changes in props over time. This method enables updating the state based on props and supports the use of the `this` keyword.

In the `render` method, a pure function, read props and state, and return JSX/components. Avoid changing state, interacting with the DOM, or making requests here.

The `componentDidMount` method is invoked once, right after the component and its children are rendered to the DOM. It's suitable for causing side effects, such as network requests or DOM interactions.