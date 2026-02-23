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
EditDate: 2023-11-02
Relates: "[[Graph]]"
Peer Reviewed: 0
dg-publish:
---
![[Graph.gif]]

## Graph

A graph is a collection of nodes or values called vertices, and the relations between vertices are called edges.

Graphs are versatile and can be used to represent various real-world scenarios. For instance, a social network can be represented as a graph, where users are vertices, and friendships are edges. Similarly, a city map can be represented as a graph, with locations in the city as vertices and roads as edges.

## Graph Cycle

A cycle in a graph occurs when three or more vertices are connected in a way that forms a closed loop. Note that the definition of a graph cycle can sometimes include cycles of length two or one. When dealing with coding interviews involving graph cycles, it's crucial to clarify what exactly constitutes a cycle.

## Acyclic Graph

An acyclic graph is a graph that contains no cycles. It's a graph structure where you cannot travel in a closed loop through the edges.

## Cyclic Graph

A cyclic graph is a graph that contains at least one cycle. It's a graph structure where you can traverse through the edges in a closed loop.

## Directed Graph

A directed graph is a graph where the edges have directions, meaning they can only be traversed in one specified direction. For example, a graph representing airports and flights would likely be directed, as flights go from one airport to another in a specific direction.

## Undirected Graph

An undirected graph is a graph where the edges have no specific direction and can be traversed in both directions. For example, a graph of friends is typically undirected since friendship is bidirectional in nature.

## Connected Graph

A graph is considered connected if there is a path of one or more edges connecting any pair of vertices. In the case of a directed graph, it is:

- Strongly connected if there are bidirectional connections between all pairs of vertices.
- Weakly connected if there are connections (though not necessarily bidirectional) between all pairs of vertices.

A graph that isn't connected is referred to as disconnected.

[For more detailed information, you can refer to the provided links.]

Graph data structures are not built into Java by default, but you can implement graphs using Java Collections.

## Graph Algorithms

Different types of graphs require specific representations and problem-solving approaches. Several algorithms are commonly used with various types of graphs:

- Depth-first search (DFS): A traversal algorithm that uses a stack and explores vertices in a delayed manner.

- Breadth-first search (BFS): A traversal algorithm that uses a queue and explores vertices level by level.

- Dijkstra's algorithm: Finds the shortest path between nodes in weighted graphs using a priority queue.

- The Bellman-Ford algorithm: Computes shortest paths in weighted digraphs and handles negative edge weights using two loops.

Each of these algorithms has different time complexities based on the type of graph and data structure used.

Implementation pattern:
- Stack: Depth-first search (Time Complexity: O(E+V))
- Queue: Breadth-first search (Time Complexity: O(E+V))
- Priority Queue: Dijkstra's algorithm (Time Complexity: O(E+V log V))
- Bellman-Ford: Handles negative edge weights with Time Complexity: O(VE).

Dijkstra's algorithm works in O(E+V log V) only if the priority queue has O(log N) add/remove complexity.

The Bellman-Ford algorithm is similar to Dijkstra's but iterates over every edge multiple times, making its time complexity O(VE) in the worst case.

The difference in time complexity is O(E+V log V) for Dijkstra's and O(VE) for Bellman-Ford.

[For more in-depth information on graphs and graph traversal algorithms, you can refer to the provided links.]