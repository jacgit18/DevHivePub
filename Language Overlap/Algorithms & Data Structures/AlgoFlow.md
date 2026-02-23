---
tags:
  - codeFlow
  - time
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a observation about the overall structure of a algorithm at the function scope. Might create a updated mind map
Status: Refinement
Started: 
EditDate: 
Relates: "[[Flow of Control]]"
Peer Reviewed: 0
dg-publish:
---
![[AlgoFlow.png]]

## When Reading Documentation

When delving into documentation about a framework, library, language, technology, or new features, it's essential to understand the underlying "why" behind it's creation. 

## Algorithm Design

### Coding Styles

-   [[Declarative Coding]]
-   [[Imperative Coding]]

![[paradigms.png]]

### High Level Example

Lets your creating a function that iterates through an array, processes its elements, and returns the sum. This approach is compared to simply using `array.reduce` to add the elements, which involves fewer steps and is more abstract.

## Consider Scope

Always keep scope in mind. Solving the right problems and understanding their impact on the broader context is crucial. Precision in problem-solving is valuable for specific tasks, but a more generalized approach has its merits. This balance between precision and generality helps tackle diverse challenges effectively.

## Storing Data in Data Structures

In data structures, **[[Dictionaries]]** and **[[Map#Hashmap vs. Map |Hash Map]]** are valuable tools for efficient data storage, particularly when dealing with values that appear multiple times in an array. This is particularly useful to avoid nested for loops, which can lead to inefficient O(n^2) algorithms.

- **Bubble Sort**: This algorithm repeatedly moves through the list, comparing adjacent elements and swapping them if they are in the wrong order. Worst case runtime is **O(n^2) 

- **Selection Sort**: This algorithm finds the minimum element from the unsorted part of the list and puts it at the beginning. Worst case runtime **O(n^2)

- **Merge Sort**: A more efficient O(n log n) sorting algorithm. Worst case runtime **O(n log(n))

## Algorithmic Approaches
>[!note] Try 
>Separate code flow or read from crud from the steps of an algorithm try this out to see how effective is at breaking down a problem

### Minimum Coin Change Problem

Given a list of coin denominations and a target amount, find the minimum number of coins needed to make that amount using the available denominations.

#### **Brute Force Algorithm**:  
The most straightforward approach.

A Brute Force approach would involve trying all possible combinations of coins to make the amount and finding the minimum combination.

```javascript
function minCoinsBruteForce(coins, amount) {
  function recursiveFind(remainingAmount) {
    if (remainingAmount === 0) return 0;
    if (remainingAmount < 0) return Infinity;

    let minCount = Infinity;

    for (let coin of coins) {
      let count = recursiveFind(remainingAmount - coin);
      if (count !== Infinity) {
        minCount = Math.min(minCount, count + 1);
      }
    }

    return minCount;
  }

  let result = recursiveFind(amount);
  return result === Infinity ? -1 : result;
}
```

#### **Naïve Algorithm**: 
The Naive approach is an improvement over Brute Force, providing a better guess that is often more optimal, but it may still have room for further optimization or some times your best guess can end up being the most optimal choice.

The Naive algorithm in this scenario involves dynamic programming to find the minimum number of coins.

```javascript
function minCoinsNaive(coins, amount) {
  const dp = new Array(amount + 1).fill(Infinity);
  dp[0] = 0;

  for (let i = 1; i <= amount; i++) {
    for (let coin of coins) {
      if (i - coin >= 0) {
        dp[i] = Math.min(dp[i], dp[i - coin] + 1);
      }
    }
  }

  return dp[amount] === Infinity ? -1 : dp[amount];
}
```

#### **Greedy Algorithm**: 
Greedy algorithms are simple, intuitive algorithms that make locally optimal choices at each stage of problem-solving. They are quick and easy to code but may not always produce an overall optimal solution. The simplicity of greedy algorithms makes them suitable for straightforward problems, but they can fall short in complex scenarios.  *Algorithm efficiency OCD*

The Greedy algorithm would involve selecting the largest denomination coin that is less than or equal to the remaining amount, subtracting it from the remaining amount, and repeating this process until the remaining amount becomes zero.

```javascript
function minCoinsGreedy(coins, amount) {
  coins.sort((a, b) => b - a); // Sort in descending order
  let coinCount = 0;
  let remainingAmount = amount;

  for (let coin of coins) {
    while (remainingAmount >= coin) {
      remainingAmount -= coin;
      coinCount++;
    }
  }
  return coinCount;
}
```


#### **Optimal Algorithm**: 
Optimal approaches aim for the most efficient solution based on the problem. While certain algorithm patterns may seem optimal, it depends on the specific problem at hand.

The true optimal solution, often involving sorting. In this scenario the Optimal algorithm would be the same as the Naive algorithm, as it's the most efficient approach for solving the minimum coin change problem.

When tackling coding challenges, especially when implementing advanced patterns, refrain from defaulting to a specific coding pattern in your approach. Take the time to analyze the problem thoroughly, considering various factors, as blindly choosing a pattern may limit your perspective and hinder a comprehensive solution. Like for example assuming every string or array question best approach is either a sliding window or two pointer this is lazy thinking and waste time.
