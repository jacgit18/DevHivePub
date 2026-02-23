---
tags:
  - search
  - pattern
  - MicroCodebaseDecision
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different types of search.
Status: Done
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Linear(Sequential) v Binary search.gif]]

## Linear/Sequential Search:

^d39416

Linear search involves going through each element of an array or data structure one by one, starting from the beginning. This method checks each element sequentially to `find the desired value`.

In essence, linear search is a specific application of [[Iteration vs Recursion|linear iteration ]]  where the goal is to find a particular value. However, linear iteration can involve various types of processing, not just searching. Linear search is a common use case for linear iteration, but it's not the only use case.

**Use Cases:**
- Linear search can be applied to any linear data structure, such as an array or a linked list, and is not limited by data order.

**Differences:**
- Linear search is a straightforward sequential approach, examining each element or node exactly once.

**Performance:**
- Linear search is suitable for small data sets.

Certainly! Here's a simple implementation of linear search in JavaScript:

```javascript
function linearSearch(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            return i; 
        }
    }
    return -1; 
}
```

## Binary Search
>Modified binary search is just a variation of the core binary search structure

Binary search, on the other hand, operates by dividing the search interval in half repeatedly. It begins with an interval covering the whole array or sorted data structure. If the value being sought is less than the item in the middle of the interval, the search narrows down to the lower half. If the value is greater, it narrows down to the upper half. This process continues until the value is found or the interval becomes empty. Binary search is highly efficient but requires the data to be sorted.

This is the standard calculation for the middle index in a binary search or any situation where you want to find the midpoint of a range between two indices (`low` and `high`). This formula works well when you are dealing with the current range and want to split it into two halves.

   ```javascript
   let mid = Math.floor((low + high) / 2);
   ```

 The formula used here to calculate the mid point is used in certain situations where you want to find the midpoint in a specific way. It is often employed in algorithms where you need to adjust the calculation to suit the problem's requirements. The `+1` in the formula ensures that the midpoint leans towards the right if the range has an odd number of elements.
 
```javascript
// Binary Search O(log N)
var search = function (nums, target) {
    let lo = 0, hi = nums.length - 1;
    while (lo < hi) {
        let mid = lo + Math.floor((hi - lo + 1) / 2);
        if (target < nums[mid]) {
            hi = mid - 1;
        } else {
            lo = mid;
        }
    }
    return nums[lo] == target ? lo : -1;
};
```

**Use Cases:**
- Binary search is ideal when dealing with sorted data, as it efficiently narrows down the search space.
- Binary search is limited as it can be implemented only on those data structures that have two-way traversal. 

**Differences:**
- Binary search is based on the "divide and conquer" approach, where it repeatedly divides the search space in half.

**Performance:**
- Binary search excels with larger data sets due to its efficient nature.

## Search Types:
A linear search involves iterating through a data structure in a linear manner, examining each element or node once. This search method is not dependent on the shape or structure of the data. If you skip elements or do not examine them all, it is a different type of search. In contrast, binary search is specifically designed for sorted data structures.



