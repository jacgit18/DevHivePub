---
tags:
  - inPlaceSort
  - sortAlgo
  - binary
  - comparisonSort
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Quick Sort
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[quickSort.gif]]


- **Quick Sort**: It's a divide and conquer algorithm, just like Merge Sort. It's known for being one of the fastest sorting algorithms on average but has some unfavorable worst-case behaviors.

- **Average Runtime and Space Complexity**: Quick Sort has a better average runtime and space complexity compared to Merge Sort for small inputs which is `Ο(n log n)` or *Linearithmic Time*.

- **Pivoting Technique**: Quick Sort employs a pivoting technique to divide the main list into smaller lists. These smaller lists are further divided and sorted using the pivoting technique until the entire list is sorted. This process is a form of divide and conquer.

- **Choosing the Pivot**: In Quick Sort, picking the pivot intelligently based on your list can significantly affect its performance. For example, choosing the first or last item as the pivot can lead to poor performance if the list is not split evenly.

- **Choosing the Pivot Point**: The choice of the pivot point in Quick Sort is somewhat random. If you can't guarantee the quality of the pivot or the data has the potential to be bad, you might want to consider other sorting methods.

- **Usefulness**: Quick Sort and Merge Sort are among the most commonly used sorting algorithms.

- **Space Complexity**: Quick Sort has good space complexity, although not as efficient as Bubble Sort, Insertion Sort, or Selection Sort. It's still better than Merge Sort in this regard.

- **Worst-Case Scenario**: Quick Sort has a worst-case time complexity of O(n^2). To mitigate this, selecting a good pivot point is crucial.

![[quicksort.png]]

```typescript
const numbers: number[] = [99, 44, 6, 2, 1, 5, 63, 87, 283, 4, 0];

function quickSort(array: number[], left: number, right: number): number[] {
  const len: number = array.length;
  let pivot: number;
  let partitionIndex: number;

  if (left < right) {
    pivot = right;
    partitionIndex = partition(array, pivot, left, right);

    // Sort left and right
    quickSort(array, left, partitionIndex - 1);
    quickSort(array, partitionIndex + 1, right);
  }
  return array;
}

function partition(array: number[], pivot: number, left: number, right: number): number {
  let pivotValue: number = array[pivot];
  let partitionIndex: number = left;

  for (let i: number = left; i < right; i++) {
    if (array[i] < pivotValue) {
      swap(array, i, partitionIndex);
      partitionIndex++;
    }
  }
  swap(array, right, partitionIndex);
  return partitionIndex;
}

function swap(array: number[], firstIndex: number, secondIndex: number): void {
  const temp: number = array[firstIndex];
  array[firstIndex] = array[secondIndex];
  array[secondIndex] = temp;
}

// Select first and last index as 2nd and 3rd parameters
console.time("quick");
console.log(quickSort(numbers, 0, numbers.length - 1));
console.timeEnd("quick");
```

