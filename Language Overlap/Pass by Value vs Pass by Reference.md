---
tags:
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Pass by Value vs Pass by Reference.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish: false
---
#### Pass by Value (Primitive Types):

```javascript
let a = 10;
let b = 20;
let c = a;  // c gets the value of a

// After modification
a;  // 10
b;  // 20
c;  // 10
```

When dealing with primitive types, a new copy of the value is created, and changes to one variable don't affect others.

#### Pass by Reference (Non-Primitive Types):

```javascript
let a = 10;
let b = 20;
let c = [1, 2];

// Memory address representation
// Variable Value   Address   Value
// a       10      --       --
// b       20      --       --
// c       0x01    0x01     [1,2]

let d = c;  // d shares the same memory address reference

// After push operation
// Variable Value   Address   Value
// c       0x01    0x01     [1,2,3]
// d       0x01    0x01     [1,2,3]

// If we reassign the value of d to a different array
d = [3, 4, 5];  // d gets a new memory address

// Variable Value   Address   Value
// c       0x01    0x01     [1,2,3]
// d       0x02    0x02     [3,4,5]
```

Arrays and objects store a memory address reference. Modifying an array/object affects others sharing the same memory address.

#### Why Identical Arrays Are Not Equal:

```javascript
let a = [1, 2];
let b = [1, 2];

console.log(a === b);  // false
console.log(a == b);   // false

// Memory address representation
// Variable Value   Address   Value
// a       0x01    0x01     [1,2]
// b       0x02    0x02     [1,2]
```

Identical arrays have different memory addresses. Comparisons check for identical values.

#### Importance in Function Parameters:

```javascript
const a = [1, 2];

function addElement(array, element) {
  array.push(element);
}

addElement(a, 3);  // Modifies the original array

console.log(a);  // [1, 2, 3]

// If we reassign array in the function, it creates a new reference
function addElement(array, element) {
  array = [element];  // New memory address
  return array;
}

addElement(a, 3);  // Doesn't affect the original array

console.log(a);  // [1, 2]
```

Understanding pass by value/reference is crucial for handling data modification within functions in JavaScript. Arrays/objects passed to functions are references, allowing modifications to affect the original data.