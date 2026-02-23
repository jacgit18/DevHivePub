---
tags:
  - sortAlgo
  - non-ComparisonSort
  - not-linear-by-Nature
  - not-binary-by-Nature
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Bucket Sort
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[BucketSort.gif]]

Bucket sort is particularly effective when dealing with uniformly distributed input over a specified range. For example, imagine sorting a large set of floating-point numbers ranging from 0.0 to 1.0, distributed uniformly across this range. 

If we were to employ a comparison-based sorting algorithm, such as Merge Sort, Heap Sort, or Quick Sort, we'd be bound by the lower limit of [[Big O#^64043d | Ω]](n log n), which means they can't perform better than n log n in terms of time complexity.

The challenge with applying counting sort is that it relies on keys as indices, and in this scenario, the keys are floating-point numbers.

To tackle this, we turn to bucket sort. The algorithm can be summarized as follows:

- If we assume inserting elements into a bucket takes` O(1) `time (for example, using a linked list to represent each bucket), then steps 1 and 2 will take `O(n)` time.
- Step 4 also takes `O(n) `time because there are n items across all buckets.
- The critical step to analyze is step 3, which takes `O(n)` time on average when the numbers are uniformly distributed.

For more details and implementation, you can refer to the resources linked below:

[What is Bucket Sort](https://www.educative.io/edpresso/what-is-bucket-sort)

[Bucket Sort Algorithm](https://learnersbucket.com/tutorials/algorithms/bucket-sort-algorithm/)


```typescript
function insertionSort(arr: number[]): number[] {
    for (let i = 1; i < arr.length; i++) {
        const current = arr[i];
        let j = i - 1;
        while (j >= 0 && arr[j] > current) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = current;
    }
    return arr;
}

function bucketSort(arr: number[]): number[] {
    const bucketSize = 5; // Set the size of each bucket
    const max = Math.max(...arr);
    const min = Math.min(...arr);

    const bucketCount = Math.floor((max - min) / bucketSize) + 1;
    const buckets: number[][] = new Array(bucketCount).fill([]).map(() => []);

    // Place elements into buckets
    for (const num of arr) {
        const index = Math.floor((num - min) / bucketSize);
        buckets[index].push(num);
    }

    // Sort each bucket and concatenate the results
    const sortedArray: number[] = [];
    for (const bucket of buckets) {
        insertionSort(bucket);
        sortedArray.push(...bucket);
    }

    return sortedArray;
}

// Example usage
const unsortedArray: number[] = [0.42, 0.32, 0.33, 0.52, 0.37, 0.47, 0.51];
const sortedArray = bucketSort(unsortedArray);
console.log(sortedArray); // Output: [0.32, 0.33, 0.37, 0.42, 0.47, 0.51, 0.52]
```

Bucket Sort does not always have to use an Insertion Sort for sorting the elements within each bucket. The choice of sorting algorithm within each bucket can vary depending on the specific implementation and requirements of the Bucket Sort.

The Insertion Sort is a common choice for sorting elements within buckets in many Bucket Sort implementations because it is simple and efficient for small datasets. However, you can use other sorting algorithms as well, depending on factors like the size of the buckets and the characteristics of the data you're sorting.

Some other sorting algorithms that can be used within the buckets include Quick Sort, Merge Sort, or even another Bucket Sort if the range of values within the buckets allows for it.

The choice of sorting algorithm within the buckets should be based on the trade-off between efficiency and simplicity, considering the specific characteristics of the data you are sorting.