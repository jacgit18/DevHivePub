---
tags:
  - pattern
  - CodingProblem
  - MicroCodebaseDecision
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Dynamic programming.
Status: Done
Started: 2023-12-09
EditDate: 2024-02-27
Relates: 
Peer Reviewed: 0
dg-publish:
---
Dynamic programming is a powerful technique used in computer science and mathematics to solve optimization problems by breaking them down into smaller overlapping subproblems. There are several common dynamic programming patterns that are frequently used to design efficient algorithms.

#### How to Determine If Dynamic Programming Is Suitable

>[!important] 
> Divide&Conquer(includes Recursion) + memoization = Dynamic programming  

1. **Divide into Subproblems**:
   - Can the problem be divided into smaller subproblems?
   - Recursive solutions often indicate a potential for dynamic programming.

2. **Repetitive Subproblems**:
   - Are the subproblems repetitive, i.e., the same calculations occur multiple times?
   - If yes, you can apply memoization to store and reuse solutions.

>[!note]  
>**Dynamic Programming Flow**
>*Probably will come up with FANG Companies*
>
Divide into sub-Problems -> solve with recursion -> memioze or tabulate subproblems and store  

### Understanding Caching

- **Caching** is a technique used to store values for future use, reducing the need for recomputation.
- Think of caching as having a backpack where you keep frequently used items for quick access, similar to reusing books or a pencil for school.
- 
### Top-Down vs Bottom-Up

#### Top-Down Approach (***Memoization***)
  - Recursive approach can use closure.
  - Suitable for smaller input values.
  - Useful for functions where inputs predictably lead to the same outputs.
  - involves storing the return values of a function based on its parameters to avoid redundant calculations.
  - Ideal for problems with repetitive subproblems.
  - Suitable for shallow trees with small input values.

```javascript
export const memoize = (fn) => {
  const cache = {};

  return (...args) => {
    const key = JSON.stringify(args);

    if (key in cache) {
      return cache[key];
    }

    const result = fn(...args);
    cache[key] = result;
    return result;
  };
};
```

```javascript
function fibonacciMaster() { // O(n)
  let cache = {};
  return function fib(n) {
    calculations++;
    if (n in cache) {
      return cache[n];
    } else {
      if (n < 2) {
        return n;
      } else {
        cache[n] = fib(n - 1) + fib(n - 2);
        return cache[n];
      }
    }
  }
}
```

#### Bottom-Up Approach(***Tabulation***)
  - Iterative and often more efficient, especially for large values.
  - Uses known information to compute unknown values.
  - Best for large-scale problems.


```javascript
function fibonacciMaster2(n) { 

  let answer = [0,1]; 

  for ( let i = 2; i <= n; i++) { 
    answer.push(answer[i-2]+ answer[i-1]); 
  } 
  return answer.pop(); 
} 
```


![[fibBottomUpDPForward vs fibBottomUpDPBackward.png]]

### Key dynamic programming patterns


1. **Memoization (Top-Down):**  
- In this approach, you solve the problem recursively, but you store the results of subproblems in a data structure (usually a dictionary or an array) to avoid redundant computations.  
  
2. **Tabulation (Bottom-Up):**  
- This involves solving the problem iteratively, starting from the smallest subproblems and building up to the larger problem. Results are stored in a table (usually a 1D or 2D array).  
  
3. **1D Dynamic Programming:**  
- This pattern involves using a 1D array to store solutions to subproblems. It is often used when the optimal solution to a problem can be expressed in terms of solutions to smaller subproblems.  
  
4. **2D Dynamic Programming:**  
- Similar to 1D dynamic programming, but uses a 2D array to store solutions. This is common when you need to keep track of two changing parameters or indices.  
  
5. **State Compression:**  
- If the state space in a dynamic programming problem is too large, you can use state compression techniques to reduce memory usage. This involves using a more compact representation of states.  
  
6. **Subset Sum Pattern:**  
- Often used in problems where you need to determine if there exists a subset of elements that satisfies a certain condition (e.g., sum of elements equals a target value).  
  
7. **Knapsack Pattern:**  
- Used in problems where you need to optimize the use of limited resources to maximize or minimize a certain value, such as the classic 0/1 Knapsack problem.  
  
8. **Longest Increasing Subsequence (LIS):**  
- This pattern is used in problems where you need to find the longest increasing subsequence in a given sequence of elements.  
  
9. **Matrix Chain Multiplication:**  
- Applied to problems where you need to find the most efficient way to multiply a chain of matrices.  
  
10. **Edit Distance (Levenshtein Distance):**  
- Commonly used in problems where you need to find the minimum number of edits (insertions, deletions, or substitutions) required to transform one string into another.  
  
These patterns serve as general templates for solving specific types of problems using dynamic programming techniques. When faced with a new problem, recognizing which pattern or combination of patterns to apply can significantly simplify the solution process.