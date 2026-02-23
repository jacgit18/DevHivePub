---
tags:
  - linear
  - dataStructure
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Stacks.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---


A stack is a higher-level data structure built upon lower-level data structures like arrays and linked lists. The choice to implement a stack using an array or a linked list depends on the specific requirements and constraints of your application, and this decision extends to depth-first search (DFS), as the choice can significantly impact performance.

A stack is less efficient in some cases but more useful. It may be limited in functionality, often having just a few essential methods: "pop" and "push," following the Last In, First Out (LIFO) principle. This means that when you insert and delete elements, you're always working with the most recently inserted items. Additionally, you can use "peek" to inspect the top element of the stack and "length" to determine its size.



**Arrays:**
- Arrays can be less memory-efficient, especially when using a fixed-size array. When you exceed the array's capacity, you may need to allocate a larger array and copy elements, which can be inefficient.
- Arrays can be either static or dynamic, depending on the programming language. Dynamic arrays automatically resize to accommodate more elements. An example of this is Java where you have static arrays and dynamic ArrayList. 
- Arrays often provide faster access times due to their contiguous memory storage, but resizing can impact this advantage.
- Implementing a stack with an array is typically simpler, as it doesn't involve managing memory allocation and pointers.

**Linked Lists:**
- Linked lists offer memory efficiency advantages by dynamically allocating memory for each node, minimizing wasted memory space. Unlike arrays, where elements are stored consecutively in memory blocks, linked lists allow nodes to be dispersed in memory, with each node pointing to different memory addresses. This flexibility arises from the use of pointers, which can reference memory locations anywhere within the system.
- Linked lists can grow or shrink dynamically, making them suitable if the size of your stack varies.
- Linked lists offer faster insertions and deletions at both ends (push and pop) with constant time complexity.
- Implementing a stack with a linked list might require more complex code due to managing nodes and references.

Your choice should consider factors like memory efficiency, dynamic requirements, time complexity, implementation complexity, and the programming language you're using. Both data structures have strengths and weaknesses, and the decision should align with your application's specific needs.

**Use Case:**
Stacks are commonly used in procedural programming as a memory stack. Building stacks with arrays can offer cache locality, making them faster when accessing items in memory. Stack logic is also used in frontend development for handling states, making it suitable for browser history. Stacks can be used with both static structures and predetermined storage capacities.

**Stack & Heaps in Computer RAM:**
The stack is allocated by the operating system when a process starts and is maintained in-line by the program. This allocation method is faster, and push and pop operations are typically efficient. Variables on the stack go out of scope and are automatically deallocated, making stack allocation faster compared to the heap.

Variables on the heap must be manually destroyed and do not go out of scope. They are freed with "delete," "delete," or "free." Heap allocation is slower than stack allocation and can result in fragmentation with many allocations and deallocations. Data on the heap is typically accessed through pointers, allocated with "new" or "malloc," and can lead to allocation failures with large buffer requests.

In summary, use the stack when you know the exact data size before compile time, and it's not too large. The heap is suitable when the data size is unknown at runtime or when significant data allocation is required, but it comes with the responsibility of managing memory and potential memory leaks.







