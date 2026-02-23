---
tags:
  - linear
  - dataStructure
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Type of Linked List
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
## [[Singly Linked List]]

Linked lists, specifically nodes and the traversal of the list, serve as the foundation for other node-based data structures like trees and graphs. Linked lists differ in how their pointers are used, which can be either pointing to the next node or, in some cases, pointing to both the previous and next nodes, with the possibility of these pointers being null. On the other hand, data structures like binary search trees can have nodes that point to multiple child nodes, either two child nodes or a single child node with its own set of child nodes. Graphs, in a broader sense, can establish connections to numerous other nodes, often using an array to track these relationships.
>[!important] 
>***LINKED LIST -> TREE -> GRAPH***
>The progression from linked lists to trees and then to graphs represents a natural evolution in terms of complexity and relationships in data structures:

1. **Linked List**: The simplest form, nodes are connected linearly, pointing primarily to the next node.

2. **Tree**: In a tree structure, nodes can have multiple children, and there is typically a hierarchical relationship between parent and child nodes. Binary trees are a common example with two children per node.

3. **Graph**: Graphs represent a more complex structure where nodes can have relationships with many other nodes. This is often implemented using arrays or other data structures to track these connections.

When it comes to iterating or traversing these data structures, it's often advantageous to iterate more extensively, especially in complex structures like trees and graphs, to explore all the relationships and data effectively. The choice of traversal algorithms can significantly impact the efficiency and functionality of these data structures.


## [[Doubly linked list]]

## [[Circular Linked Lists]]



4. **Skip List:**  
- Consists of multiple layers of linked lists, where each layer skips over a fixed number of elements.  
- Used for efficient searching and insertion operations.  
  
5. **Self-adjusting List:**  
- Reorders its elements based on the access pattern to improve performance.  
- Example: Move-to-front list, transpose list.  
  
6. **Unrolled Linked List:**  
- Each node contains an array of elements rather than a single element.  
- Reduces overhead by storing multiple elements in a single node.  
  
7. **XOR Linked List:**  
- Each node stores the XOR combination of addresses of its previous and next nodes.  
- Requires bitwise XOR operation for traversal.  
  
8. **Multi-level Linked List:**  
- Contains multiple levels of linked lists, often used in hierarchical data structures.  
  
9. **Hashed Linked List:**  
- Combines linked lists with hash table concepts for efficient data retrieval.  
  
These are just a few examples, and there may be variations or combinations based on specific requirements in different contexts.




## Linked List Techniques


When working with Linked List In some scenarios, you can create and use dummy nodes in a linked list. Dummy nodes are typically structured like this:

```JavaScript
let previousNode = new ListNode(25);
let dummyNode = previousNode;
```

The purpose of the dummy node is to provide a stable reference point, especially when inserting or deleting nodes. As you update the `previousNode`, the dummy node remains intact. For example, if you want to create a linked list like `25 -> 10 -> null`, you can do so by continuing to add values after the initial `25`, while `dummyNode` remains the reference to the head of the list:

```plaintext
Initially: 25 -> null
After adding 10: 25 -> 10 -> null
```

If you don't need to use a dummy node, you can directly store nodes as `prevNode` and `currentNode`, allowing you to have multiple references and swap or reassign them as needed. This approach can be particularly useful when iterating through a linked list.

Here's a common iteration pattern through one or more nodes in a linked list:

```JavaScript
let prevNode = head;  // Initialize prevNode with the head of the linked list
let currentNode = head.next;  // Initialize currentNode with the node after the head

while (currentNode !== null) {
    // Perform some action on the current node or data
    // ...

    // Move to the next node
    prevNode = currentNode;
    currentNode = currentNode.next;
}

// If you need to create a new node and insert it, you can do so by updating prevNode.next:
let newNode = new ListNode(newValue);
prevNode.next = newNode;
```

This allows you to traverse the linked list and manipulate the nodes efficiently. Just make sure to update the `prevNode` and `currentNode` references as you iterate through the list.


