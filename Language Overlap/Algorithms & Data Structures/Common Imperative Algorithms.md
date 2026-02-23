---
tags:
  - MacroCodebaseDecision
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Common Imperative Algorithms
Status: Done
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 1
dg-publish:
---
### [[Imperative Coding]] Example

```javascript
function LengthCheck(inputArray) {
  let result = false;

  if (inputArray && inputArray.length) {
    const trimmedArray = inputArray.trim().split(" ");
    const lastElement = trimmedArray.pop();
    const lastElementLength = lastElement.trim().length;

    result = Boolean(lastElementLength);
  }

  return result;
}

// Example usage
let myArray = "  some text   ";
console.log(checkAltLength(myArray)); // Outputs: true
```


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
```


```Javascript
const removeDuplicates = (nums) => { 
    const unique = new Set(nums); 

    if(unique.size === nums.length) return false; // only false if no duplicates exist 
    
    return true; 
} 

let theNum = [1, 2, 3, 1]; 
console.log(containsDuplicate(theNum))
```


```javascript
// Odd Even Check
let result;
if (number % 2 === 0) {
  result = Math.sqrt(num);
} else {
  result = parseFloat(Math.cbrt(num).toFixed(3));
}
```


```javascript
// Count Characters
const charCounter = (characterString) => {
  let maxRepeat = 0;
  let minRepeat = Infinity;
  let letterFreq = {}, uniqueChars = 0;

  for (let currChar of characterString) {
    if (!letterFreq[currChar]) {
      uniqueChars++;
      letterFreq[currChar] = 1;
    } else {
      letterFreq[currChar]++;
    }
    maxRepeat = Math.max(maxRepeat, letterFreq[currChar]);
    minRepeat = Math.min(minRepeat, letterFreq[currChar]);
  }

  return ['Letter Count: ', letterFreq, `UniqCharacter: ${uniqueChars}, MinRepeatCharacters: ${minRepeat}, MaxRepeatCharacters: ${maxRepeat}`];

// Letter Count:  { c: 2, b: 3, a: 3, e: 1, d: 1 }                                                              

// UniqCharacter: 5, 
// MinRepeatCharacters: 1  
// MaxRepeatCharacters: 3 
```


```javascript
// Generate Array
function generateAlphabetArray() {
  let alphabetArray = [];
  for (let i = 0; i < 26; i++) {
    alphabetArray[i] = 0;
  }
  return alphabetArray;
}

function generateBoardArray(Row, Col, val) {
  let boardArray = [];
  for (let i = 0; i < Row; i++) {
    boardArray[i] = [];
    for (let j = 0; j < Col; j++) {
      boardArray[i][j] = val;
    }
  }
  return boardArray;
}

function handleGivenArray(arr) {
  let newArray = [];
  for (let i = 0; i < arr.length; i++) {
    newArray[i] = arr[i];
  }
  return newArray;
}

// Example usage
let AlphaBet = generateAlphabetArray();

const Row = 9, Col = 9, val = 0;
let boardNestedArray = generateBoardArray(Row, Col, val);

let arr = [
  [0, 1, 1, 1, 1, 1, 1, 1, 1],
  [1, 1, 1, 1, 1, 1, 1, 1, 1],
  [2, 1, 1, 1, 1, 1, 1, 1, 1],
  [3, 1, 1, 1, 1, 1, 1, 1, 1],
  [4, 1, 1, 1, 1, 1, 1, 1, 1],
  [5, 1, 1, 1, 1, 1, 1, 1, 1],
  [6, 1, 1, 1, 1, 1, 1, 1, 1],
  [7, 1, 1, 1, 1, 1, 1, 1, 1],
  [8, 1, 1, 1, 1, 1, 1, 1, 1]
];

let newArray = handleGivenArray([1, 2, 3, 4, 6, 7, 3, undefined]);
```

