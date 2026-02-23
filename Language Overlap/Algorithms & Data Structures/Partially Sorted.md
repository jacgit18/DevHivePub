---
tags:
  - dataStructure
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses Partially Sorted arrays.
Status: Done
Started: 2024-02-19
EditDate: 
Relates: "[[Types of Arrays]]"
Peer Reviewed: 0
dg-publish:
---
A partially sorted array is not necessarily considered only a rotated array; there are other types of partially sorted orders as well. Partially sorted arrays can exhibit different patterns, and rotation is just one possibility. Here are a few examples of partially sorted arrays:  
  
1. **Rotated Array:**  
- Elements are shifted circularly. For example, `[3, 4, 5, 1, 2]` is a rotated version of `[1, 2, 3, 4, 5]`.  
- Probably only one were Binary search can be applied were you want to get lowest value at the beginning to access it.  
  
2. **Nearly Sorted Array:**  
- Elements are mostly in sorted order, but a few elements are out of place. This can happen, for instance, when a small number of elements are swapped.  
  
```plaintext  
[2, 1, 3, 4, 5]  
```  
  
3. **Wave Array:**  
- Elements alternate between being smaller and larger than their neighbors.  
  
```plaintext  
[1, 3, 2, 5, 4]  
```  
  
4. **Zigzag Array:**  
- Similar to a wave, but the alternation is not strict, allowing for sequences like "up-down-up" or "down-up-down."  
  
```plaintext  
[1, 3, 2, 5, 4, 7, 6]  
```  
  
5. **Local Minima/Maxima Array:**  
- Elements have local minima or maxima, meaning they are smaller or larger than their neighbors.  
  
```plaintext  
[1, 5, 3, 2, 4]  
```  
  
6. **Block-Sorted Array:**  
- The array can be divided into blocks, and each block is sorted, but the overall order may not be strict.  
  
```plaintext  
[2, 1, 4, 3, 6, 5]  
```  
  
The term "partially sorted" is a broad concept, and it can encompass various arrangements that are not strictly sorted or reversed. Each type of partially sorted array might require a specific approach or algorithm depending on the problem at hand. Understanding the specific characteristics of the partially sorted order is crucial for designing efficient algorithms that leverage the partially sorted nature of the array.