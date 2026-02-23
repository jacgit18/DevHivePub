---
tags:
  - CodebaseDecision
  - CleanPrinciples
  - AlgorithmComponent
  - principles
  - languageOverlap
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses BUD principle.
Status: Done
Started: 
EditDate: 2023-12-03
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[Bud.gif]]

"Bud" is more of a metaphorical term used informally to describe a small, suboptimal part of code that could be improved. While it captures the idea of identifying and addressing small issues in the codebase, it's not a formalized or widely adopted principle like [[DRY]], KISS, and[[SOLID Design Principles | SOLID]] in software engineering.

## Bottlenecks 

A brute force algorithm is to go through the array, starting from the first element, and then search through the remaining elements (which will form the other side of the pair). For each pair, compute the difference. If the difference equals k, increment a counter of the difference.  

The bottleneck here is the repeated search for the "other side" of the pair. It's therefore the main thing to focus on optimizing. 

How can we more quickly find the right "other side"? Well, we actually know the other side of ( x,  ? ) .   It's x  +  k or x  -   k. If we sorted the array, we could find the other side for each of the N elements in O( log N)time by doing a binary search. 

We now have a two-step algorithm, where both steps take O(N  log N) time. Now, sorting is the new bottleneck. Optimizing the second step won't help because the first step is slowing us down anyway.  

We just have to get rid of the first step entirely and operate on an unsorted array. How can we find things quickly in an unsorted array? With a hash table.  

Throw everything in the array into the hash table. Then, to look up if x   +    k or x    -k exist in the array, we just look it up in the hash table. We can do this in O(N) time. 


## Unnecessary Work 

Get rid of unnecessary work like a condition or a loop especially if it doesn't benefit runtime 



## Duplicated Work

Duplicate work in programming refers to having redundant or repeated code, where similar logic is implemented more than once. This can lead to maintenance challenges, increased likelihood of bugs, and decreased code readability. Using TypeScript, let's consider a simple example:

Suppose you have a program that calculates the area of different shapes, and you've implemented a function for calculating the area of a rectangle and a square separately. Here's an example with duplicate work:

```typescript
function calculateRectangleArea(length: number, width: number): number {
    return length * width;
}

function calculateSquareArea(side: number): number {
    return side * side;
}

// Somewhere else in the code...
const rectangleArea = calculateRectangleArea(5, 8);
const squareArea = calculateSquareArea(4);
```

In this example, both `calculateRectangleArea` and `calculateSquareArea` contain similar logic for calculating the area of a shape. To eliminate duplicate work, you could create a more generic function:

```typescript
function calculateArea(sideOrLength: number, width?: number): number {
    if (width !== undefined) {
        // Rectangle
        return sideOrLength * width;
    } else {
        // Square
        return sideOrLength * sideOrLength;
    }
}

// Usage
const rectangleArea = calculateArea(5, 8);
const squareArea = calculateArea(4);
```

Now, the `calculateArea` function handles both rectangles and squares, reducing duplicate work and making the code more maintainable. This way, if you need to update the area calculation logic, you only have to do it in one place.




