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
![[binHeap.gif]]

The heap data structure is an array object that we can view as a nearly complete binary tree. Each node of the tree corresponds to an element of the array. The tree is completely filled on all levels except possibly the lowest level, which is filled from the left up to a point.  

1. **Binary Heaps**:
   - Binary heaps are a type of heap data structure that is implemented as a binary tree with specific rules.
   - They can be categorized as either min-heaps or max-heaps.
   -  Each node in a binary heap can have at most two children, and the sibling order doesn't matter.
   - Elements are added to a binary heap in a compact and orderly manner.
   - Binary heaps are often implemented using arrays to optimize storage.

2. **Insertion in a Max Heap**:
   - When inserting into a Max Binary Heap, a method called "bubbling up" is used.
   - The insertion method involves two helper functions: `swap` and `bubbleUp`.
   - The `swap` function swaps elements in the values array at two specified indices.
   - The `bubbleUp` function compares the newly added element with its parent and swaps if the child is greater.
   - This process continues until the element fits or reaches the root of the heap.

>[!note] In the `insert` method, the key line that distinguishes between Min and Max Heap is the comparison between the parent node and the current node's value. For Min Heap, it's `this.heap[Math.floor(current / 2)] > this.heap[current]`, and for Max Heap, it's `this.heap[Math.floor(current / 2)] < this.heap[current]`.

3. **Removal in a Max Heap**:
   - Removal in a Max Binary Heap also involves bubbling.
   - The largest element (the root) is removed by swapping it with the last element in the array.
   - After removal, the heap is sorted using the `bubbleDown` method.
   - The `bubbleDown` method checks the children nodes against the new root (the last element).
   - It swaps the parent with the larger child if the parent is lesser than one of the children.
   - The process continues until the heap property is restored.

4. **Min Heap**:
   - The same principles of insertion and removal can be applied to create a Min Binary Heap.
   - The logic for insertion and removal is the same, except that comparisons and swapping are done differently to maintain the Min Heap property.


5. **Use Cases**:
   - Binary heaps are useful when you need quick access to the highest or lowest priority element.
   - They are commonly used to implement priority queues.
   - Binary heaps are employed in various algorithms and data structures.

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>(); 

// Max Heap: --> to keep the max element always on top, the same order as above. 

PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Comparator.reverseOrder()); 

// Which is the same as (Integer o1, Integer o2) -> Integer.compare(o2, o1) or - Integer.compare(o1, o2) as suggested from other answers. 
```


6. **Applications**:
   - Heap Sort: Heap Sort is an efficient sorting algorithm that uses binary heaps, with a time complexity of O(n log n).
   - Priority Queue: Binary heaps support priority queue operations efficiently, including insert, delete, extract max/min, and decrease key.
   - Graph Algorithms: Binary heaps play a crucial role in graph algorithms like Dijkstra's Shortest Path and Prim's Minimum Spanning Tree.



