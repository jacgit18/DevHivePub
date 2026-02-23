---
tags:
  - linear
  - dataStructure
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Queues.
Status: Refinement
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Standard queue.gif]]


Queues are similar to stacks but follow a "first in, first out" (FIFO) order, much like a checkout line. Dynamic queues can grow in size and are particularly useful for background processes and task scheduling. They find extensive use in applications such as cron jobs, memory management, and various background activities.

In some cases, a central queue is employed with multiple points of access, allowing different parts of a system to interact with it.

```java
Queue<Integer> queue = new Queue<Integer>();  
```

```typescript
Let queue = new Array<Integer>(); 
```

Enqueuing, the process of adding an item to the end, and dequeuing, the process of removing an item from the front, are the fundamental operations in queues.

Queues are essential in algorithms like Breadth-First Search (BFS), which is used to traverse or search trees and graphs.

Queues are linear data structures, and they can be accessed sequentially.

Advantages of both stacks and queues include their efficiency in adding and removing items. They are particularly suitable for specific use cases, although they may have limited applicability compared to other data structures.

Queues are commonly used in scenarios like managing printers, where tasks are processed in the order they are submitted.

In terms of time complexity, traversal (going through all elements), enqueue, dequeue, and peek operations are O(n), where 'n' is the number of elements in the queue. Enqueue is analogous to "push," and dequeue is similar to "pop," but it removes the first item, following the FIFO principle.

When implementing queues, it is generally more efficient to use linked lists, as insertion and removal are O(1), indicating constant time complexity. Linked lists are well-suited for queue implementation. Using arrays for queues can be less efficient because dequeuing requires shifting array indices, resulting in O(n) time complexity, where 'n' is the number of elements in the array.

Additionally, [[Priority Queue Implementation |priority queues ]]are introduced, which function like queues but prioritize items based on their importance. They are often implemented using a [[Binary Heap]]  data structure.

Storing a binary heap as an array is advantageous due to lower memory usage, simpler memory management, and better locality of reference compared to a linked list implementation.


![[Queues.gif]]