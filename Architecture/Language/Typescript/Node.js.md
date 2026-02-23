---
tags:
  - javascript
  - eventDriven
  - WebDevelopment
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what is Node.js and its inner working.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Understanding Node.js: A Comprehensive Overview

Node.js is a versatile, open-source, cross-platform JavaScript runtime environment designed for executing JavaScript code outside the browser, enabling the development of applications across various platforms. It is built upon the V8 engine, an open-source high-performance JavaScript and WebAssembly engine developed by Google for Google Chrome and other internet browsers.

#### V8 Engine Basics:

The V8 engine, at the heart of Node.js, comprises two integral components:

1. **Memory Heap:** The area where memory allocation occurs, storing objects and variables.

2. **Call Stack:** The mechanism that manages the execution of function calls, ensuring they occur in the correct order.

#### Single-Threaded, Non-Blocking Asynchronous Execution:

Node.js operates as a single-threaded, non-blocking, and asynchronous execution framework. It is specifically tailored for non-blocking, event-driven servers, making it ideal for real-time, push-based architectures. This design allows Node.js to efficiently handle concurrent requests without the need for an extensive thread pool.

#### Node.js Architecture:

- **Global Utilities:** Node.js provides global utilities, including consoles, timers, processes, buffers, and more.

- **Underscore Library:** A widely-used JavaScript library available on NPM, Underscore (npm install underscore) offers extensive functional programming support, aligning with conventions from other languages like Ruby and Python.

- **Streams for Data Handling:** Node.js excels in handling streaming data, enhancing user experience and reducing server resource utilization.

#### Event Handling with EventEmitter:

Node.js includes a built-in events module that simplifies event handling. The central class, `EventEmitter`, facilitates the emission and subscription to events.

```javascript
const EventEmitter = require('events');
```

- **EventEmitter Class:** Designed for easy event emission and subscription, the EventEmitter class forms the foundation of Node.js event handling.

#### Event-Driven Programming

Events provide a broadcast-like mechanism, allowing components to raise occurrences without knowing about their clients. This decoupling makes events ideal for scenarios where clients determine the significance of occurrences. Multiple client registrations are streamlined through events, providing flexibility and simplicity.

#### Conclusion:

Node.js, with its unique architecture and event-driven approach, empowers developers to create scalable and efficient applications. Learning and expanding knowledge on NPM, Express.js (a popular framework for building web applications and APIs), and mastering the EventEmitter class contribute to harnessing the full potential of Node.js in diverse application development scenarios.
## Event Loop 

The Event Loop is one of the most important aspects to understand about Node.js. Why is this so important? Because it explains how Node.js can be asynchronous and have non-blocking I/O, it explains the "killer feature" of Node.js, which made it this successful.


## Inside the engine of Javascript

![[Javascript Engine.jpeg]]

When you write a program, a syntax parser reads your code and then the compiler translates it into computer instructions(a lower-level language). 

Where you write your code and what surrounds it is crucial! The area of the code you are looking at physically is the lexical environment. 

It sounds funny, but not every programming language is like that. In JS, however, the compiler that converts your code cares about where you put things. And based on it, decide where your code will sit in the memory and interact. 

So there are multiple lexical environments, but one that is being executed is handled by the execution context — a context in which javascript code is running.