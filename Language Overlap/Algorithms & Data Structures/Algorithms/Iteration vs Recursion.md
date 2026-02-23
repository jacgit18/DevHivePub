---
tags:
  - looping
  - traversal
  - search
  - linear
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Linear Iteration vs Linear Recursion vs Binary Iteration vs Binary Recursion
Status: Done
Started: 
EditDate: 2024-02-27
Relates: "[[Iterating vs Traversing]]"
Peer Reviewed: 0
dg-publish:
---
![[many Ways.gif]]


## Linear iteration

Linear iteration is a broader concept that refers to the process of sequentially visiting or processing each item in a collection/Data Structure, typically from the first item to the last, in a linear order.  It is not limited to searching for a specific value like a [[Linear search vs Binary search#^d39416 |Linear Search]]; it can involve various operations on each item in the collection, such as printing, modification, or computation.  

```javascript
function linearIteration(arr) {
  for (let index = 0; index < arr.length; index++) {
    // Process the element at the current index
    console.log(arr[index]);
  }
}

const myArray = [1, 2, 3, 4, 5];
linearIteration(myArray);
```

## Linear Recursion

While it's not a common approach, you can implement linear iteration using recursion. Here's an example of how you can do this by creating a recursive function to iterate over an array of elements and process each element one by one:  
  
```javascript  
function linearIterationRecursive(arr, index) {  
// Base case: When the index is equal to the length of the array, stop the recursion.  
if (index === arr.length) {  
return;  
}  
  
// Process the element at the current index  
console.log(arr[index]);  
  
// Recursive call to process the next element  
linearIterationRecursive(arr, index + 1);  
}  
  
const myArray = [1, 2, 3, 4, 5];  
linearIterationRecursive(myArray, 0);  
```  
  
In this example, the `linearIterationRecursive` function takes an array `arr` and an `index` as parameters. It processes the element at the current index and then makes a recursive call to process the next element by incrementing the index. The base case checks if the index is equal to the length of the array, and if so, it stops the recursion.  
  
It's important to note that while this code demonstrates a recursive approach for linear iteration, it's not the most efficient or common way to achieve linear iteration. Using a "for" loop is a more straightforward and efficient choice for linear iteration in most cases.

## Binary Iteration

```javascript
const searchIter = (nums, target) => {
    let lo = 0;
    let hi = nums.length - 1;
    while (lo <= hi) {
        let mid = lo + Math.floor((hi - lo + 1) / 2);
        if (target < nums[mid]) {
            hi = mid - 1; // index
        } else {
            lo = mid; // index
        }
    }
    return nums[lo] == target ? lo : -1;
};
```


## Binary Recursion

```javascript
const searchRec = (nums, target) => {
    return findTarget(nums, target, 0, nums.length - 1);
};

const findTarget = (nums, target, start, end) => {
    if (start > end) {
        return -1;
    }
    const mid = Math.floor((end - start) / 2) + start;
    if (nums[mid] == target) {
        return mid;
    } else if (nums[mid] > target) {
        return findTarget(nums, target, start, mid - 1); // Adjust the end index to mid - 1
    } else {
        return findTarget(nums, target, mid + 1, end); // Adjust the start index to mid + 1
    }
};
```







