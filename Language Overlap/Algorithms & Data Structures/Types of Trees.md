---
tags:
  - dataStructure
  - non-linear
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses trees
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[tree.gif]]
## Tree 

^2c4475

A **general tree** not built into java is a versatile tree data structure that imposes no specific constraints on its hierarchical organization. The properties of a general tree can vary depending on the specific implementation.

- General Tree Structure:
  - A node in a general tree can have any number of children, allowing for diverse hierarchical arrangements.
  - The hierarchy within a general tree follows a sequence from the root to parent nodes, children, siblings, and leaves. Sub-trees, which are like mini trees rooted at a node, are often associated with recursive processes.

- Node Terminology:
  - **Child Node**: The immediate successor of a node in a general tree is referred to as its child node.
  - **Leaf Node**: Nodes without any child nodes are called leaf nodes.
  - **Ancestor of a Node**: Predecessor nodes on the path from the root to a specific node are known as its ancestors.
  - **Descendant**: Successor nodes on the path from a leaf node to a particular node are its descendants.
  - **Sibling**: Nodes that share the same parent node are considered siblings.
  - **Neighbor of a Node**: Parent or child nodes of a specific node are referred to as its neighbors.

## Binary Tree

A **binary tree** is a specialized tree data structure with constraints that each node can have at most two child nodes, typically referred to as the left and right children.

- Significance of Binary Trees:
  - Binary trees strike a balance between the characteristics of arrays and linked lists, making them well-suited for search, sorting, and insertion operations.
  - They find applications in various domains, including compilers, expression parsing, router tables, and more.

### Types of Binary Trees

Binary trees come in different variations, each with its unique properties and applications:

- **Perfect Binary Trees**: These trees exhibit exponential growth, doubling the number of nodes with each level. The sum of nodes in all levels up to the last level equals the total nodes in the last level plus one. Perfect binary trees are highly efficient structures.

- **Balanced Trees**: In balanced trees, nodes on each side of the tree are no more than one level apart. Deviating beyond one level difference results in an unbalanced tree.

- **Full Binary Trees**: Full binary trees are unbalanced, with one side having more nodes than the other. The difference in levels between nodes exceeds one. Understanding the hierarchy of levels is essential for classifying full binary trees.

The complexity of insertion, deletion, and traversal operations on binary trees is O(logN) for balanced trees but can degrade to O(N) for unbalanced ones. This logarithmic time complexity is related to the number of levels in the tree structure.

# Binary Search Tree (BST)
![[BST.gif]]

A **binary search tree** extends the concept of a binary tree with a unique property: the binary-search-tree property. This property ensures that the values (or keys) of nodes follow a specific order.

- Binary Search Tree Properties:
  - The value of the left child node is less than or equal to the parent value, while the value of the right child is greater than or equal to the parent value.
  - BSTs are employed in simple sorting algorithms, priority queues, and search applications.

## Pros and Cons

### Pros:

- Efficient Insertion and Deletion Operations.
- Quick Access to Elements.
- Maintains Sorted Order.
- Adaptable Size.

### Cons:

- Overhead in Creation and Management.
- Unbalanced BSTs can lead to linear time complexity (O(N).
- In production, self-balancing trees like AVL or red-black trees are often preferred to ensure balance.

### Binary Search on Arrays

Binary search is a widely-used search method, often associated with sorted arrays. This concept aligns with the fact that we don't need to be concerned with the specific implementation of a binary search tree; our primary interest is in performing three essential operations: retrieving an element, obtaining a left sub-object, and accessing a right sub-object. Of course, these actions are subject to constraints, such as the elements in the left sub-object being less than the element and the elements in the right sub-object being greater.

These three operations can be seamlessly executed with a sorted array. In this context, the "element" corresponds to the middle element of the array, the left sub-object encompasses the subarray to its left, and the right sub-object encompasses the subarray to its right.

In common practice, the term "binary search" typically refers to the algorithm applied to sorted arrays, while "binary search tree" pertains to a tree-based data structure endowed with specific properties. Nevertheless, the requirements for binary search and the properties of binary search trees ultimately unify these two aspects. Being a binary search tree often implies a specific implementation, but fundamentally, it involves providing specific operations and adhering to particular constraints. Binary search is an algorithm that operates on data structures possessing the


# AVL Tree

An **AVL tree** is a self-balancing binary search tree that automatically maintains its balance, ensuring efficient performance.

- AVL Tree Properties:
  - Follows binary search tree properties.
  - Self-balancing nature.
  - Uses balance factors to manage tree balance.
  - Ideal for situations involving frequent insertions.

# Red-Black Tree

A **red-black tree** is another self-balancing binary search tree where each node is assigned a color (red or black) to ensure balanced tree structures.

- Red-Black Tree Properties:
  - Conforms to binary search tree properties.
  - Self-balancing with color-coded nodes.
  - All paths from a node to its leaf descendants maintain a consistent number of black nodes.

# Splay tree 

^4d0f96

A **splay tree** is a self-balancing binary search tree that prioritizes recently accessed elements for quick retrieval. After operations like search, insertion, or deletion, splay trees rearrange themselves to place the specific element at the root.

# Treap

A **treap**, a fusion of "tree" and "heap," is a binary search tree where each node has both a key and a priority value. The keys follow the binary search tree property, while priorities follow the heap property. Treaps are used for various applications, including authorization certificates and fast set operations.

# B-Tree

A **B-tree** is a self-balancing search tree that maintains data in sorted order. It consists of multiple nodes, each with keys, and serves as a versatile data structure for large datasets.

1. **Node Structure**: Each node contains keys, the number of keys, and information about whether it's a leaf node.
2. **Children**: Nodes can have multiple children.
3. **Bounds on Keys**: Nodes have bounds on the number of keys they can store.

B-trees are widely used for solving sorting problems and offer optimal time complexity (O(log(N)) for various operations.

This comprehensive overview highlights different tree structures, each serving specific purposes in computer science and practical applications. Trees, with their various characteristics and properties, provide a flexible foundation for organizing and managing data efficiently.