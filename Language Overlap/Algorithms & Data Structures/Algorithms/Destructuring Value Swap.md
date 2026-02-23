---
tags:
  - AlgorithmComponent
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses swapping values in an array.
Status: Done
Started: 
EditDate: 2024-02-29
Relates: "[[Arrays]]"
Peer Reviewed: 0
dg-publish:
---
```javascript
// Initialize two arrays
let arrOne = [1, 2, 3, 4, 5];
let arrTwo = [10, 9, 8, 7, 6];

// Swapping the first values of each array
[arrOne[0], arrTwo[0]] = [arrTwo[0], arrOne[0]];

console.log("Swapping the first values of arrOne and arrTwo:");
console.log("arrOne:", arrOne);
console.log("arrTwo:", arrTwo);

// Number swap using destructuring
let word = "97999";
[arrOne[4], word[1]] = [word[1], arrOne[4]];

console.log("\nSwapping a number in arrOne with a character in 'word':");
console.log("arrOne:", arrOne);

// Initialize an object
let objL = { 1: "A", 2: "B", 3: "C", 4: "D" };

// Swap the values associated with keys 1 and 2 in the object
[objL[1], objL[2]] = [objL[2], objL[1]];

console.log("\nSwapping values associated with keys 1 and 2 in objL:");
console.log("objL[1]:", objL[1]); // Outputs "B"
console.log("objL[2]:", objL[2]); // Outputs "A"
console.log("objL:", objL);
```

