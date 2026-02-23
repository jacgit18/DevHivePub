---
tags:
  - MicroCodebaseDecision
author:
  - jacgit18
Purpose: This documentation discusses Grokking Algorithm patterns
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
> [!note] The pattern names are just visual abstraction of the pattern
## Sliding Window

- **Definition:** Sliding Window is a pattern for efficiently processing arrays or strings by maintaining a "window" of elements.
- **Key Elements:**
  - Input array or string.
  - WindowStart and WindowEnd.
	  - You may check if it is greater than diff between WindowEnd to WindowStart  + 1 
  - Window size conditions to increments and decrements or both.
  - Iteration by array length.
  - Target sum  
- **Potential Problem Goals**
	- You may also leverage min and max other Math methods depending on what you're doing 
	- You may return something like length, minLength, maxLength in terms of window size 
- **Use Cases:**
  - Contiguous sub-arrays or sublists.
  - Finding the smallest, longest, or other subarray.
- **Hints:** 
	- Look for keywords like "contiguous," "subarray," and "sublist."
	- Typically we use all of the elements within the sliding window for the problem like too combine things or do some type of action within window range 
- **Use Sorting:** Sort the input arrays/lists if necessary before applying the Two Pointer technique. 

Two pointer and Sliding window can be interchangeable solution but one would just be more efficient then the other depending on the what the problem solution demands typically pointer is used for comparison while window is used for other action like adding or doing some other action with the elements in the range of the window but not specifically comparison of values.

## Two Pointer
Problem [[Two Pointer Indicators |Indicators]]
*Right pointer doesn't always need to point to last element*

don't always need to move both pointers one pointer can stay still

- **Definition:** The Two Pointer pattern involves using two pointers to traverse arrays or strings.
- **Commonalities & Common things to Leverage**
	- Similar attributes to Sliding window 
	- Math methods like min, max, etc...
- **Common Sub Steps:**
	- Iterate through array with while loop with condition of while left is less then right pointer 
	- Maybe swap values 
- **Key Elements:**
  - Input array or string.
  - Left and right pointers.
- **Use Cases:**
  - Comparing values at two pointers.
  - Fast-slow pointer variations.
  - Very useful when dealing with cyclic Linked Lists or Arrays. 
  - In Place sort which involves comparing two values at a time.
 > [!important]  Used to compare the values at the two pointer instead of all the elements between the pointers. 
- **Use Sorting:** Sort the input arrays/lists if necessary before applying the Two Pointer technique. 

>[!note] Two pointer can be applied to two arrays or strings or a combination of a string and a array or used to find numbers in a range just like Sliding window  

## Fast & Slow Pointers

- **Definition:** Fast & Slow Pointers are a valuable technique used for detecting cycles in linked lists.

- **Complexity:** The time complexity of using Fast & Slow Pointers for cycle detection in linked lists is typically O(N), where N represents the number of elements in the list.

- **Key Elements:**
  - A linked list data structure.
  - Two pointers, the slow pointer, and the fast pointer.
  - Iterative traversal of the linked list to check for cycles.

- **Potential Problem Goals:**
  - Detect cycles or loops in a linked list.
  - Ensure the integrity of a linked list, preventing infinite loops in data structures.

- **Steps:**
  1. Check if the head of the linked list exists. If `fastPointer` or `fastPointer.next` does not exist, return `false`.
  2. Check if `slowPointer` equals `fastPointer` or `slowPointer` equals `fastPointer.next`. If either condition is true, return `true`.
  3. Initialize both slow and fast pointers:
     - Create and store the linked list HEAD in the `slowPointer` variable.
     - Create and store the linked list HEAD in the `fastPointer` variable.
  4. Iterate through the list.
  5. Update the `slowPointer` to `slowPointer.next`.
  6. Update the `fastPointer` to `fastPointer.next.next`.

- **Use Cases:** Fast & Slow Pointers are primarily used for detecting cycles in linked lists. This is crucial to ensure the integrity of linked data structures and to prevent infinite loops in algorithms that operate on linked lists.

- **Hints:**
  - Fast & Slow Pointers are an efficient approach to identifying cycles in linked lists, and they can be instrumental in various applications, such as detecting cycles in graphs represented as linked lists.

Fast & Slow Pointers are a powerful technique that offers a straightforward way to detect cycles or loops within linked lists, ensuring data structure integrity and preventing infinite loops in various algorithms.


## Reversing a Linked List

- **Definition:** Reversing a linked list is a fundamental operation that involves changing the order of elements in a singly linked list. It transforms the list so that the last element becomes the first, and so on, effectively flipping the direction of the list.

- **Complexity:** Reversing a linked list operates with a time complexity of O(N), where N represents the number of elements in the linked list.

- **Key Elements:**
  - A singly linked list data structure.
  - Three pointers: `prev`, `current`, and `next`.
  - Iterative traversal of the list to reverse the order of elements.

- **Potential Problem Goals:**
  - Improve the efficiency of algorithms that require processing elements in reverse order.
  - Solve problems that involve reordering elements in a linked list.

- **Steps:**
  1. Initialize three pointers: `prev`, `current`, and `next`. Set `prev` to `null` initially.
  2. Start at the head of the linked list (`current` points to the head).
  3. While `current` is not `null`:
     - Store the next node (`current.next`) in the `next` pointer to prevent losing the rest of the list.
     - Update the `current.next` to point to the previous node (`prev`), effectively reversing the pointer direction.
     - Move the `prev` pointer to the `current` node.
     - Move the `current` pointer to the `next` node.
  4. Once the loop is complete, the `prev` pointer will be pointing to the new head of the reversed list.
  5. Update the head of the original list to the node pointed to by `prev`, making it the head of the reversed list.

- **Use Cases:** Reversing a linked list can be useful in various scenarios, such as optimizing algorithms or solving problems that require elements to be processed in reverse order. It's a foundational operation in data structure manipulation.

- **Hints:**
  - This operation can be especially valuable when algorithms need to access elements in a reverse order, as it simplifies traversal and data processing.

Reversing a linked list is a crucial technique in data structure manipulation and is frequently used to enhance algorithm efficiency or address specific challenges requiring reversed element order within the list.


## Cyclic Sort

^b310e2

- **Definition:** Cyclic Sort is an algorithmic technique that sorts an array in-place by iterating through the array and placing each element in its correct position, ensuring the sorted order in a cycle-like manner.
- **Complexity:** Cyclic Sort operates with a time complexity of O(N) due to its linear nature.
- **Key Elements:**
  - Input array with elements ranging from 1 to N.
  - Iterative swapping of elements to their correct positions.
  - Looping through the array to place each element at its corresponding index.
- **Potential Problem Goals:**
  - Sort an array containing distinct elements in the range 1 to N.
  - Find missing or duplicate elements within a given range.
  - Ensure the array is sorted in ascending order without using additional space.
- **Steps:**
  1. Initialize an index.
  2. Find the current and decremented subarrays.
  3. Swap elements as needed. 
```javascript
  [nums[index], nums[decrementedSubarray]]   
  =    
  [nums[decrementedSubarray], nums[index]] 
```
  4. Increment the index.
- **Use Cases:**
  - Sorting arrays with missing or duplicate elements in a known range.
  - Ensuring an array is sorted in place without additional memory overhead.
  - The work is focused on the elements of array since fixed in terms of your dealing with a range of numbers with one or more numbers missing in the range.
- **Hints:**
  - Look for problems involving array sorting without utilizing additional space.
  - Typically used when the elements are within a specific range and there are no duplicates.

This technique is particularly useful when dealing with arrays containing unique elements within a known range and aims to sort the array in a cyclic manner without additional space overhead.



## K-Way Merge

- **Definition:** K-Way Merge is a technique used to merge K sorted arrays or lists into a single sorted collection. This approach extends the concept of merging pairs of arrays (as in traditional merge sort) to handle K arrays efficiently.

- **Complexity:** The time complexity of K-Way Merge is typically O(N log K), where N is the total number of elements across all arrays. The efficiency arises from the use of priority queues or heap data structures.

- **Key Elements:**
  - K sorted arrays or lists.
  - A data structure to efficiently track the smallest elements during the merging process, often implemented using a priority queue or a min-heap.

- **Potential Problem Goals:**
  - Merge K sorted arrays into a single sorted array.
  - Efficiently process and merge data from K different sources.

- **Steps:**
  1. Initialize a priority queue or a min-heap to track the smallest elements from each array.
  2. Populate the priority queue with the first element from each of the K arrays.
  3. Extract the smallest element from the priority queue and add it to the result.
  4. Replace the extracted element with the next element from its respective array in the priority queue.
  5. Repeat steps 3-4 until all elements are merged.

- **Use Cases:** K-Way Merge is commonly used in scenarios where data is distributed across multiple sources or when dealing with K sorted arrays, such as merging results from parallel computations.

- **Hints:**
  - Choose the appropriate data structure (priority queue or min-heap) based on the language and problem requirements.
  - Keep track of the array index associated with each element in the priority queue to efficiently fetch the next element from that array during the merging process.

K-Way Merge is a powerful technique for efficiently merging K sorted arrays, providing an effective solution for scenarios involving distributed data or parallel processing. The priority queue or min-heap is a key component in maintaining efficiency during the merging process.


### k way merge vs 2-way Merge

The main difference between k-way merge and 2-way merge is the number of sorted lists being merged. 

In 2-way merge, two sorted lists are merged into a single sorted list. It's a basic merging operation often used in algorithms like Merge Sort.

On the other hand, k-way merge involves merging k sorted lists into a single sorted list. This generalizes the concept to handle more than two input lists. Algorithms like external sorting or certain types of database query processing may employ k-way merging when dealing with a larger number of sorted datasets.

#### More use cases
Dealing with multiple arrays, rows in two-dimensional arrays, or multiple linked lists, where you find the lowest value and store them in order from least to greatest, similar to a min-heap or merge sort.

In summary, 2-way merge deals with two sorted lists, while k-way merge handles k sorted lists.



## Merge Intervals

- **Definition:** Merging Intervals is a common algorithmic technique used to combine overlapping or adjacent intervals into a single interval, simplifying data representations and solving problems related to time or range intervals.
- **Complexity:** Merging Intervals typically operates with a time complexity of O(N log N) when sorting is involved and O(N) without sorting, where N is the number of intervals.
- **Key Elements:**
  - A collection of intervals, represented as pairs of start and end points.
  - Identifying and merging overlapping or adjacent intervals.
  - Managing interval data efficiently for various applications.
- **Potential Problem Goals:**
  - Combine and condense overlapping time intervals.
  - Determine the availability of time slots when scheduling events.
  - Find the maximum number of overlapping intervals.
- **Steps:**
  1. Sort the intervals based on their start points (if not already sorted).
  2. Initialize an empty result list to store merged intervals.
  3. Iterate through the sorted intervals, merging overlapping or adjacent ones.
  4. Add the merged intervals to the result list.
  5. When working with multiple matrices or comparing pairs, create and store indexes for each matrix.
  6. Access matrix elements using indices and reassign values as needed.
  7. To find the non-overlapping intervals, push the max between start points and min between end points into the new array.
  8. Implement conditional logic for incrementing or handling multiple matrices and pairs.
- **Use Cases:**
  - Scheduling meetings and events to find available time slots.
  - Consolidating overlapping date ranges in a database.
- **Hints:**
  - Sorting intervals by their start points simplifies the merging process.
  - Carefully handle edge cases, such as when intervals are already sorted or if they have gaps.

Merging Intervals is a valuable technique for solving a wide range of problems involving overlapping or adjacent intervals, helping to simplify and manage interval data efficiently, especially when dealing with multiple matrices or comparisons between pairs of intervals.


## Subsets/Backtracking

- **Definition:** Subsets/Backtracking is a powerful algorithmic technique used to explore and generate unique paths, combinations, or solutions in a matrix, graph, or data structure. It is commonly applied in solving complex problems that involve exhaustive search or the generation of all possible combinations. This technique can be applied in various ways, including using binary search or starting at a particular part of the matrix based on the specific problem requirements.

- **Complexity:** The time complexity of Subsets/Backtracking can vary depending on the specific problem and implementation, often ranging from O(2^N) to O(N^N).

- **Key Elements:**
  - A matrix, graph, or data structure with multiple possible paths or combinations.
  - Recursive traversal to explore various paths.
  - Conditions for determining when to backtrack, such as out-of-bounds, visited positions, or target conditions.

- **Potential Problem Goals:**
  - Generate all unique paths in a matrix or graph.
  - Find combinations of elements that satisfy specific conditions.
  - Solve problems that require exhaustive search, such as the "N-Queens" problem or solving puzzles like Sudoku.

- **Steps:**
  1. Begin a recursive traversal to explore various paths or combinations.
  2. Implement conditions for backtracking, which may include checking for out-of-bounds positions, visited nodes, or target conditions.
  3. Mark coordinates or elements as visited as you traverse them.
  4. Continue the exploration until all paths or combinations have been considered.

- **Use Cases:** Subsets/Backtracking is commonly used for generating unique paths in a matrix, solving combinatorial problems, and addressing scenarios where exhaustive search is required.

- **Hints:**
  - Subsets/Backtracking is a versatile technique used in various applications, including puzzle-solving, pathfinding, and combinatorial optimization.
  - Carefully define the conditions for backtracking to avoid unnecessary exploration and improve efficiency.

Subsets/Backtracking is a versatile technique with a wide range of applications, including puzzle-solving, pathfinding, and combinatorial optimization. Carefully defining the conditions for backtracking is crucial to avoid unnecessary exploration and improve efficiency.

## Modified Binary Search

**Definition:** Modified Binary Search is an algorithmic technique used to efficiently search for a target element in a sorted array or a similar data structure.

**Complexity:** The time complexity of Modified Binary Search is typically O(log N), making it an efficient search method for large datasets.

**Key Elements:**
- A sorted array or data structure.
- A target element to search for.
- Low and high indices to define the search range.
- Binary search algorithm for efficient target identification.

**Potential Problem Goals:**
- Quickly find a specific element in a sorted array or data structure.
- Identify the location or presence of a target value.
- Optimize search operations for ordered datasets.

**Steps:**
1. Create/Store Low with a value of 0 and High with a value of `array.length - 1`.
2. Iterate while Low < High.
3. Create/Store mid-point with a value of either:
   - `Low + floor((High - Low + 1) / 2)` or
   - `Low + floor((High - Low) / 2)`.

   In the context of merge sort, you would Create/Store mid with a value of `floor(array.length / 2)`.
4. Update Low with the value of `array.slice` (values in the range of array start index to middle).
5. Update High with the value of `array.slice` (with just the middle) or Create/Store Low with the value of `array.slice` (values in the range of array start index to middle + 1), so High would have 1 more value than Low, and High with the value of `array.slice` (middle + 1).
6. Do some type of check when you want to UPDATE High.
7. Do some type of check when you want to UPDATE LOW.

**Use Cases:** Modified Binary Search is frequently used for searching in sorted arrays, such as finding an element in a list of names or locating a value in a sorted database.

**Hints:**
- Modified Binary Search is a powerful technique for quickly locating specific elements in sorted data structures.
- Ensure the data is sorted before applying binary search for optimal results.

Modified Binary Search is a valuable algorithmic technique employed in various applications to efficiently locate a target element within a sorted array or similar data structure, reducing the search time significantly.


## Bitwise XOR

- **Definition:** Bitwise XOR (exclusive or) is a binary operation that takes two binary numbers and returns a new binary number. It performs the XOR operation on each pair of corresponding bits: if the bits are the same, the result is 0; if the bits are different, the result is 1.

- **Complexity:** Bitwise XOR operates in constant time, O(1), regardless of the number of bits in the binary representation.

- **Key Elements:**
  - Two binary numbers or bit patterns.
  - Bitwise XOR operator (^).

- **Potential Problem Goals:**
  - Combine or compare binary values bit by bit.
  - Perform bit-level toggling or flipping.
  - Implement various encryption and decryption techniques.
  - Solve specific programming problems that involve bit manipulation.

- **Steps:**
  1. Take two binary numbers or bit patterns to be XORed.
  2. Perform the XOR operation on each pair of corresponding bits.
  3. The result will be a new binary number representing the XORed values.

- **Use Cases:** Bitwise XOR is used in various applications, including cryptography, error detection and correction, data manipulation, and solving programming problems that involve bitwise operations.

- **Hints:**
  - Bitwise XOR is often used for toggling specific bits in a binary number, encrypting data, and solving algorithms that require bitwise manipulation. It's a fundamental operation in low-level programming and computer science.

Bitwise XOR is a fundamental operation in binary arithmetic, offering a versatile way to manipulate binary data, encrypt information, and solve specific problems that involve bitwise operations.

## Top K Elements

- **Definition:** Top K Elements refers to a technique in computer science and data analysis for finding the K largest or smallest elements in a collection, such as an array, list, or data stream.

- **Complexity:** The time complexity of finding the top K elements depends on the chosen data structure or algorithm, but it often ranges from O(N log N) for sorting methods to O(N log K) using data structures like heaps.

- **Key Elements:**
  - A collection of elements.
  - The value of K, representing the number of elements to retrieve.
  - Data structures like heaps, priority queues, or sorting algorithms for efficient retrieval.

- **Potential Problem Goals:**
  - Find the K largest or smallest numbers in an array or list.
  - Identify the most frequent elements in a dataset.
  - Solve problems that require selecting or processing a specific number of elements from a larger collection.

- **Steps:**
  1. Choose a suitable data structure or algorithm based on the problem and K value.
  2. Process the elements in the collection, maintaining the top K elements.
  3. Update the selection as new elements arrive or as the collection changes.
  4. Retrieve the top K elements as needed.

- **Use Cases:** Top K Elements is used in a wide range of applications, including data analysis, stream processing, priority scheduling, and solving problems that involve selecting a specific number of elements from a larger dataset.

- **Hints:**
  - Consider the problem constraints, such as the size of the dataset, the value of K, and the desired efficiency, to choose the most suitable approach for finding the top K elements.
  - Data structures like heaps or priority queues are often used to maintain the top K elements efficiently.

Top K Elements is a versatile technique that is frequently applied in computer science and data analysis to identify and retrieve the K largest or smallest elements from a collection, allowing for efficient data processing and problem-solving.


## Dynamic Programming

- **Definition:** Dynamic Programming is a method for solving complex problems by breaking them down into simpler, overlapping subproblems and solving each subproblem only once, storing the results to avoid redundant computations.

- **Key Elements:**
  - **Optimal Substructure:**
    - The problem can be broken down into smaller, simpler subproblems, and the solution to the overall problem can be constructed from optimal solutions to its subproblems.
  - **Overlapping Subproblems:**
    - Subproblems recur several times, and solutions to these subproblems are reused instead of recomputed.
  - **Memoization or Tabulation:**
    - Techniques to store and reuse solutions to subproblems, avoiding redundant calculations.
  - **Recursive Formulation:**
    - Often problems can be expressed recursively, solving for smaller instances and combining them for the overall solution.

- **Potential Problem Goals:**
  - Optimize time and space complexity by avoiding redundant computations.
  - Achieve efficient solutions for problems with optimal substructure and overlapping subproblems.

- **Use Cases:**
  - **Fibonacci Sequence:**
    - Calculate Fibonacci numbers efficiently using memoization or tabulation.
  - **Shortest Path Problems:**
    - Find the shortest path in a graph or grid using dynamic programming techniques.
  - **Longest Common Subsequence:**
    - Determine the longest common subsequence between two sequences.
  - **Knapsack Problem:**
    - Optimize the selection of items to maximize or minimize a value while staying within a given limit.

- **Hints:**
  - Recognize problems that exhibit optimal substructure and overlapping subproblems.
  - Break down the problem into smaller, solvable subproblems.
  - Consider memoization (top-down) or tabulation (bottom-up) based on the problem requirements.

- **Example:**
  - Solving the Fibonacci sequence efficiently using dynamic programming involves storing and reusing solutions to subproblems, reducing the overall time complexity.

- **Comparison with Greedy or Divide and Conquer:**
  - Dynamic programming differs from greedy algorithms and divide-and-conquer strategies by solving each subproblem only once and storing the results for future use.

Understanding dynamic programming is crucial for tackling complex optimization problems efficiently. It provides a systematic approach to problem-solving by breaking down intricate problems into manageable subproblems and avoiding redundant computations through memoization or tabulation.


## Knapsack Problem

- **Definition:** The Knapsack Problem is a classic optimization problem where the goal is to select a subset of items with maximum value or minimum cost, considering the constraint of a limited capacity.

- **Key Elements:**
  - **Items:**
    - A set of items, each with a specific weight and value.
  - **Capacity:**
    - The maximum weight or size that the knapsack can hold.
  - **Objective:**
    - Maximize the total value of selected items or minimize the total cost while staying within the capacity.

- **Types of Knapsack Problems:**
  - **0/1 Knapsack:**
    - Each item can either be selected or rejected, not partially.
  - **Fractional Knapsack:**
    - Items can be broken into fractions, and a fraction of an item can be selected.
  - **Multiple Knapsack:**
    - Multiple knapsacks with different capacities, and items need to be distributed among them optimally.

- **Potential Problem Goals:**
  - Optimize the selection of items to maximize total value or minimize total cost within the given capacity.
  - Implement efficient algorithms to solve different variations of the Knapsack Problem.

- **Use Cases:**
  - **Resource Allocation:**
    - Allocating limited resources (like time, budget, or space) to maximize value.
  - **Inventory Management:**
    - Selecting items for sale to maximize profit within storage constraints.

- **Hints:**
  - Recognize the problem as a Knapsack Problem based on the presence of items, weights, values, and capacity constraints.
  - Consider dynamic programming, greedy algorithms, or other optimization techniques depending on the problem type.

- **Example:**
  - Solving the 0/1 Knapsack Problem involves choosing items to maximize total value while not exceeding the knapsack's weight capacity.

- **Comparison with Other Problems:**
  - Different from dynamic programming problems where solutions to subproblems are reused; in Knapsack, each item is either selected or rejected, leading to overlapping subproblems.

The Knapsack Problem is a fundamental optimization challenge with various real-world applications. Understanding its variations and choosing the appropriate algorithm is crucial for solving resource allocation problems efficiently.

## Topological Sort

- **Definition:** Topological Sort is an ordering of the vertices of a directed acyclic graph (DAG) such that for every directed edge (u, v), vertex u comes before vertex v in the ordering.

- **Key Elements:**
  - **Directed Acyclic Graph (DAG):**
    - A graph with directed edges and no cycles.
  - **Ordering:**
    - Arranging vertices in a linear order based on dependencies.
  - **Indegree and Outdegree:**
    - Indegree represents the number of incoming edges to a vertex, and outdegree represents the number of outgoing edges.
  - **Valid Topological Sort:**
    - The ordering must be valid, satisfying the dependencies of the graph.

- **Potential Problem Goals:**
  - Find a valid topological ordering for a given directed acyclic graph.
  - Identify dependencies and the order of execution for tasks or events.

- **Use Cases:**
  - **Course Prerequisites:**
    - Determining the order in which courses must be taken based on prerequisites.
  - **Task Scheduling:**
    - Establishing a sequence for executing tasks with dependencies.
  - **Compiler Dependency Resolution:**
    - Resolving dependencies in compiling code with multiple source files.

- **Hints:**
  - Recognize the problem as involving a directed acyclic graph (DAG).
  - Utilize indegree and outdegree information to identify the correct topological ordering.
  - Employ depth-first search (DFS) or breadth-first search (BFS) algorithms to find the ordering.

- **Algorithm Overview:**
  - **Step 1:**
    - Identify vertices with an indegree of 0; these are the potential starting points.
  - **Step 2:**
    - Remove the chosen vertex (with indegree 0) and its outgoing edges.
  - **Step 3:**
    - Update indegrees of remaining vertices.
  - **Step 4:**
    - Repeat Steps 1-3 until all vertices are included in the ordering.

- **Example:**
  - In a course prerequisite graph, a topological sort reveals the order in which courses should be taken to meet prerequisites.

- **Comparison with Other Graph Algorithms:**
  - Distinct from cyclic graphs, where no valid topological ordering exists.
  - Unlike depth-first search (DFS), topological sort focuses on the linear ordering of vertices rather than exploration.

Understanding topological sort is crucial for tasks involving dependencies and ordering, making it a fundamental tool in various domains such as project management, course planning, and compiler design.


## Working with Strings:
- For common string operations, consider using maps or tries.

## General Optimization:
- Hash maps are often the key to improving time complexity in various coding scenarios.
- Hash tables and precomputed information (e.g., sorted data) are excellent for code optimization.