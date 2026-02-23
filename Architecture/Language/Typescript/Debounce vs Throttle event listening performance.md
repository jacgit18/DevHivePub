---
tags:
  - performance
  - WebDevelopment
  - javascript
  - events
  - APICalls
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the difference between Throttling and Debouncing.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish:
---
Addressing performance concerns is a common challenge in JavaScript applications, and two essential techniques for achieving better control over function invocation rates are throttling and debouncing. These techniques are indispensable for web developers, particularly in scenarios involving event handler assignments.

Throttling and debouncing become crucial when dealing with situations where invoking functions excessively is undesirable. Consider a callback intended to execute upon a window resize. Is it practical to trigger the callback with every resize event? Most likely not. Instead, it's preferable to wait until the user has finished interacting before firing the callback.

So, what distinguishes throttling from debouncing?

**Throttling:**
Throttling can be likened to a car throttle, where the foot's pressure limits the gas flow into the engine. In this context, the goal is to restrict the frequency of function invocation. Think of it like a lottery where only one ball is drawn every five seconds, or a bar with a policy allowing you to order drinks only every 45 minutes. Throttling ensures that, even if you attempt multiple invocations within a short timeframe, only one is executed after the throttle interval. This is analogous to ordering a drink in the 15th minute but receiving it in the 45th minute. Throttling is beneficial for scenarios like preventing spam clicks, limiting API calls, or managing event handlers like mousemove or touchmove.

**Debouncing:**
Debouncing operates differently, waiting until there are no more changes inbound before executing the function. It's akin to ordering food at a restaurant, where the waiter or waitress asks if your order is complete before proceeding. If additional items are added, the process repeats until you're clear to proceed. For instance, debouncing is useful for an autosave feature, ensuring that the save function is only triggered when the user hasn't made updates or interacted for a specified period, preventing unnecessary and performance-hindering saves.

Example use cases for throttling and debouncing include:

- **Throttling:**
  - Button click to prevent spam clicking
  - Throttling API calls to manage request frequency
  - Throttling mousemove/touchmove event handlers for performance optimization

- **Debouncing:**
  - Debouncing a resize event handler
  - Debouncing a scroll event handler
  - Debouncing a save function in an autosave feature

While throttling is less commonly used than debouncing, both techniques play critical roles in optimizing performance. When considering throttling, it's often worthwhile to evaluate whether a debounce approach might be more suitable for the specific use case. Ultimately, these techniques empower developers to strike a balance between responsiveness and resource efficiency in their applications.


### Implementing Throttle and Debounce in JavaScript

Throttle and debounce are crucial techniques for controlling the frequency of function execution. Although various implementations exist, many share a common approach centered around the use of setTimeout. Let's explore simplified versions of both throttle and debounce.

#### Debounce Implementation:

```javascript
const debounce = (func, delay) => {
  let inDebounce;

  return function () {
    const context = this;
    const args = arguments;

    clearTimeout(inDebounce);

    inDebounce = setTimeout(() => func.apply(context, args), delay);
  };
};
```

In this debounce function, a delay period is tracked by the `inDebounce` variable. If the function is invoked during this period, the delay restarts. A practical example of using debounce:

```javascript
debounceBtn.addEventListener('click', debounce(function () {
  console.info('Hey! It is', new Date().toUTCString());
}, 3000));
```

#### Throttle Implementation:

```javascript
const throttle = (func, limit) => {
  let lastFunc;
  let lastRan;

  return function () {
    const context = this;
    const args = arguments;

    if (!lastRan) {
      func.apply(context, args);
      lastRan = Date.now();
    } else {
      clearTimeout(lastFunc);

      lastFunc = setTimeout(() => {
        if (Date.now() - lastRan >= limit) {
          func.apply(context, args);
          lastRan = Date.now();
        }
      }, limit - (Date.now() - lastRan));
    }
  };
};
```

This throttle function limits the rate of function execution, ensuring that consecutive invocations within the throttle period are ignored. A practical example:

```javascript
throttleBtn.addEventListener('click', throttle(function () {
  console.log('Hey! It is', new Date().toUTCString());
}, 1000));
```

To address the edge case where the last call is within the limit period, we modify the implementation. Now, it captures and executes the last invocation correctly, making the previous `inThrottle` variable redundant.

This implementation of throttle can be conceptualized as a chaining debounce, where each invocation shortens the waiting period. Additionally, throttle offers interesting possibilities, such as storing ignored executions and running them collectively at the end.

For a more in-depth exploration of debounce and throttle, refer to [this tutorial](https://webdesign.tutsplus.com/tutorials/javascript-debounce-and-throttle--cms-36783).