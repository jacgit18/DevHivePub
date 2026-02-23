---
tags:
  - CPU
  - processes
author:
  - jacgit18
  - chatgpt
Status: Refinement
Purpose: This documentation discusses how cpu works with processes.
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Cores vs Threads.jpg]]
## Prompt


## Threads
**Hyper-threading** is a process by which a CPU **divides up its physical cores into virtual cores** that are treated as if they are actually physical cores by the operating system. These virtual cores are also called *threads* which is a unit of execution used to manage concurrency in programming. Most CPU's with 2 cores use this process to create 4 threads/virtual cores. Cores increase the amount of work accomplished at a time by doing things like [[Content switching]]. Whereas threads improve throughput, and computational speed up using multiple CPU's for operating numerous processes or sequences of processes. Threads can have multiple independent execution streams along with shared state. Besides that it can use preemptive scheduling and synchronization(lock condition).
![[Hyper Threading.png]]

## Multi-Threading
***Multi-threading*** is a technique that takes a process and breaks it down into multiple task and executing those sub task of that initial process at the same time and also having the ability to execute individually while sharing their resources. it is also considered a type of [[Synchronous vs Asynchronous vs Multiprocessing| asynchronous programming ]] .

Multithreading is used a lot in game development but not as much in business app development

>Process = Multiple applications running simultaneously in the server, PC or Mac
>Thread =Multiple tasks running within a process

## Daemon thread
A daemon is a type of useful support thread that performs unique tasks like running continuously as a background process and wakes up to handle periodic service requests, which often come from remote processes. 

## Multiprocessing 
Multiprocessing - the idea of, instead of spinning up threads in a single process that shares the same resources of the process. we create individual unique processes with there on memory structure and you just communicate between these process using inter process communication or centralized Redis database, there are many ways to communicate between processes. 

Multiprocessing is good for scaling up to be used on multiple machines and can used to brute force through a password with a hash 



### Parallel processing vs Concurrent processing
![[Parallel vs Concurrent.jpg]]
- Concurrency(Multi-threading) is the task of running and managing multiple computations at the same time. core to thread operates by switching.  
- In Java, concurrency is the ability to run several programs or parts of a program in parallel. A time-consuming task can be performed asynchronously or in parallel improving the program's throughput and interactivity. A modern computer has several CPU's or several cores within one CPU.
- [[Parallelism]] is the task of running multiple computations simultaneously. core to core all operate at the same time. ^2862c2

[[Concurrent programming]]

![[concuurentPAra.gif]]

![[1718947920180.gif]]


#todo/Med/Dev 
- [ ] shorten answers

## Flashcard
#cpuProcesses
What is a daemon thread;; A daemon thread is a low-priority thread used for unique task.

Why use multithreading in your applications;; concurrent execution of multiple threads.



Can you explain what the thread scheduler is and its relationship to thread priority;; The thread scheduler is what allocates CPU time to threads and determines the order in which threads execute.


Why might you describe thread behavior as unpredictable;; Because thread scheduling is determined by the CPU, different CPUs may give priority to different threads. This means there's a chance two CPUs might not run your threads in the same order, creating unpredictability in your code execution.


What's time slicing;; Time slicing is the process used by the thread scheduler to divide CPU time between the available active threads.


What's thread starvation;; Thread starvation is when there's insufficient CPU capacity to execute a thread. This can happen with low-priority threads or threads that programmers demote in favor of other threads.


Explain the busy spin technique and why you might use it;; Busy spin is when you pause a thread by making it run an empty loop for a certain period. Unlike other methods like wait() or sleep(), a busy spin doesn't give up CPU control and therefore preserves CPU cache.


Can you start a thread twice;; Once you execute a thread, it's dead and you can't restart it


Can you describe a deadlock situation;; A deadlock situation occurs when multiple threads are waiting on one another to release CPU resources so they can run. For example, this can happen when a single thread has exclusive priority but needs resources from a waiting thread, or all the threads are depending on one another to release needed resources.


What happens when a livelock occurs;; A livelock is similar to a deadlock situation, except in a livelock, the state of the threads change without ever making progress. For instance, if all the threads are in infinite loops.



