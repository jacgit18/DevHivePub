---
tags:
  - error
  - errorHandling
  - CapitalOne
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses type of errors.
Status: Done
Started: 
EditDate: 2024-11-11
Relates: "[[Exception Handling]]"
Peer Reviewed: 0
dg-publish: false
---
## Syntax Error 
Typically associated when you forget a bracket or put the wrong sign 

So you end up needing to add or remove a bracket or replace a comma 

## Reference Error 
Usually occurs if you misspell something or your variable might not exist in the  current scope 

## [Type Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError) 
confusing one thing for another like calling a variable instead of a function 

## Logic error 
The worst error is just a core logical issue which takes time to understand and fix

## Timing Errors

Timing-related errors can appear on both the front end and back end, but they manifest in different ways due to how each handles tasks:

### 1. Front End:

Timing issues often show up due to asynchronous operations, especially with user interface elements and network requests. For example, a component might render before data is fully fetched, or animations may not sync well with user interactions.

These errors are more common in front-end testing when dealing with race conditions, especially with JavaScript’s asynchronous nature. Tests for front-end applications need to account for the timing of events, such as waiting for specific DOM elements or API responses to load fully.

### 2. Back End:

In the back end, timing-related errors usually occur due to concurrency and load management. For instance, multiple requests trying to access the same resource or incomplete handling of asynchronous tasks can cause issues.

Back-end timing issues are often seen with database transactions, API rate limiting, and multi-threaded environments. This can cause problems like deadlocks or delays in response times, especially under high loads.

---

### Testing Approach:

- **Front-end testing** often requires careful use of waits or retries to ensure components render in a predictable state before assertions.
  
- **Back-end testing** might involve stress testing, load testing, and concurrency checks to catch timing issues under various conditions.

---

In general, front-end timing issues can be more visible and directly affect the user experience, but back-end timing issues can have a more systemic impact, especially under heavy traffic or complex operations.