---
tags:
  - codeFlow
  - CodebaseDecision
  - CodingProblem
  - potentialMerge
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different aspect of a algorithm to examine.
Status: Refinement
Started: 
EditDate: 
Relates: "[[Iteration vs Recursion]]"
Peer Reviewed: 0
dg-publish:
---
![[paths.gif]]
## Problem Identification

When approaching a problem, it's important to begin by identifying the core issue at hand. Rather than focusing too much on the desired output, consider the attributes and parameters involved, especially when multiple parameters are at play prioritize the parameter that is apart of the main functionality or main problem.

### Keeping Scope in Mind

It's essential to consider the broader scope of a problem and its impact on the larger context. While precision is valuable for specific tasks, a more generalized approach can provide a broader perspective.

- Precision is useful for specific elements within a scope.
- A more generalized approach allows you to experience the bigger picture.
- Alternating between precision and a broader approach is key; no single tool works for every situation.




## Handling Numeric Values
![[numbers.png]]
**Numeric values can also be represented with ASCII values
- For an array of numbers or numbers, consider attributes like:
  - Natural numbers (positive numbers)
  - Whole numbers (Natural and zero)
  - Integers (Whole and negative numbers)
  - Rational numbers (Integers, Decimal, Fractions )
  - Min/Max values, zero, and decimal aspects.
  - Evaluate range, partial range, order, and decimal floor/ceiling.

## Handling String Values
- For strings or arrays of strings, think about the following attributes:
	- Check for emptiness, spaces, and length (odd/even).
	- Examine substrings, Unicode values, and special characters.
	- Consider unique characters, fixed-length strings, and letter casing.
	- Account for null as an argument.
	- Use built-in functions cautiously; explore algorithm patterns.
	- For arrays of characters, analyze length, range, empty spaces, and duplicates.
	- Mind loop direction and duplicates; use sets for efficiency.
	- Don't forget the alphabet (26 characters)
	- Be cautious with assumptions about ASCII values avoid defaulting to ASCII values.

## Array Operations
- Boundary analysis: -1 and 1 after the array length
- Incrementing the entire length of the array
- Handling nested arrays with a single loop
- Min/max considerations
- Splitting an array using binary search
  ```javascript
  const length = array.length;
  const middle = Math.floor(length / 2);
  const left = array.slice(0, middle);
  const right = array.slice(middle);
  ```

## Starting Point and End point
- Do a Boundary Analysis Analyze the current value in relation to the values before and after.
- Evaluate whether you need to traverse every element, which ties back to understanding the problem.
- Considerations for values contained in a specific range
- Length or calculation value
- Reducing iteration by breaking down large ranges
- Decrementing arrays from the end index to the start (array.Length to 0)

## Fixed Length Data

Dealing with data of fixed length, whether it's a matrix or an array, may require approaches like Merge Interval. This can apply to numbers or when handling ASCII values for letters.

- Focus your conditional logic on the fixed length, which is critical for solving these problems.

- Consider how these boundary cases may overlap or relate to each other.


## Data Structures Brain Storming
- When examining an algorithm, identify the data structures, types, and constructs that can be used.


# Pre & Post Processing
## Sorted Data

When data is sorted, focus on binary search, particularly by targeting the middle element.

## Partially Sorted Data

In cases of partial sorting, especially with elements within a specified range, cyclic sort is a valuable approach.

## Unsorted Data

For unsorted data, the choice of algorithm depends on the problem. If preserving order is not a priority, sorting followed by binary search can be effective. Otherwise, consider patterns that might include a linear search. Also depending on the problem if you have to search use a hashtable or hashmap.


## Sort Algorithm Boundary Cases
- Potential scenarios where sorting algorithms may fail:
  - Empty input
  - Input with only one element
  - Very long input
  - Garbage inside the collection to be sorted
  - Null input
  - Duplicate elements
  - Collection with all elements equal
  - Odd/even length input


## Nested Objects and Recursion
When working with nested objects like JSON, you often encounter a structure that resembles a tree, involving repetitive tasks such as traversing file directories. In such cases, using recursion can be a powerful technique to efficiently navigate and process these nested structures. Additionally, when you delve deeper into handling repetitive sub problems within these nested structures, you may consider employing memoization techniques to optimize performance and avoid redundant calculations.



## Apply Steps to Other Data Structures

- Extend these steps and considerations to other data structures, utilizing built-in functionalities where applicable.


