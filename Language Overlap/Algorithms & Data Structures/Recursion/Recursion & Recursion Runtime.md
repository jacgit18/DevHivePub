---
tags:
  - CodebaseDecision
  - timeComplexity
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Recursion Runtime
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[BigORecursion.png]]
# Understanding Recursion

Recursion is a powerful concept in computer science and mathematics. It is defined as a process where an entity is defined in terms of a smaller version of itself. In the realm of programming, any problem that can be tackled recursively can also be solved iteratively with a for loop, and vice versa. 

## Recursive Methods and Time Complexity

Recursive methods offer readability but may lead to large stacks, potentially causing stack overflow errors. However, you can optimize recursive methods to have a time complexity of O(n) by using dynamic programming techniques like [[Memoization]]. Recursive approaches are particularly useful in certain scenarios, such as when searching for solutions, working with trees, converting data into tree structures, sorting, and dynamic programming.

## Different Ways to Implement Recursion

Recursion can be implemented in various ways, each with its own characteristics:

### 1. General Case (Recursive Case)
   - In this case, the method calls itself, often while incrementing through an array (e.g., `i++`).

```javascript
function factorial(n) {
    // Base case: when n is 0 or 1, the factorial is 1
    if (n === 0 || n === 1) {
        return 1;
    } else {
        // Recursive case: n! = n * (n-1)!
        return n * factorial(n - 1);
    }
}

// Example usage:
const n = 5;
const result = factorial(n);
```

### 2. Indirectly Recursive
   - This type of recursion involves a method that calls another method, which eventually results in the original method call.

Example:
```javascript
function doSomething() {
    something();
}

function something() {
    something();
}
```

### 3. Direct Recursion
   - In direct recursion, a function directly calls itself.

Example:
```javascript
function do() {
    do();
}
```

### 4. Tail Recursive Method
   - A tail-recursive method is a type of recursion in which no statements are executed after the return from the recursive call.

```javascript
function factorialTailRecursive(n, result = 1) {
    if (n === 0 || n === 1) {
        return result;
    } else {
        // Multiply the current result by n and pass it to the next recursion
        return factorialTailRecursive(n - 1, n * result);
    }
}

// Example usage:
const n = 5;
const result = factorialTailRecursive(n);
console.log(`The factorial of ${n} is ${result}`);
```

### 5. Infinite Recursion
   - This occurs when a function calls itself endlessly, resulting in an infinite loop.

```javascript
function infiniteRecursion() {
    console.log("This function calls itself endlessly.");
    infiniteRecursion(); // Recursive call without any termination condition
}

// This will result in an infinite loop and eventually a stack overflow error
infiniteRecursion();
```

All recursive approaches involve establishing a recursive case or procedure before reaching a base case. The base case acts as the iteration condition or an if statement that acts as the equivalent of a while loop.

## Divide & Conquer Approach (Think Merge Sort)

Divide and conquer is a powerful technique used in many algorithms, including merge sort, depth-first search, and binary search. The key steps in a divide and conquer approach typically involve breaking a problem into smaller parts, solving each part independently, and then combining the results to obtain the final solution. 

For example, you might have a recursive function for traversing a linked list:

```javascript
function printForwardRec(current) {
    if (current !== null) {
        // Do something with the current node
        current = printForwardRec(current.next);
    }
}
```

The recurrence relation is the essence of the divide and conquer approach, where each step builds upon the previous one to solve the larger problem.

A recurrence relation is a mathematical equation that defines a sequence by specifying how to compute the next term based on the previous term(s). This concept is particularly relevant when dealing with functions like the factorial.

When working with recurrence relations, it can be insightful to start by considering simpler, smaller cases. For instance, let's take the example of calculating the factorial of 4 and visualize the process. By breaking down the problem into smaller steps and understanding the logic behind it, we can derive the base case.

1. fact(4) = 4 * fact(3)
   - fact(3) is computed in the next step.

2. fact(3) = 3 * fact(2)
   - fact(2) is computed in the next step.

3. fact(2) = 2 * fact(1)
   - fact(1) is computed in the next step.

4. fact(1) = 1
   - This is the base case, and it returns 1.

Now, let's multiply these values as we move back up the chain:

- fact(1) = 1
- fact(2) = 2 * 1 = 2
- fact(3) = 3 * 2 = 6
- fact(4) = 4 * 6 = 24

So, the final result is:

fact(4) = 24

To formalize this in the form of a recurrence relation:

- Step 1: fact(n) = n * fact(n-1)
- Step 2: Stop condition - If n === 1, return 1.

This logical breakdown helps us understand the recursive structure and ultimately leads to the base case, which is crucial for solving recursive problems.

## Optimize & Solve Technique: Base Case and Build

The "Base Case and Build" technique involves solving a problem first for a base case (e.g., when `n = 1`) and then building upon that to solve more complex or interesting cases (e.g., when `n = 3` or `n = 4`). This technique is particularly useful in generating recursive algorithms. 

Consider an example of printing all permutations of a string. You can start with the base case of a single character and build permutations for longer strings based on the prior solutions. This pattern often leads to natural recursive algorithms.

```javascript
function permutationsOfString(input) {
    if (input.length === 0) {
        // Base case: When the input is an empty string, return an array with an empty string.
        return [""];
    }

    // Recursive case: For each character in the input, find permutations of the remaining characters.
    const permutations = [];
    for (let i = 0; i < input.length; i++) {
        const currentChar = input[i];
        const remainingChars = input.substring(0, i) + input.substring(i + 1);
        
        const remainingPermutations = permutationsOfString(remainingChars);
        for (const perm of remainingPermutations) {
            permutations.push(currentChar + perm);
        }
    }

    return permutations;
}

// Example usage:
const inputString = "abc";
const result = permutationsOfString(inputString);
console.log("All permutations of '" + inputString + "':");
console.log(result);
```

***Consider a test string abcdefg

1. **Starting with "a"**
   - In the simplest case, when we have just the character "a," the permutation is {"a"}.

2. **Moving to "ab"**
   - When we add "b" to the string, we get {"ab", "ba"}. These are all the possible permutations for "ab."

3. **Progressing to "abc"**
   - Now, we face a more interesting case: "abc." How can we generate permutations for this longer string, given that we already know the permutations for "ab"?
   - To solve this, we take the next character, "c," and insert it into all possible positions within the permutations of "ab."
   - The result is:
     - P("abc") = Insert "c" into all locations of all strings in P("ab").
     - P("abc") = Insert "c" into all locations of {"ab", "ba"}.
     - P("abc") = Merge({"cab", "acb", "abc"}, {"cba", "bca", "bac"}).
     - P("abc") = {"cab", "acb", "abc", "cba", "bca", "bac"}.

4. **General Recursive Algorithm**
   - To develop a general recursive algorithm for generating permutations, we follow a pattern:
     - We "chop off" the last character (in this case, "c") and generate all permutations of the remaining characters ("ab").
     - Once we have the list of permutations for the shorter string ("ab"), we iterate through it.
     - For each string in the list, we insert the "chopped-off" character ("c") into every possible location within the string.

In essence, the "Base Case and Build" approach often leads to natural recursive algorithms when solving problems like generating permutations. It helps us break down complex problems into smaller, more manageable parts and build solutions progressively.

<iframe src="https://www.enjoyalgorithms.com/blog/time-complexity-analysis-of-recursion-in-programming" allow="fullscreen" allowfullscreen="" style="height: 100%; width: 100%; aspect-ratio: 1 / 1;"></iframe>