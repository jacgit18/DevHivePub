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
Status: Done
Purpose: This documentation discusses react hooks.
Started: 
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
A distinctive feature in React, hooks facilitate the use of React functionalities without resorting to class components, promoting a more functional coding style. Classes, while powerful, come with challenges such as navigating the intricacies of the 'this' keyword, binding event handlers, and suboptimal minification and hot-reloading reliability.

Unlike classes, hooks offer a straightforward approach to reusing stateful component logic, addressing the absence of a standardized method for such reusability. Patterns like Higher Order Components ([[Props#Higher Order Components (HOC) and Render Prop Pattern |HOC]]) and render props have traditionally tackled some of these challenges.

Hooks shine in simplifying the reuse of stateful logic without altering the component hierarchy, especially in scenarios involving complex components with data fetching and event subscriptions. They excel in organizing related code by allowing the definition of nested functions within a parent function.

With hooks, data fetching aligns with the [[Lifecycle methods]] of class components: `componentDidMount` and `componentDidUpdate`. Event listeners find their place in `componentDidMount` and are cleaned up in `componentWillUnmount`.

Crucially, hooks should be invoked only at the top level or in parent components. Avoid calling hooks within loops, conditions, or nested functions, and ensure usage exclusively within React functions, not standard JavaScript functions.

When working with state variables, hooks like [[useState]] accommodate various types, such as strings, booleans, numbers, objects, and arrays. Unlike class components, where state is an object, `useState` allows you to add state to functional components directly. The hook takes two parameters: the current state and a state setter function. This setter function, used as a callback in an anonymous function, updates the state based on the new value. When dealing with arrays or objects, it's recommended to spread the state variable before calling the setter function to ensure proper state updating.


