---
tags:
  - memory
  - javascript
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses memory management in javascript with Stacks, Heaps, and Event Loop.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Call Stack.gif]]

**Stacks and Heaps:**

In JavaScript, a stack handles primitive values like numbers, strings, booleans, nulls, undefined, and symbols. It operates swiftly but has limited space. On the other hand, a heap, while slower, accommodates all object types—object literals, arrays, functions, dates, and others—and provides ample space.

When creating a primitive type like a string, its value is stored in a stack. For objects, a pointer is created, leading to the stack with the reference of the object variable name.

If you have two variables with the same primitive type, they are distinct values in the stack. However, with objects, they share the same pointer on the heap. Therefore, updating the first variable affects the second, as they reference the same object.

**Call Stack:**

The call stack, maintained in memory for each task and thread, is a stack of function calls executed in order. Each function call forms a frame on the stack, containing function arguments and local variables. The stack operates on a last-in, first-out basis. JavaScript, being single-threaded, has one call stack, making it non-blocking but single-threaded.

**Heap:**

Objects in JavaScript reside in the heap—a large, unstructured memory region. Every created object needs space in the heap. If transitioning from C++, the heap is analogous to where things go when constructed using `new` in C++.

**Web APIs and Events:**

Web APIs, low-level functions in the JavaScript runtime, interact with the OS and are implemented by the browser/host. They include functions like `setTimeout()`. Web APIs, when called, generate messages that are sent to the callback queue, enabling asynchronous behavior. Callbacks, attached to these messages, are processed by the Event Loop.

**Callback Queue:**

The callback queue contains tasks that have finished processing, with callback functions for each message. The Event Loop facilitates the transfer of callbacks from the queue to the call stack once it is empty.

**Event Loop:**

The Event Loop continuously checks if the call stack is empty. When empty, it retrieves the first element from the callback queue and transfers the callback to the call stack. The Run-to-Completion principle ensures that a message runs to completion before new messages are added to the call stack, maintaining order in execution.
  
  
 
