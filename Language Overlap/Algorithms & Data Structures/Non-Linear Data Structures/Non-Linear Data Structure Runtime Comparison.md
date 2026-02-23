---
tags:
  - timeComplexity
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
![[nonLinearRuntime.png]]

### Set 
**Insertion (CREATE/UPDATE) :
- Set: Worst: O(n), Average: O(1) for `add()` ^0b928b


**Access(Read):**
- Set: doesn't have a specific access action because the way it is structured. 


**Search:**
- Set: Worst: O(n), Average: O(1) for `has()` or iterating through objects. ^03b8d8


**Delete(Delete/Update):**
- Set: Worst: O(n), Average: O(1) for delete() ^a73e52

### HashMap & HashTable
**Insertion (CREATE/UPDATE) :
- Hash-table: Worst: O(n), Average: O(1) for add()
- HashMap: Worst: O(n), Average: O(1) for set() ^22edde

**Access(Read):**
- Hash-table: Access may not be straightforward.
- HashMap: Worst: O(n), Average: O(1) for `myObject.keyName` alternatively you can use `myObject[keyName]`

**Search:**
- Hash-table: Worst: O(n), Average: O(1) for iterating through objects
- HashMap: Worst: O(n), Average: O(1) for `get()` or `has()` methods which searches through object main difference is `get()`returns value vs `has()` return boolean ^0b11f5

**Delete(Delete/Update):**
- Hash-table: Worst: O(n), Average: O(1) for `remove()`
- HashMap: Worst: O(n), Average: O(1) for `delete()` ^2057fe

# Binary Search Tree
Binary Search Trees are data structures that maintain their elements in a way that allows for efficient searching and manipulation.

**Insert(Create/Update):** 
  - **Worst-Case:** O(n)
  - **Average:** O(log(n))
  - **Explanation:** The time complexity for insertion in a BST can be O(n) in the worst case when the tree becomes unbalanced, but on average, it is O(log(n)) when the tree remains balanced. Insertion involves checking whether the new element is less than or greater than the current node and appropriately updating the tree.

**Access(Read):**
  - **Worst-Case:** O(n)
  - **Average:** O(log(n))
  - **Explanation:** Accessing a specific element in a BST, such as `root.left.right.left.value`, has a time complexity of O(n) in the worst case, but it is O(log(n)) on average in a balanced tree.

**Search:**
  - **Worst-Case:** O(n)
  - **Average:** O(log(n))
  - **Explanation:** Searching in a BST can be O(n) in the worst case when the tree is unbalanced. However, on average, when the tree is balanced, it is O(log(n) due to the binary search property.

**Delete(Delete/Update):**
  - **Worst-Case:** O(n)
  - **Average:** O(log(n))
  - **Explanation:** Deletion in a BST can be O(n) in the worst case when the tree is unbalanced, but it is O(log(n)) on average when the tree remains balanced. Deletion involves reassigning nodes or deleting leaf nodes and reassigning to null.


# Graph
## 1. Storage:
   - **Category:** Access
   - **Worst-Case Runtime Complexity:** This operation is not typically categorized with traditional runtime complexities, as it's related to the memory required to store the graph's structure. In the case of an [[Graph List & Matrix Type#^897f42| adjacency matrix]], it's `O(|V|^2)`, and for an [[Graph List & Matrix Type | adjacency list]], it's `O(|V| + |E|)`.
   - **Average Runtime Complexity:** N/A (as it's memory-related)
   - Access action for graphs example: 
	   `node.id` 
	   `node.edge[1]`
	   `node.edge[2].id`
	   `node.edge` 
## 2. Add Vertex:
   - **Category:** Insertion
   - **Worst-Case Runtime Complexity:** `O(1)`
   - **Average Runtime Complexity:** `O(1)`
   - **Explanation:** Adding a vertex to the graph is typically a constant-time operation, regardless of the representation.

## 3. Add Edge:
   - **Category:** Insertion
   - **Worst-Case Runtime Complexity:** `O(1)`
   - **Average Runtime Complexity:** `O(1)`
   - **Explanation:** Adding an edge between two vertices is typically a constant-time operation in both adjacency matrix and adjacency list representations.

## 4. Remove Vertex:
   - **Category:** Deletion
   - **Worst-Case Runtime Complexity:** The exact complexity can vary depending on the implementation, but it is often `O(V + E)` for adjacency list representations, as you need to remove the vertex and update associated edges.
   - **Average Runtime Complexity:** N/A (as it depends on the specific implementation)

## 5. Remove Edge:
   - **Category:** Deletion
   - **Worst-Case Runtime Complexity:** `O(V)` in the worst case for adjacency list representations, as you may need to traverse the adjacency list to find and remove the edge.
   - **Average Runtime Complexity:** `O(V)` in the average case for adjacency list representations.
   
## 6. Query :
> ***e.g., checking if there is an edge between two vertices

   - **Category:** Search
   - **Worst-Case Runtime Complexity:** `O(1)`
   - **Average Runtime Complexity:** `O(1)`
   - **Explanation:** Querying the existence of an edge between two vertices is typically a constant-time operation in both adjacency matrix and adjacency list representations, as you can directly check the corresponding entry or list element.



# Max/Min Heap: Not Considered an Abstract Data Type

Max and Min Heaps are specific types of binary trees that are often used as data structures for implementing Priority Queues. They have characteristics that make them suitable for efficient priority-based operations.

#### Priority Queues:

Priority queues are implemented with heaps, particularly binary heaps, which are complete binary trees where each parent node has a value greater (in the case of Max Heaps) or smaller (in the case of Min Heaps) than its child nodes.

#### Operations and Time Complexities:

- **Insert(Create/Update)/Add:** O(log(n))
  - Explanation: Insertion or addition of an element to a heap takes logarithmic time because it involves maintaining the heap's properties.

- **Delete(Delete/Update)/Remove:** O(log(n))
  - Explanation: Deletion or removal of an element from a heap typically requires O(log(n)) time. In some cases, like deleting the root, it can be more efficient.

- **Access(Read)/Peek:** O(1)
  - Explanation: Accessing the minimum or maximum value in a heap is a constant-time operation as it can be directly obtained from the root.

- **Search:** O(n)
  - Explanation: Searching in a heap is not efficient, as heaps do not guarantee any specific order. You may need to traverse all elements to find a specific value.

#### Other Heap Varieties:

- **Decrease Key:** O(log(n))
  - Explanation: Decreasing the key of an element in a heap takes logarithmic time and is often used in algorithms like Dijkstra's shortest path algorithm.

- **Union:** O(n)
  - Explanation: The union operation on heaps typically takes linear time. You can look into more efficient heap data structures like binomial heaps for improved union operations.

#### Specialized Heap Data Structures:

- **Binomial Heap:** O(log(n)) for each action
  - Explanation: Binomial heaps are specialized heap data structures that offer efficient time complexities for various operations.

- **Fibonacci Heap:** O(1) for each action
  - Explanation: Fibonacci heaps are another specialized heap data structure that offers constant-time amortized complexities for many actions. However, they have a higher constant factor.

- **Searching for Extreme Values:** O(n)
  - Explanation: If you need to search for an extreme value (e.g., the maximum value in a Min Heap or the minimum value in a Max Heap), it would require O(n) time because you may need to search through all elements.

In summary, Max and Min Heaps, along with Priority Queues implemented using these heaps, offer efficient time complexities for various operations, especially when you need to quickly access extreme values. However, searching within a heap is not efficient due to the lack of specific order. You can explore specialized heap data structures like binomial heaps and Fibonacci heaps for further optimizations in specific scenarios.


