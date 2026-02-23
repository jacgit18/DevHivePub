---
tags:
  - bestPractices
  - sortAlgo
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses best practices for sorting.
Status: Done
Started: 2023-11-01
EditDate: 2024-02-27
Relates: "[[All Sorts of Sorts]]"
Peer Reviewed: 0
dg-publish: false
---
Sorting algorithms do not always need to return `void`. The return type of a sorting algorithm depends on the specific programming language and the design of the algorithm. Sorting algorithms can have different return types:  
  
1. **Void**: In many cases, sorting algorithms modify the input data in place, and therefore, they return `void`, meaning they do not return any value but directly change the order of the elements in the input data.  
  
2. **New Array/Collection**: Some sorting algorithms create a new sorted array or collection and return that sorted data, leaving the original data unchanged. In this case, the return type is typically the same as the type of the elements being sorted. 
>[!note] 
>This is typically better practice but it seems when it comes to sorting. I try and do this instead of modify original value in general outside of sorting this relates to this note [[Shallow Copy and Deep Copy(clone)]]
  
3. **Boolean**: Sorting algorithms can return a boolean value to indicate whether the sorting operation was successful or not.  
  
The choice of return type depends on the design and requirements of the algorithm and the specific use case in a given programming context.  
  
  
Returning a new array is a different approach to sorting that can be a better practice in some situations, depending on your specific use case. Here are some considerations for when it might be better to return a new array instead of sorting in place:  
  
1. **Immutability**: Returning a new array preserves the immutability of the original data, which can be important in situations where you need to keep the original data intact.  
  
2. **Functional Programming**: In functional programming, immutability is often preferred. Returning a new sorted array fits well with functional programming principles.  
  
3. **Parallelism**: Some sorting algorithms can be parallelized more easily when returning a new array, as multiple threads or processes can work on different parts of the data simultaneously.  
  
4. **Comparative Sorting**: In cases where the sorting algorithm is based on comparisons and the original data should not be modified, returning a new array makes sense.  
  
However, there are trade-offs. Returning a new array consumes additional memory, which can be a concern for large datasets. In contrast, in-place sorting algorithms modify the existing array, which can save memory but alter the original data.  
  
The choice between in-place sorting and returning a new array depends on your specific requirements and constraints. It's essential to consider factors like memory usage, performance, and the desired behavior of your program when making this decision.

