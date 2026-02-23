---
tags:
  - sortAlgo
  - binary
  - comparisonSort
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Merge sort
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[MergeSort.gif]]


- **Merge Sort**: This sorting technique is based on the divide and conquer method and is known for its worst-case time complexity of `Ο(n log n)` or *Linearithmic Time*, making it highly respected.

- **Space Complexity**: Merge sort has a space complexity of `O(n),` which means it uses additional memory for sorting.

- **Worst-Case Scenarios**: If you're concerned about worst-case scenarios and need a reliable sorting algorithm, Merge sort is a good choice.

- **In-Memory Sorting**: If you need to sort data in memory on your local machine and are worried about space complexity, Merge sort may be less efficient due to its higher space requirements.

- **External Sorting**: For scenarios where you have huge files that can't fit entirely in memory and need an external sorting process, Merge sort becomes suitable because space complexity matters less in such cases.


![[mergeSort.png]]



```typescript
const numbersortMerge: number[] = [99, 44, 6, 2, 1, 5, 63, 87, 283];

function mergeSort(array: number[]): number[] {
  if (array.length === 1) {
    return array;
  }
  // Split Array into right and left
  const length: number = array.length;
  const middle: number = Math.floor(length / 2);
  const left: number[] = array.slice(0, middle);
  const right: number[] = array.slice(middle);

  return mergeHelper(mergeSort(left), mergeSort(right));
}

function mergeHelper(left: number[], right: number[]): number[] {
  const result: number[] = [];
  let leftIndex: number = 0;
  let rightIndex: number = 0;
  while (leftIndex < left.length && rightIndex < right.length) {
    if (left[leftIndex] < right[rightIndex]) {
      result.push(left[leftIndex]);
      leftIndex++;
    } else {
      result.push(right[rightIndex]);
      rightIndex++;
    }
  }
  return result.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
}

console.time("mergeHelper");
console.log(mergeSort(numbersortMerge));
console.timeEnd("mergeHelper");
```

