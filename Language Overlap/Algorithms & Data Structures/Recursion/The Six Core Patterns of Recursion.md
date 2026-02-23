---
tags:
  - looping
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Patterns of Recursion
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Recursion.gif]]

## Iteration and Recursion

As you may know, problems that can be solved using loops can also be tackled using recursion, and vice versa. While recursion may not always be the most convenient approach, it can prove invaluable in specific scenarios, particularly when we need to reference previously processed items in our algorithm.

## Subproblems and Decomposition

Recursion is a powerful technique that allows us to break down complex problems into simpler, more manageable subproblems. You can observe this strategy in various recursive problem-solving approaches. Consider, for example, the Fibonacci problem, where the mathematical definition of the Fibonacci sequence itself is inherently recursive. Similarly, the Towers of Hanoi problem requires decomposing the main problem into its subproblems to find a solution.

## Selection and Dynamic Programming

Selection is a fundamental pattern that frequently arises in Recursion and Dynamic Programming. This pattern involves evaluating all possible solutions and selecting those that meet specific conditions. Take the 0–1 Knapsack Problem, for instance. While it's a classic dynamic programming problem, let's approach it from a recursive standpoint. The brute force solution for this problem involves generating all conceivable combinations and choosing the most optimal answer among them.

```java
List<List<Integer>> combinations(int[] n) {
    List<List<Integer>> results = new LinkedList();
    combinations(n, 0, results, new LinkedList<Integer>());
    return results;
}

void combinations(int[] n, int i, List<List<Integer>> results, List<Integer> path) {
    if (i == n.length) {
        results.add(path);
        return;
    }
    
    // Find all the combinations that exclude the current item
    // Find all the combinations that include the current item
    List<Integer> pathWithCurrent = new LinkedList(path);
    pathWithCurrent.add(n[i]);
    
    combinations(n, i+1, results, path);
    combinations(n, i+1, results, pathWithCurrent);
}
```

## Ordering and Permutations

The ordering pattern, as a permutation of the Selection pattern, focuses on exploring different orders of values. Calculating all permutations of a given set of elements is a classic problem. For instance, problems like Bogosort, which involves generating permutations and determining the sorted one, or finding all palindromes from a set of characters.

```java
List<List<Integer>> permutations(Set<Integer> n) {
    List<List<Integer>> results = new LinkedList();
    permutations(n, results, new LinkedList<Integer>());
    return results;
}

void permutations(Set<Integer> n, List<List<Integer>> results, List<Integer> path) {
    if (n.isEmpty()) {
        results.add(path);
        return;
    }

    for (int i : n) {
        n.remove(i);
        List<Integer> pathWithCurrent = new LinkedList(path);
        pathWithCurrent.add(i);
        permutations(n, results, pathWithCurrent);
        n.add(i);
    }
}
```

## Divide and Conquer

Divide and conquer is a technique where we divide a problem into smaller parts, solve each part separately, and then combine their results to obtain the final solution. This approach is the foundation of many algorithms like merge sort, depth-first search, and binary search.

As an example, consider splitting a string at every possible point:

```java
List<String> parentheses(String s) {
    if (s.length() == 1) {
        List<String> result = new LinkedList<String>();
        result.add(s);
        return result;
    }

    List<String> results = new LinkedList<String>();
    for (int i = 1; i < s.length(); i++) {
        List<String> left = parentheses(s.substring(0, i));
        List<String> right = parentheses(s.substring(i, s.length()));

        for (String s1 : left) {
            for (String s2 : right) {
                results.add("(" + s1 + s2 + ")");
            }
        }
    }
    return results;
}
```