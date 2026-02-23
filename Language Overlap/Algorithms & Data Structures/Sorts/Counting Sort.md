---
tags:
  - sortAlgo
  - non-ComparisonSort
  - not-linear-by-Nature
  - not-binary-by-Nature
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Counting Sort
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[CountingSort.gif]]


Counting Sort is a non-comparative integer sorting algorithm that works efficiently for a range of input values. with the ability to surpass the efficiency of `O(n log n)` sorting algorithms. It is a stable sorting algorithm, which means that it preserves the relative order of equal elements in the sorted output. Counting Sort is particularly useful when you have a limited range of input values, making it more efficient than comparison-based sorting algorithms like Quicksort or Merge Sort for such cases.

Here's how Counting Sort works:

1. Determine the range of input values: To use Counting Sort, you need to know the minimum and maximum values within the input array. Let's call these values "min" and "max."

2. Create a counting array: Create an auxiliary array called the "counting array" with a size equal to the range of input values. In most cases, this array is initialized with all zeros.

3. Count the occurrences: Loop through the input array and, for each element, increment the corresponding position in the counting array. This step counts how many times each value appears in the input array.

4. Calculate cumulative counts: Modify the counting array to store the cumulative count of elements. Each element at index i in the counting array will represent the number of elements in the input array that are less than or equal to i.

5. Reconstruct the sorted array: Create a new output array of the same size as the input array. Then, iterate through the input array in its original order. For each element, find its position in the counting array (which represents its sorted position) and place it in the output array at that position.

6. Finalize the sorted array: After processing all the elements in the input array, the output array will contain the sorted version of the input array.

Here's a implementation of Counting Sort:

```typescript
function countingSort(arr: number[]): number[] {
    const max = Math.max(...arr);
    const min = Math.min(...arr);

    // Create a counting array to store the frequency of each value
    const countArray: number[] = new Array(max - min + 1).fill(0);

    // Count the occurrences of each value in the input array
    for (const num of arr) {
        countArray[num - min]++;
    }

    // Build the sorted array from the counting array
    const sortedArray: number[] = [];
    for (let i = 0; i < countArray.length; i++) {
        for (let j = 0; j < countArray[i]; j++) {
            sortedArray.push(i + min);
        }
    }

    return sortedArray;
}

// Example usage
const unsortedArray: number[] = [4, 2, 2, 8, 3, 3, 1];
const sortedArray = countingSort(unsortedArray);
console.log(sortedArray); // Output: [1, 2, 2, 3, 3, 4, 8]
```


Counting Sort has a time complexity of O(n + k), where "n" is the number of elements in the input array, and "k" is the range of input values (max_val - min_val + 1). It is a linear-time sorting algorithm and can be extremely efficient when the range of input values is small. However, it is not suitable for sorting non-integer values or for large ranges of values.