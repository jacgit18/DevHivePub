---
tags:
  - dataStructure
  - non-linear
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[fib.png]]

Much like the Binomial Heap, a Fibonacci Heap is a collection of trees, each adhering to either the Min-Heap or Max-Heap property. However, in the case of a Fibonacci Heap, the trees are far more flexible in their structure. They can take on various shapes, and it's even possible for all trees to consist of just single nodes. This stands in contrast to the Binomial Heap, where every tree must conform to the rigid structure of a Binomial Tree.

One of the distinctive features of a Fibonacci Heap is its efficient means of tracking the minimum value within the heap. This is accomplished by maintaining a pointer to the minimum value, which corresponds to the root of one of the trees in the heap. These tree roots are interconnected using a circular doubly linked list, making it possible to access all of them through a single 'min' pointer. This circular structure enhances the efficiency of operations in Fibonacci Heaps.