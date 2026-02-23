---
tags:
  - synchronous
  - multiThreading
  - concurrency
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the difference between Synchronous, Asynchronous, and Multiprocessing.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: "[[Asynchronous Programming]]"
Peer Reviewed: 0
dg-publish:
---




Asynchronous - the relationship between two or more events/objects that do interact within the same system but do not occur at predetermined intervals and do not necessarily rely on each other's existence to function. 

Asynchronous makes a request and leaves a callback function to handle the result and trigger some type of event that can be handled 

In web development, it's commonly associated with actions requiring waiting for responses from other machines. Concurrency plays a significant role, though Node operates as a single thread, leveraging Express.js to manage multiple requests in the background. While browsers exhibit some concurrency, control is limited unless employing tools like web workers. The dynamics shift when designing scripts, data processing, or low-level code, where concurrency becomes a fundamental approach.


What's the difference between synchronous and asynchronous programming?

Asynchronous and synchronous programming are two common methods that execute tasks differently. Multithreading is a type of asynchronous programming, and an interviewer might ask this question to gauge your understanding of basic coding ideas. When you answer, you can simply explain the primary difference between these two methods, which is how they run tasks.

Example: "Synchronous programming runs tasks individually from a queue. Asynchronous programming allows multiple tasks to run at once on the same thread."



async/await is syntactic sugar it looks Synchronous but is Asynchronous 




![[aysnc func generating task.png]]


https://www.youtube.com/watch?v=0vFgKr5bjWI 

[https://web.stanford.edu/~ouster/cgi-bin/papers/threads.pdf](https://web.stanford.edu/~ouster/cgi-bin/papers/threads.pdf)





