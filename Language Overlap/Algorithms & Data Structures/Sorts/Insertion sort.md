---
tags:
  - inPlaceSort
  - WontReallyUse
  - sortAlgo
  - linear
  - comparisonSort
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Insertion sort
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[InsertionSort.gif]]

This is an in-place comparison-based sorting algorithm. Here, a sub-list is maintained which is always sorted. For example, the lower part of an array is maintained to be sorted. An element that is to be 'inserted in this sorted sub-list, has to find its appropriate place, and then it has to be inserted there. Hence the name, insertion sort.  
  
The array is searched sequentially and unsorted items are moved and inserted into the sorted sub-list (in the same array). This algorithm is not suitable for large data sets as its average and worst-case complexity are of Ο(n2), where n is the number of items.  
  
Well, insertion sort should be used with only a few items if your input is small or items are mostly sorted. It's really really fast.  
  
It uses very little space and most importantly it's really easy to implement in code.