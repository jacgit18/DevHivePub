---
tags:
  - web
  - API
  - concurrency
  - multiThreading
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Web Workers which relates to multi threading but in the Javascript ecosystem.
Status: Done
Started: 2023-11-23
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish: true
---
You can leverage the `Worker` API to execute functions concurrently in pure JavaScript, eliminating the need for HTML. Here's an illustrative example: 

```javascript

// Function 1
function function1() {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log('Function 1 completed');
      resolve();
    }, 1000); // Simulating a time-consuming task
  });
}

// Function 2
function function2() {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log('Function 2 completed');
      resolve();
    }, 2000); // Simulating a longer time-consuming task
  });
}

// Create a Worker for function1
const worker1 = new Worker(URL.createObjectURL(new Blob([`(${function1.toString()})()`]));

// Create a Worker for function2
const worker2 = new Worker(URL.createObjectURL(new Blob([`(${function2.toString()})()`]));

const start = performance.now();

// Listen for messages from worker1

worker1.onmessage = () => {
  console.log('Worker 1 completed');
  worker1.terminate();
};

// Listen for messages from worker2
worker2.onmessage = () => {
  console.log('Worker 2 completed');
  worker2.terminate();

  const end = performance.now();
  const elapsedTime = end - start;
  console.log(`Both workers completed in ${elapsedTime} milliseconds`);
};

worker1.postMessage('start');
worker2.postMessage('start');
```

In this example, we define `function1` and `function2`, then create two distinct workers to execute them concurrently. Communication between workers and the main script occurs via `postMessage`. The main script measures the elapsed time once both workers finish their tasks to assess their speed.