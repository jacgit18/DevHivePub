---
tags:
  - MacroCodebaseDecision
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Common Declarative Algorithms
Status: Done
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
### [[Declarative Coding]] Example

**Array Map Method:** is apart of array wrapper class don't confuse it with map data structure.

```javascript
const LengthCheck = (inputArray) => {
  return Boolean(
    inputArray?.length &&
    inputArray
      .trim()
      .split(" ")
      .pop()
      .trim()
      .length
  );
};

// Example usage
let myArray = "  some text   ";
console.log(altLengthCheck(myArray)); // Outputs: true
```


```javascript
const deepClone = (obj) => {
  if (typeof obj !== "object" || obj === null) return obj;

  return Array.isArray(obj)
    ? obj.map(deepClone)
    : Object.fromEntries(Object.entries(obj).map(([key, value]) => [key, deepClone(value)]));
};
```


```javascript
const removeDuplicates = (nums) => {
  return Array.from(new Set(nums));
};

let theNum = [1, 2, 3, 1];
let uniqueNums = removeDuplicates(theNum);
console.log(uniqueNums);
```



```javascript
// Odd Even Check
const result = (number % 2 === 0)
  ? Math.sqrt(num)
  : Math.cbrt(num).toFixed(3);
```


```javascript
const charCounter = (characterString) => {
  const letterFreq = [...characterString].reduce((acc, currChar) => {
    acc[currChar] = (acc[currChar] || 0) + 1;
    return acc;
  }, {});

  const uniqueChars = Object.keys(letterFreq).length;
  const minRepeat = Math.min(...Object.values(letterFreq));
  const maxRepeat = Math.max(...Object.values(letterFreq));

  return ['Letter Count: ', letterFreq, `UniqCharacter: ${uniqueChars}, MinRepeatCharacters: ${minRepeat}, MaxRepeatCharacters: ${maxRepeat}`];
};

console.log(charCounter('cbaebabacd'));
```


```javascript
function generateArrays() {
  // Generate Array
  let AlphaBet = Array(26).fill(0);

  const Row = 9, Col = 9;
  const val = 0;
  const boardNestedArray = Array.from(Array(Row), () => Array(Col).fill(val));

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

  let newArray = [1, 2, 3, 4, 6, 7, 3, undefined];

  return { AlphaBet, boardNestedArray, arr, newArray };
}

// Example usage
const { AlphaBet, boardNestedArray, arr, newArray } = generateArrays();
console.log(AlphaBet);
console.log(boardNestedArray);
console.log(arr);
console.log(newArray);
```


-1 (Out of bounds), 0, 1, 2, 3, 4, 5, 6, 7 (doesn't exist) need to push

**Note:**
You can't just access the column since you would be accessing indexes from multiple arrays. Access both row & column using `matrix[currRow].length` or `curCol >= matrix.length`.

