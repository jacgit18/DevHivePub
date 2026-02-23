---
tags:
  - bfs
  - dfs
  - AlgorithmExamination
  - looping
  - search
  - traversal
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses DFS & BFS
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[TreeTraversal.gif]]

**The essence of DFS and BFS lies in the order of operations and base cases, depending on the specific problem.**

**DFS (Depth-First Search):**

DFS is an algorithm designed for traversing or searching tree data structures. It begins at the root node and explores as deeply as possible along each branch before backtracking. In simpler terms, DFS explores a path all the way to a leaf before considering another path.

**BFS (Breadth-First Search):**

BFS, on the other hand, is another algorithm for traversing or searching tree data structures. It starts at the root node and initially explores the neighbor nodes before moving to the next level neighbors. This approach ensures that BFS traverses the tree level by level and depth by depth.

It's important to note that the choice between DFS and BFS depends on the problem at hand. BFS is ideal when searching for something closer to the root, while DFS is more suitable when the target node is closer to a leaf.

The choice of data structures for these algorithms is crucial:

- BFS traditionally employs a queue, as it processes nodes in a first-in-first-out manner.
- DFS can be implemented with a stack, and whether you choose a linked list or an array depends on your specific requirements. Arrays are faster but less dynamic.

#### Here's a quick reference to the data structures for each algorithm:

**For BFS (Queue ***implemented with Linked List***):**
- Use `enqueue()` to add elements to the end of the queue implemented by linked list vs if implemented by array you would  `push()`.  
- Use `dequeue()` to remove elements from the front of the queue. You can build these functions as needed for a linked list-based queue vs the array implementation uses `pop()`


**For DFS (Stack with array is simpler):**
> *If you use linked list implemented stack it,s good to use if you anticipate a lot of adding and removing of elements
- Use `pop()` (removes the last element) - Standard for stacks.
- Use `push()` - Typical for stacks.


## **Breadth-First Search with Queue (Applicable to Trees and Graphs) - O(|V|)**

### Tree

1. Store the `[tree]` in a queue with an initial length of 1.
2. Initialize a `currentNode` variable.
3. Create an empty `result` array to store the results.
4. Iterate while the queue length is greater than 0.
5. Assign `currentNode` by shifting from the queue, which removes the root node from the queue.
6. Check the left and right children of the current node and add their references to the queue.
7. Push 12 to the result array.
8. Repeat the process by shifting out the left child, which leaves only the right child in the queue. Focus on the current node, which contains the left child. Add its children to the queue and repeat until the queue is empty.

```javascript
function breadthFirstSearch(root) {
  if (!root) return [];

  const result = [];
  const queue = [root];

  while (queue.length) {
    const node = queue.shift();
    result.push(node.value);

    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);
  }

  return result;
}
```


```javascript
function breadthFirstSearchRecursive(root) {
  if (!root) return [];

  const result = [];
  const queue = [root];

  function traverse() {
    if (queue.length === 0) {
      return;
    }

    const node = queue.shift();
    result.push(node.value);

    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);

    traverse();
  }

  traverse();

  return result;
}
```



### Graph

1. Create and store the graph in a queue.
2. Initialize a `current` variable.
3. Create and store the added graph nodes in a new set.
4. Loop through the queue while its length is greater than 0.
5. Update `current` by dequeuing (using `queue.shift()`) the first element from the queue.
6. Loop through the edges of the graph, checking if they have been visited with the set.
7. Push and add the edge into the queue and set.
8. Perform any desired action with `current.id`, such as pushing it to an array.


```javascript
function breadthFirstSearch(startVertex, graph) {
  const visited = new Set();
  const queue = [startVertex];
  const result = [];

  visited.add(startVertex);

  while (queue.length > 0) {
    const currentVertex = queue.shift();
    result.push(currentVertex);

    for (const neighbor of graph[currentVertex]) {
      if (!visited.has(neighbor)) {
        visited.add(neighbor);
        queue.push(neighbor);
      }
    }
  }

  return result;
}

// Example usage:
const graph = {
  A: ['B', 'C'],
  B: ['A', 'D'],
  C: ['A', 'E'],
  D: ['B', 'E'],
  E: ['C', 'D'],
};

const bfsResult = breadthFirstSearch('A', graph);
console.log(bfsResult); // Output: ['A', 'B', 'C', 'D', 'E']
```


```javascript
function recursiveBFS(startVertex, graph) {
  const visited = new Set();
  const queue = [startVertex];

  function visitNeighbors(node) {
    if (node === null || visited.has(node)) {
      return;
    }
    visited.add(node);
    console.log(node); // Process the current node

    for (const neighbor of graph[node]) {
      if (!visited.has(neighbor)) {
        queue.push(neighbor);
      }
    }
    if (queue.length > 0) {
      visitNeighbors(queue.shift());
    }
  }

  visitNeighbors(startVertex);
}

// Example usage:
const graph = {
  A: ['B', 'C'],
  B: ['A', 'D'],
  C: ['A', 'E'],
  D: ['B', 'E'],
  E: ['C', 'D'],
};

console.log("BFS Traversal:");
recursiveBFS('A', graph);
```



## **Depth-First Search with Stack (Applicable to Trees and Graphs) - O(|V|)**

>[!important]
> For DFS, it's not about the queue that can be Implemented with Array or Linked List but more about the order of traversal.

### Tree
**Tree Preorder:**


```javascript
BASE CASE
Action
Left Check = Recursive call with node.left as the parameter
Right Check = Recursive call with node.right as the parameter
```

![[preOrder.gif]]

```javascript
function IterativePreOrder() {
  let stack = [root];
  let res = [];

  while (stack.length) {
    let curr = stack.pop();
    res.push(curr.key);
    if (curr.left) stack.push(curr.left);
    if (curr.right) stack.push(curr.right);
  }

  return res.reverse();
}



function recursivePreOrder(root) {
  if (!root) {
    return [];
  }

  const result = [];

  function traverse(node) {
    if (node) {
      result.push(node.key); // Process the current node
      traverse(node.left);    // Recursively traverse the left subtree
      traverse(node.right);   // Recursively traverse the right subtree
    }
  }

  traverse(root);

  return result;
}
```



**Tree Inorder:**

```javascript
BASE CASE
Left Check = Recursive call with node.left as the parameter
Action
Right Check = Recursive call with node.right as the parameter
```

![[inOrder.gif]]


```javascript
function IterativeInOrder() {
  let stack = [root];
  let res = [];

  while (stack.length) {
    if (curr.left) stack.push(curr.left);
    let curr = stack.pop();
    res.push(curr.key);
    if (curr.right) stack.push(curr.right);
  }

  return res.reverse();
}



function recursiveInOrder(root) {
  if (!root) {
    return [];
  }

  const result = [];

  function traverse(node) {
    if (node) {
      traverse(node.left);    // Recursively traverse the left subtree
      result.push(node.key);  // Process the current node
      traverse(node.right);   // Recursively traverse the right subtree
    }
  }

  traverse(root);

  return result;
}
```


**Tree Postorder:**

```javascript
BASE CASE
if (node == null) return 0; // Alternative cases
Left Check = Recursive call with node.left as the parameter
Right Check = Recursive call with node.right as the parameter
Action Example: Get the height - `return Math.max(left, right) + 1;`
Alternative action: Push the current node to a value array
```

![[postOrder.gif]]

```javascript
function IterativePostOrder() {
  let stack = [root];
  let res = [];

  while (stack.length) {
    if (curr.left) stack.push(curr.left);
    if (curr.right) stack.push(curr.right);

    let curr = stack.pop();
    res.push(curr.key);
  }

  return res.reverse();
}




function recursivePostOrder(root) {
  if (!root) {
    return [];
  }

  const result = [];

  function traverse(node) {
    if (node) {
      traverse(node.left);    // Recursively traverse the left subtree
      traverse(node.right);   // Recursively traverse the right subtree
      result.push(node.key);  // Process the current node
    }
  }

  traverse(root);

  return result;
}
```


### Graph
>[!important] 
>In graph DFS, the concept of "in-order" doesn't apply in the same way because there may not be a strict hierarchy or ordering between neighbors.

It's similar to BFS but uses stacks with `pop()` instead of `shift()`. The order of operations in recursive implementation might mimic pre and post-order traversal, even though these concepts may not directly apply to graphs.

1. Create and store the graph in a stack.
2. Initialize a `current` variable.
3. Create and store the added graph nodes in a new set.
4. Loop through the stack while its length is greater than 0.
5. Update `current` by popping (using `stack.pop()`) the last element from the stack.
6. Loop through the edges of the graph, checking if they have been visited with the set.
7. Push and add the edge into the stack and set.
8. Perform any desired action with `current.id`, such as pushing it to an array.


```javascript
function iterativeDFSPreOrder(graph, startNode) {
  const visited = new Set();
  const stack = [startNode];
  const result = [];

  while (stack.length) {
    const currentNode = stack.pop();
    if (!visited.has(currentNode)) {
      result.push(currentNode); // Pre-order processing
      visited.add(currentNode);

      for (const neighbor of graph[currentNode]) {
        if (!visited.has(neighbor)) {
          stack.push(neighbor);
        }
      }
    }
  }

  return result;
}


function recursiveDFSPreOrder(graph, currentNode, visited = new Set(), result = []) {
  if (!visited.has(currentNode)) {
    result.push(currentNode); // Pre-order processing
    visited.add(currentNode);

    for (const neighbor of graph[currentNode]) {
      if (!visited.has(neighbor)) {
        recursiveDFSPreOrder(graph, neighbor, visited, result);
      }
    }
  }

  return result;
}
```


```javascript
function iterativeDFSPostOrder(graph, startNode) {
  const visited = new Set();
  const stack = [startNode];
  const result = [];

  while (stack.length) {
    const currentNode = stack[stack.length - 1];

    if (visited.has(currentNode)) {
      stack.pop();
      result.push(currentNode); // Post-order processing
    } else {
      visited.add(currentNode);

      for (const neighbor of graph[currentNode]) {
        if (!visited.has(neighbor)) {
          stack.push(neighbor);
        }
      }
    }
  }

  return result;
}


function recursiveDFSPostOrder(graph, currentNode, visited = new Set(), result = []) {
  if (!visited.has(currentNode)) {
    visited.add(currentNode);

    for (const neighbor of graph[currentNode]) {
      if (!visited.has(neighbor)) {
        recursiveDFSPostOrder(graph, neighbor, visited, result);
      }
    }

    result.push(currentNode); // Post-order processing
  }

  return result;
}
```

```
 * 

 *                     2 

 *                   /   \ 

 *            0 ~~~ 1    4  ~~~ 5 ~~~ 3 

 *                \   / \    / 

 *                  7     6 

DFS: [ 

  0, 

  1, 7, 4, 

  6, 5, 3, 

  2 

] 
```
