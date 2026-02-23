---
tags:
  - dataStructure
  - timeComplexity
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Linear Data Structure and there runtime for there action.
Status: Done
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[RuntimeProcess.gif]]

I view data structures as diverse arrangements of key-value objects, each structured with unique advantages and drawbacks. Then you have algorithms were  you create a class with specialized functions to manipulate the structure. This class then acts as a wrapper, encapsulating both the data structure and its associated functionality. This conceptual approach embraces the principles of object-oriented programming, although the implementation specifics may vary depending on the particular data structure and programming language employed.


## **Data Structure Operations Worst and Average Time Complexity**

Operations on data structures can have varying worst-case and average-case time complexities, depending on the specific data structure and the operation being performed. Below is an overview of the worst-case and average-case time complexities for different data structure operations, with a focus on common data structures like arrays, linked lists, hash tables, and more:

### Insertion (CREATE/UPDATE) -
>[!note]
> In terms of create and update when doing insertion you are adding a new element that didn't exist before also insertion can be viewed as an update operation, particularly if you're adding or replacing an element in a data structure that already exists. For instance, if you're inserting a value into a specific position in an array, you are updating the array at that index. The distinction between creating and updating during insertion often depends on whether the element being inserted is entirely new or if it's modifying an existing structure. 

- Array: Worst: O(n), Average: O(n) for push()
- Stack: Worst: O(n), Average: O(1) for push()
- Queue: Worst: O(n), Average: O(1) for enqueue and queue.shift()
- Singly-Linked List: Worst: O(n), Average: O(1) for reassigning a pointer ^a8bac8
- Doubly-Linked List: Worst: O(n), Average: O(1) for reassigning a pointer


### Access / Lookup (READ)

Accessing elements in data structures can have different worst-case and average-case time complexities based on their implementation:

- Array: Worst: O(n), Average: O(1) for `arr[3]`
- Stack: Worst: O(n), Average: O(1) for accessing elements like `arr[LastIndex] `or `arr[FirstIndex]`
- Queue: Worst: O(n), Average: O(1) for accessing elements like `arr[FirstIndex]` and `arr[LastIndex]`
- Singly-Linked List: Worst: O(n), Average: O(n) for accessing elements like head.next.next.next.value
- Doubly-Linked List: Worst: O(n), Average: O(n) for accessing elements like head.prev


### Searching 
>[!note] 
>Searching and [[Iterating vs Traversing#^5bf9d2 | Traversing]] are common operations when working with data structures but have a slight distinction that searching involves looking for a specific element vs traversing is more broad visiting and inspecting all elements in a structure or proceess them. 

- Array: Worst: O(n), Average: O(n)
- Stack: Worst: O(n), Average: O(n)
- Queue: Worst: O(n), Average: O(n)
- Singly-Linked List: Worst: O(n), Average: O(n)
- Doubly-Linked List: Worst: O(n), Average: O(n)

Binary search can be more efficient with sorted values, typically Worst: O(log n) with an iterative implementation, Average: O(log n), or Average: O(1) with a recursive implementation.

### Deletion (DELETE/UPDATE)
>[!note]
>- When you delete an element from a data structure like an array or a linked list, it can involve updating the data structure to remove the element.
>- Deletion may also require reassigning pointers, changing the structure of a linked list, or shifting elements in an array to fill the gap left by the deleted item.
>- In some cases, deletion can indeed be considered an "updating" operation because it changes the state of the data structure.

- Array: Worst: O(n), Average: O(1) for pop()
- Stack: Worst: O(n), Average: O(1) for pop()
- Queue: Worst: O(n), Average: O(1) for dequeue(), which is similar to pop()
- Singly-Linked List: Worst: O(1), Average: O(1) for reassigning pointers to null or other nodes
- Doubly-Linked List: Worst: O(1), Average: O(1) for reassigning pointers to null or other nodes, either before or after


### Runtime Complexity of Search vs. Access

When it comes to runtime complexity, searching a data structure may involve more effort than direct access. Accessing a specific element directly (e.g., through pointers) is typically Worst: O(1), Average: O(1), as it doesn't require searching through the data structure. In contrast, searching often involves iterative or recursive algorithms and may vary in complexity based on the data structure.











