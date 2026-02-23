---
tags:
  - synchronous
  - concurrency
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Synchronous programming.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
Synchronous programming refers to the traditional way of executing code where each operation blocks the execution until it completes. In simple terms, the program waits for each task to finish before moving on to the next task. Synchronous programming is sequential and predictable.

```java
console.log("Start");

// Task 1
task1();

// Task 2
task2();

console.log("End");

function task1() {
    console.log("Executing Task 1");
    // Perform some time-consuming operation
    console.log("Task 1 completed");
}

function task2() {
    console.log("Executing Task 2");
    // Perform some time-consuming operation
    console.log("Task 2 completed");
}

```