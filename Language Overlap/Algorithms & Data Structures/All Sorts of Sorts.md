---
tags:
  - time
  - sortAlgo
  - preProcesing
  - postProcessing
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the world of sorting algorithms.
Status: Refinement
Started: 
EditDate: 2024-02-10
Relates: "[[Big O]]"
Peer Reviewed: 0
dg-publish:
---
## Array Sorting Algorithms

|Algorithm|Time Complexity|   |   |Space Complexity|
|---|---|---|---|---|
||Best|Average|Worst|Worst|
|[Quicksort](http://en.wikipedia.org/wiki/Quicksort)|`Ω(n log(n))`|`Θ(n log(n))`|`O(n^2)`|`O(log(n))`|
|[Mergesort](http://en.wikipedia.org/wiki/Merge_sort)|`Ω(n log(n))`|`Θ(n log(n))`|`O(n log(n))`|`O(n)`|
|[Timsort](http://en.wikipedia.org/wiki/Timsort)|`Ω(n)`|`Θ(n log(n))`|`O(n log(n))`|`O(n)`|
|[Heapsort](http://en.wikipedia.org/wiki/Heapsort)|`Ω(n log(n))`|`Θ(n log(n))`|`O(n log(n))`|`O(1)`|
|[Bubble Sort](http://en.wikipedia.org/wiki/Bubble_sort)|`Ω(n)`|`Θ(n^2)`|`O(n^2)`|`O(1)`|
|[Insertion Sort](http://en.wikipedia.org/wiki/Insertion_sort)|`Ω(n)`|`Θ(n^2)`|`O(n^2)`|`O(1)`|
|[Selection Sort](http://en.wikipedia.org/wiki/Selection_sort)|`Ω(n^2)`|`Θ(n^2)`|`O(n^2)`|`O(1)`|
|[Tree Sort](https://en.wikipedia.org/wiki/Tree_sort)|`Ω(n log(n))`|`Θ(n log(n))`|`O(n^2)`|`O(n)`|
|[Shell Sort](http://en.wikipedia.org/wiki/Shellsort)|`Ω(n log(n))`|`Θ(n(log(n))^2)`|`O(n(log(n))^2)`|`O(1)`|
|[Bucket Sort](http://en.wikipedia.org/wiki/Bucket_sort "Only for integers. k is a number of buckets")|`Ω(n+k)`|`Θ(n+k)`|`O(n^2)`|`O(n)`|
|[Radix Sort](http://en.wikipedia.org/wiki/Radix_sort "Constant number of digits 'k'")|`Ω(nk)`|`Θ(nk)`|`O(nk)`|`O(n+k)`|
|[Counting Sort](https://en.wikipedia.org/wiki/Counting_sort "Difference between maximum and minimum number 'k'")|`Ω(n+k)`|`Θ(n+k)`|`O(n+k)`|`O(k)`|
|[Cubesort](https://en.wikipedia.org/wiki/Cubesort)|`Ω(n)`|`Θ(n log(n))`|`O(n log(n))`|`O(n)`|


<body style="margin: 0; overflow: hidden;"> 
<iframe src="https://www.hackerearth.com/practice/algorithms/sorting/radix-sort/visualize/" style="width: 100%; height: 75vh; border: none;"></iframe> </body>

> [!important] On Interview you may be asked a question more so then actually implement also you can mention that you would use one sort or the other with reason why depending if it is relevant to problem your doing. 

### In-Place Sorting  
When sorting is done in place, it means that the original input, such as an array, is modified directly during the sorting process, without creating a new sorted array. This relates to [[Shallow Copy and Deep Copy(clone)]] also examples of this type of sort are Bubble, Insertion, Selection, Heap, and Cyclic sort.

### Merge Sort:

[[Merge sort]]is a reliable sorting algorithm that falls under the category of  `divide and conquer `sorts. It is known for its consistent and linear time complexity.

In the case of Merge Sort, the time complexity is typically `O(n log(n))`. However, Quick Sort can be more space-efficient, but it can have an unfavorable runtime in worst-case scenarios due to its pivot technique, which may lead to `exponential` time complexity.

If you're concerned about worst-case scenarios, Merge Sort is a safer choice. But if you're sorting data in memory on your machine and space efficiency is a priority, Merge Sort can be more resource-intensive. For large data structures, Merge Sort is often a better choice. It's a stable sort and can be adapted for linked lists and large datasets stored on slower media like disks.

### Quick Sort:
[[Quick Sort]] , on the other hand, is known for its space efficiency and good cache locality. It's an in-place sorting algorithm, meaning it doesn't require additional storage space for sorting. In the worst-case scenario, Quick Sort has a time complexity of` O(n^2)`, but this can be improved with techniques like randomized Quick Sort or careful pivot selection.

Quick Sort is particularly efficient for smaller arrays or datasets and has good cache locality, making it faster in some cases, especially in a virtual memory environment.

### Heap Sort
alternatively you can use [[Heap Sort]] but it is a little slower than quicksort but you don't have to worry about worst-case and it has a better space complexity than merge sort 

### [[Key Base Attributes of  Grokking Algorithm patterns#^b310e2 |Cyclic Sort]]
A sort under grokking algorithms


# Wont Really Use

## Practice Sorts

### [[Bubble sort]] & [[Selection sort]]

Practice with bubble and selection sort to understand basics don't use bubble or selection sort in your code or interview

Bubble insertion and selection sort are typically the worst in terms of runtime which is exponential or `O(n^2) `but when it comes to insertion if best case which is small amounts of data then it can become O(n) or Ω(n) which is linear time
### [[Insertion sort]]

use insertion sort for small inputs that are partially sorted to get the LINEAR TIME `O(n)` and it uses little space  

## Non-Comparison Sorts

### [[Bucket Sort]]

Bucket sort is mainly useful when dealing with numbers in different ranges

## [[Counting Sort]]

Counting sort also deals with numbers in different ranges

### [[Radix Sort]](Not likely to be on interview)

Radix Sort + Counting Sort are used for integers in a restricted range


**Don't forget to Keep [[_Sort Implementation Focus]] in mind**

# Summary

- Use Merge Sort when reliability and worst-case performance are important, especially for  dealing with larger arrays or datasets.
- Choose Quick Sort when space efficiency and speed for smaller datasets are your priorities.
- Merge Sort is preferred for linked lists and scenarios where stability is crucial.
- Quick Sort is preferred for arrays and can be optimized to be as efficient as Merge Sort in certain cases.
- Both these sorts are usually implement [[Recursion & Recursion Runtime| Recursively]]

**Sorting Method:**

- Quick sort is considered an internal sorting method, where data is sorted directly in main memory.

- In contrast, merge sort is an external sorting method, typically used when the data to be sorted cannot fit entirely in memory and requires auxiliary storage.

**Stability:**

- Merge sort is a stable sorting method, ensuring that two elements with equal values maintain their original order as they were in the input unsorted array.

- Quicksort, by default, is unstable in this regard but can be modified to achieve stability through code adjustments.

**Preferred For:**

- Quicksort is often the preferred choice for sorting arrays.

- Merge sort, on the other hand, is well-suited for sorting linked lists.


## Sorting Nature
> [!important] This was an observation I made and was curious about sorting algorithms and how they iterate through arrays or different data structures "linear" and "binary" can be used to classify sorting and searching algorithms based on their operation or strategy, with linear algorithms working through the data one element at a time and binary algorithms employing a divide and conquer approach or binary decisions.
### Linear Sorting Algorithms: 
These are algorithms that involve comparing and moving elements one at a time through the entire input data set to arrange them in the desired order. Examples of linear sorting algorithms include:

1. **Bubble Sort:** It repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. This process continues until the entire list is sorted.

2. **Insertion Sort:** It builds a sorted portion of the list one element at a time by shifting larger elements to the right until they are in the correct order.

3. **Selection Sort:** It repeatedly selects the minimum element from the unsorted part and puts it at the beginning.

### Binary Sorting Algorithms:
These algorithms employ a "divide and conquer" strategy, breaking the data into smaller parts and performing operations based on binary decisions. Examples of binary sorting algorithms include:

1. **Merge Sort:** It divides the unsorted list into n sub-lists, each containing one element, and then repeatedly merges sub-lists to produce new sorted sub-lists until there is only one sub-list remaining.

2. **Quick Sort:** It chooses a "pivot" element and partitions the list into two sub-lists, according to whether they are less than or greater than the pivot. It then recursively sorts the sub-lists.

**Binary Search:** While not a sorting algorithm, binary search is a searching algorithm that operates on sorted data by repeatedly dividing the search space in half. It is considered a "binary" operation because it makes binary decisions to narrow down the search space.


## Non Comparative Sorts Nature 

1. **Heap Sort:** Heap Sort is not a "linear" or "binary" sort in the sense of linear vs. binary operations. It is typically categorized based on its time complexity. Heap Sort is a comparison-based sorting algorithm with a time complexity of O(n log n), making it more efficient than quadratic time complexity sorts like Bubble Sort or Insertion Sort.

2. **Radix Sort:** Radix Sort is a non-comparison-based sorting algorithm that sorts data based on the individual digits or characters of the elements. It is not specifically categorized as "linear" or "binary." Radix Sort has a linear time complexity, O(nk), where "n" is the number of elements, and "k" is the number of digits or characters in the input values. It is efficient for certain types of data, such as integers with a limited number of digits.

3. **Counting Sort:** Counting Sort is another non-comparison-based sorting algorithm that operates by counting the occurrences of each element in the input and then reconstructing the sorted output. It is also not categorized as "linear" or "binary." Counting Sort has a linear time complexity, O(n+k), where "n" is the number of elements, and "k" is the range of possible input values. Counting Sort is highly efficient for a small range of integers.

4. **Bucket Sort:** Bucket Sort is another non-comparison-based sorting algorithm that distributes elements into a fixed number of buckets and sorts each bucket individually. Similar to Radix Sort and Counting Sort, it's not classified as "linear" or "binary." Bucket Sort's time complexity can vary depending on the number of buckets used and the distribution of data but can be considered a linear time complexity algorithm in many cases.

In general these sorting algorithms don't fit into the "linear" or "binary" categories when classifying them based on their core operation. They are better categorized based on their time complexity and approach, whether they are comparison-based or non-comparison-based, and whether they are stable or unstable sorts. 




