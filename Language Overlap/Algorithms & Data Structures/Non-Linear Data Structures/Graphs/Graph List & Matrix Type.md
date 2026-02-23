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
Relates: "[[Graph]]"
Peer Reviewed: 0
dg-publish:
---
List & Matrix represent and are used to store the relationships between nodes (vertices) and edges in a graph. Each has its own advantages and is chosen based on the specific characteristics of the graph and the types of operations you need to perform.

## Adjacency List:

An adjacency list is a commonly used method to represent a graph, where each vertex of the graph is associated with a array of its neighboring vertices.

**Key Advantages of Adjacency Lists:**

- Efficient for Sparse Graphs: This representation is particularly efficient for sparse graphs, where there are relatively few edges. It minimizes memory wastage by only storing information about existing edges.

- Easy Neighboring Vertex Traversal: Adjacency lists make it straightforward to traverse neighboring vertices for each vertex in the graph.

- Example: For instance, in a graph with vertices A, B, C, and edges (A-B) and (A-C), the adjacency list for vertex A might look like [B, C].

**Using Linked Lists for Adjacency Lists:**

In practice, adjacency lists are often implemented using linked lists:

1. Create a linked list for each vertex in the graph.
2. Populate the linked list for each vertex with pointers or references to its neighboring vertices.

**Comparing Adjacency Lists to Adjacency Matrices:**

- **Memory Usage:** For sparse graphs, adjacency lists are more memory-efficient, using O(V + E) memory, where V is the number of vertices and E is the number of edges. In contrast, adjacency matrices use O(V^2) memory, which can be wasteful for sparse graphs.

- **Edge Lookup:** In an adjacency list, looking up edges connected to a vertex takes O(degree) time, where the degree is the number of neighbors. Adjacency matrices offer constant-time edge lookup (O(1)), which is advantageous for dense graphs or scenarios requiring frequent edge searches.

- **Space and Insertion Complexity:** Linked list-based adjacency lists are space-efficient for sparse graphs and have lower insertion complexity when adding or removing edges. Adjacency matrices are better suited for dense graphs and provide constant-time insertion and removal complexity.

In summary, the choice between using linked lists (adjacency lists) or arrays (adjacency matrices) for graph implementation hinges on your graph's specific characteristics, such as density and the operations you need to perform. Sparse graphs with dynamic requirements often favor linked list-based implementations, while dense graphs and frequent edge lookups may benefit from array-based representations.


## Incidence List:
- An incidence list is used to represent graphs that are directed or contain weighted edges. It associates vertices with incident edges, including information about the edge's weight and direction.  
- It is commonly used for algorithms related to edge traversals, like Dijkstra's algorithm.  
- Example: For a directed graph with vertices A, B, C, and edges (A->B), (A->C), the incidence list for vertex A might include [(A->B), (A->C)].  
  
## Adjacency Matrix:  

^897f42

- An adjacency matrix is a 2D array where each cell represents the presence or absence of an edge between two vertices.  
- It's a compact way to represent graphs with relatively more edges, but it may be space-inefficient for sparse graphs.  
- It allows for quick look-up of whether an edge exists between any two vertices but may require O(V^2) space for a graph with V vertices.  
- Example: In an adjacency matrix, cell (i, j) might be 1 if there is an edge between vertex i and vertex j, and 0 otherwise.  
  
## Incidence Matrix:
- An incidence matrix is used to represent graphs, particularly bipartite graphs, where rows represent vertices, and columns represent edges.  
- The elements of the matrix indicate the relationship between vertices and edges, often using -1, 0, and 1 to represent no connection, incoming edge, and outgoing edge.  
- It is used in certain graph algorithms, such as maximum flow and bipartite matching.  
- Example: In an incidence matrix, rows represent vertices, columns represent edges, and a -1 or 1 indicates the direction of the edge relative to the vertex.  
  




