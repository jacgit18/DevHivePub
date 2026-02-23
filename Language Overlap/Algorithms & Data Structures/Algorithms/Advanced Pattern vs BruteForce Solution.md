---
tags:
  - CodingProblem
  - MicroCodebaseDecision
  - pattern
  - timeComplexity
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses how a advanced algorithm pattern isn't also the most optimal approach.
Status: Done
Started: 
EditDate: 2024-02-27
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Algorithm Pattern are good for improving runtime 

>[!important] 
>But doesn't always do so, sometimes a brute force approach can be more optimal depending on the problem


```javascript
function sortedSquaredArray(array) {
  let newArray = [];
  let start = 0;
  let end = array.length - 1;
  let cures = array.length - 1;

  while (end >= start) {
    let leftSq = array[start] ** 2;
    let rightSq = array[end] ** 2;

    if (leftSq > rightSq) {
      newArray[cures] = leftSq;
      start++;
    } else {
      newArray[cures] = rightSq;
      end--;
    }
    cures--;
  }

  return newArray;
}

console.log(sortedSquaredArray([1,2,3]))

```

```javascript

function sortedSquaredArrayTwo(array) {
  let newArray = [];

  for (let num of array) {
    newArray.push(num ** 2);
  }

  return newArray.sort((a, b) => a - b);
}

console.time("test");
console.log(sortedSquaredArray([1, 2, 3, 5, 6, 8, 9]));
console.timeEnd("test");

console.time("testTwo");
console.log(sortedSquaredArrayTwo([1, 2, 3, 5, 6, 8, 9]));
console.timeEnd("testTwo");
```
