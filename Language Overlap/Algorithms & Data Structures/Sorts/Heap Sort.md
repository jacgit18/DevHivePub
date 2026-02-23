---
tags:
  - sortAlgo
  - comparisonSort
  - not-linear-by-Nature
  - not-binary-by-Nature
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Heap Sort
Status: Refinement
Started: 
EditDate: 2024-02-27
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[HeapSort.gif]]


The heapsort algorithm utilizes the heap data structure. Here's a refined summary of the process:

1. **Building the Max-Heap**: Start with an input array A[1..n], where n = A.length. Create a max-heap by using the "BUILD-MAX-HEAP" operation.

2. **Exchanging Maximum Element**: The maximum element is at the root (A[1]). Move it to its final position by exchanging it with A[n].

3. **Restoring Max-Heap Property**: Discard node n from nothe heap (decrement A.heap-size). The children of the root remain max-heaps, but the new root might not. To restore the max-heap property, use the "MAX-HEAPIFY" function on A[1..n-1].

4. **Repeat**: Repeat the process for max-heaps of decreasing size from n-1 down to a heap of size 2.

For more details and implementation, you can refer to the resources you provided:

- [Stack Abuse](https://stackabuse.com/heap-sort-in-javascript/)
- [GitConnected](https://levelup.gitconnected.com/heapsort-for-javascript-newbies-598d25477d55)
- [Vhudyma's Blog](https://vhudyma-blog.eu/2020-09-22-algorithms-heap-sort-in-javascript/)


```typescript
function swap(input: number[], index_A: number, index_B: number): void {
  const temp: number = input[index_A];
  input[index_A] = input[index_B];
  input[index_B] = temp;
}

function max_heapify(array: number[], index: number, length: number): void {
  let left: number = 2 * index; // left child index
  let right: number = 2 * index + 1; // right child index
  let maximum: number;

  if (right < length) {
    // Right child exists?
    if (array[left] >= array[right]) {
      // Compare children to find the maximum
      maximum = left;
    } else {
      maximum = right;
    }
  } else if (left < length) {
    // Left child exists?
    maximum = left;
  } else {
    return; // No children, return
  }

  if (array[index] < array[maximum]) {
    // Check if the largest child is greater than the parent
    swap(array, index, maximum); // Swap both
    max_heapify(array, maximum, length); // All over again
  }
}

function heap_sort(array: number[]): number[] {
  const length: number = array.length;
  for (let i: number = Math.floor(length / 2) - 1; i >= 0; i--) {
    max_heapify(array, i, length); // Build the max heap
  }
  for (let i: number = length - 1; i >= 0; i--) {
    swap(array, 0, i); // Delete the root element
    max_heapify(array, 0, i); // Build max heap again
  }
  return array;
}

const array: number[] = [8, 4, 7, 1, 3, 5];
console.log(`Array before: ${array}`);
console.log(`Array after: ${heap_sort(array)}`);
```

