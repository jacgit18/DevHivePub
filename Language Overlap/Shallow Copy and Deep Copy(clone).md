---
tags:
  - pureFunction
  - impureFunction
  - mutability
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses shallow and deep copy.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Shallow and Deep Copy.gif]]
Shallow copy involves creating a new object with an exact copy of values from the original. If the object contains references to other objects, only the memory addresses are copied.

```javascript
let xArray = [1, 2, 3];
let yArray = xArray; // stores memory reference

let zArray = [...yArray, 10]; // results in [1, 2, 3, 10]
```

**Object.assign(target, source) for Shallow Copy:**

```javascript
const tArray = Object.assign([], zArray); // creates a new array
tArray === zArray // returns false different memory reference 
```

**Nested Objects in Shallow Copy:**

```javascript
let jArray = [1, 2, 3];
jArray.push([4, 5, 6]);
// Results in [1,2,3,[4,5,6] ]  

let vArray = [...jArray];
// Results in [1, 2, 3, [4, 5, 6]]

vArray[4].push(7); 
// jArray and vArray both get 7 pushed in them along with an increase of there array size 

// So this ends up being [1, 2, 3, [4, 5, 6, 7]]
```

**Array.from() and slice() for Shallow Copy:**

```javascript
const shallowCopy = Array.from(jArray);
```

**Object.freeze() for Shallow Freeze:**

```javascript
const obj = { "first": 44, "sec": 12, "third": { "a": 1, "b": 2 } };
Object.freeze(obj); // stops any changes to object also prevents its prototype from being changed. freeze() returns the same object that was passed in. 
obj.third.a = 8; // attempts to reassign a to 8, but it won't happen due to Object.freeze()
```

## Deep Copy
> "Depending on specific code requirements and best practices, opting for a deep copy is often preferred to mitigate potential unintended side effects associated with shallow copies. Deep copies create independent duplicates of the entire data structure, ensuring changes in one copy do not impact the original, providing a more robust solution in scenarios where data immutability and isolation are crucial." could do this with a helper function 

"A deep copy copies all fields, and makes copies of dynamically allocated memory pointed to by the fields. A deep copy occurs when an object is copied along with the objects to which it referenced." In a deep copy, not only are the values of the fields copied, but if those fields contain references to other objects, the deep copy ensures that new copies of the referred objects are created as well. This extends recursively to all nested objects, resulting in a completely independent copy of the original structure with no shared references.

Various libraries, such as lodash, ramda, and others, incorporate built-in functionality for deep copying.

```javascript
const Score = { "first": 44, "sec": 12, "third": { "a": 1, "b": 2 } };

const newScore = JSON.parse(JSON.stringify(Score));

Score === newScore // references different memory so false which we want 

// this doesn't works with Dates, function, undefined, Infinity, RegExps, Maps, 

Sets, Blobs, FileLists, ImageDates, and other complex data types 
```

**Better Custom Deep Clone Function:**

```javascript
const deepClone = (obj) => {
    if (typeof obj !== "object" || obj === null) return obj;
    const newObj = Array.isArray(obj) ? [] : {};
    for (let key in obj) {
        const value = obj[key];
        newObj[key] = deepClone(value);
    }
    return newObj;
};

let testArray = [44,22] 
let testObj = { "first": 44, "sec": 12, "third": { "a": 1, "b": 2 } };

const newA = deepClone(testArray);
testArray === newA //false good 

const objay = deepClone(testObj);
objay === testObj //false good 

```

**Function Example with Deep Clone:**
if you have a function with shallow copy that makes it impure deep copy fixes that 

```javascript
const pure = (array, score = 87, deepClone) => {
    const newArray = deepClone(array);
    newArray.push(score);
    return newArray;
};

const impure = (array, score = 87) => {
    array.push(score);
    return array;
};
```

## Conclusion

Shallow copies share references, making them susceptible to unintended mutations, while deep copies create independent copies, preventing such issues. Choose the appropriate method based on your needs.

