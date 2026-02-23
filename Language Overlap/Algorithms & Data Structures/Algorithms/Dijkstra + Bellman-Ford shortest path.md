---
tags:
  - AlgorithmExamination
  - graph
  - looping
  - traversal
  - search
  - non-linear
  - pattern
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses path algorithms.
Status: Done
Started: 
EditDate: 2024-02-27
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[graph Pathway.gif]]

# Choosing the Right Algorithm for Shortest Path Problems

## Breadth-First Search (BFS)
- BFS is a great choice for finding the shortest path when all paths have the same weight.
- It works well when considering paths without caring about edge weights.

## Weighted Graphs
- Real-life scenarios often involve weighted graphs where edges have different weights. For example, in navigation systems like Google Maps, some roads are faster due to traffic conditions or shorter distances.
- Weighted graphs have numbers associated with their edges.

## Algorithms for Weighted Graphs
In an interview, if asked about solving the shortest path problem in weighted graphs, consider two common algorithms:

### Bellman-Ford Algorithm
- Accommodates graphs with negative weights.
- Effective for solving the shortest path problem in graphs with negative weights.
- However, it can be relatively slow due to its time complexity.

### Dijkstra Algorithm
- Efficient and faster than Bellman-Ford in most cases.
- Cannot handle graphs with negative weights between nodes.

## Choosing the Right Algorithm
When faced with a problem in a weighted graph, ask the interviewer which algorithm they want to use:
- Breadth-First Search
- Bellman-Ford Algorithm
- Dijkstra Algorithm

### Example:
- If asked to find the shortest path in a weighted graph with no negative weights, choose the Dijkstra Algorithm.
- Dijkstra is suitable for weighted graphs without negative weights.

Understanding the strengths and weaknesses of these algorithms will help you make the right choice in solving shortest path problems during interviews. While encoding these algorithms might be complex, knowing when to use them is often more important than writing the code.

Using Depth-First Search (DFS) for a graph can be likened to exploring each path in a maze until all possible paths are checked. However, DFS is not typically used for finding the shortest path, especially in weighted graphs, where BFS, Bellman-Ford, or Dijkstra algorithms are more suitable.

Feel free to ask for further clarification or if you have any specific questions related to algorithms or graph traversal.