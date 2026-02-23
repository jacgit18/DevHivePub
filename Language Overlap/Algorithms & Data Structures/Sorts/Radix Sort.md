---
tags:
  - sortAlgo
  - non-ComparisonSort
  - not-linear-by-Nature
  - not-binary-by-Nature
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Radix Sort
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
<iframe title="Radix Sort | GeeksforGeeks" src="https://www.youtube.com/embed/nu4gDuFabIM?feature=oembed" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>



**Improving Sorting Time Complexity without Comparisons**

When it comes to optimizing sorting algorithms, it's possible to enhance time complexity without relying on comparisons. This is where non-comparison sorting methods like radix sort come into play.

Radix Sort is a` non-comparative`  sorting algorithm meaning  that sorting takes a unique route by distributing elements into different "buckets" based on individual digits or characters at different positions within the elements. It's often used to sort integers, strings, or other data with a well-defined radix (base). Here's how it works:


1. Determine the maximum number of digits or characters in the given elements. This determines the number of passes the algorithm will make.

2. Start with the rightmost (least significant) digit or character and move to the leftmost (most significant) one.

3. In each pass, distribute the elements into 10 buckets (0 to 9) based on the digit or character at the current position.

4. Collect the elements from the buckets in order, combining all the buckets to form a new sorted list.

5. Repeat this process for each position, moving from right to left.

6. After processing all the positions, you'll have a fully sorted list.

Radix sort offer entirely different approaches to sorting data. Unlike comparison-based sorting, which determines the order of numbers by continuously asking whether one element is greater than another, 

These methods leverage the binary representation of numbers in our computer systems, operating with zeros and ones to efficiently organize data. However, it's important to note that these non-comparison sorts are most effective with integers within a limited range.

For example, if you have a set of numbers ranging from zero to 100, a small range, these methods can significantly expedite the sorting process. They are specifically tailored for numeric data due to the way numbers are stored in memory.

Non-comparative sorting algorithms like [[Counting Sort]] and radix sort are primarily suitable for fixed-length integers, and they can outperform the typical` O(n log n)` time complexity of comparison-based sorts.  Radix sort has `best/average/worst ` runtime of  **[[Big O#^64043d | Ω(nk)]]**,  **[[Big O#^68b727 | Θ(nk)]]** **[[Big O#^93b0ef | O(nk)]]**, and space complexity of `O(n+k)`.  Additionally, you may encounter another non comparative sorting method called [[Bucket Sort]]. 


Radix Sort is stable, which means it maintains the relative order of equal elements. It can be used for sorting integers, strings, or other data types with a radix (e.g., binary, decimal, or characters in a string). However, it has some limitations, such as its efficiency depends on the number of digits or characters, and it may not be the best choice for large data sets or data with widely varying lengths.



```typescript
// Function to find the maximum number in an array
function findMax(arr: number[]): number {
    let max = arr[0];
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}


function radixSort(arr: number[]): number[] {
    const max = findMax(arr);
    const maxLength = max.toString().length;

    for (let digitPlace = 1; digitPlace <= maxLength; digitPlace++) {
        // Initialize 10 buckets (0-9)
        const buckets: number[][] = Array.from({ length: 10 }, () => []);

        // Distribute the elements into buckets based on the current digit place
        for (const num of arr) {
            const digit = Math.floor((num / Math.pow(10, digitPlace - 1)) % 10);
            buckets[digit].push(num);
        }

        // Collect the elements from the buckets in order
        arr = ([] as number[]).concat(...buckets.reduce((acc, bucket) => acc.concat(bucket), []));
    }

    return arr;
}


// Example usage
const unsortedArray: number[] = [170, 45, 75, 90, 802, 24, 2, 66];
const sortedArray = radixSort(unsortedArray);
console.log(sortedArray); // Output: [2, 24, 45, 66, 75, 90, 170, 802]

```

