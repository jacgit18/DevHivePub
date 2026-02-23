---
tags:
  - MicroCodebaseDecision
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the most common built in functions used in coding challenge problems.
Status: Done
Started: 
EditDate: 2024-02-23
Relates: 
Peer Reviewed: 1
dg-publish:
---
## Common Math 

### Absolute value
```javascript
Math.abs(-1) = 1 
```
### Rounding Numbers
```javascript
Math.ceil(5.95) = 6 // Up
Math.floor(5.95) = 5 // Down
Math.round(5.95) = 6 // Closest 
```

### Power
```javascript
Math.pow(base,root) = 2^3 = 8 

// Square Root returns root of the value passed 
Math.sqrt(25) = 5 

// Cube Root returns base of the exponent passed 
Math.cbrt(64) = 4^3 = 4 
```
### Max
```javascript
Math.max(value0...valueN) = max value 
```

### Min
```javascript
let min = Infinity                        
Math.min(min...valueN) = min value  
```

## Common [[Primitive Types]]

### Numbers

#### Number Decimal place
```javascript
123.456.toFixed() = 123           
123.456.toFixed(1) = 123.5 automatically rounds 
```

#### Number From String
```javascript
Number.parseFloat('4.567abcdefgh') = 4.567          
Number.parseInt('4.567abcdefgh') = 4 
```

#### Check if Number
```javascript
Number.isNaN('4.567abcdefgh') = false          
```

#### Parity Check
```js
const isEven = (number) => number % 2 === 0;
```


### String 
#### Character to Ascii Code
```javascript
'ab'.charCodeAt(1) = 98
'ab'.charCodeAt() = 97 // default to zero
```

#### Ascii Code to Character
```javascript
String.fromCharCode(98) = 'b'
String.fromCharCode(97,98, ...nums) = 'ab'
String.fromCharCode() = '' // empty string
```

#### Ends With
```javascript
const str1 = 'Cats are the best!';

str1.endsWith('best!') // output: true
str1.endsWith('best', 17)// output: true
// best starts at index 13 but spelling is completed at index 17 or end of string

// 'best' appears at or before the 17th

const str2 = 'Is this a question?';
str2.endsWith('question');// output: false
```

#### Starts With
```javascript
const str1 = 'Saturday night plans';

str1.startsWith('Sat')// output: true
str1.startsWith('Sat', 0); // output: true
str1.startsWith('Sat', 3) // output: false
```


#### Include
```javascript
const sentence = 'The quick brown fox jumps.';

const word = 'fox';

sentence.includes(word) // ouputs true

const mainString = "Hello, how are you?"; 
const searchString = "how"; 
// Check if the mainString includes the searchString starting from position 7 
const includesResult = mainString.includes(searchString, 7); console.log(includesResult); // Output: false
```

#### Repeat string
```javascript
const mood = 'Happy! ';
mood.repeat(3)// output: "Happy! Happy! Happy! "
```

#### Split
```javascript
let name = "Alphonse Gabriel Capone";

.split() 
.split(separator) 
.split(separator, limit) 

let nameArray = name.split(' ') 
["Alphonse", "Gabriel", "Capone"]

const spltNames ={ 
     firstName:  nameArray[0], 
     middleName: nameArray[1], 
     lastName: nameArray[2] 
} 
```

#### Specific Range of SubString
```javascript
const str = 'Mozilla';  
  
console.log(str.substring(1, 3)); // output: "oz"  
  
console.log(str.substring(2)); // output: "zilla"
```

#### Slice
```js
String.slice(beginIndex, endIndex(OPITIONAL) ) 
const str = 'The quick brown fox jumps over the lazy dog.';

console.log(str.slice(31));
// Expected output: "the lazy dog."

console.log(str.slice(4, 19));
// Expected output: "quick brown fox"

console.log(str.slice(-4));
// Expected output: "dog."

console.log(str.slice(-9, -5));
// Expected output: "lazy"
```

#### Trim
```js
' Hello world! '.trim() = "Hello world!" 
' Hello world! '.trimEnd() = " Hello world!" // only end
' Hello world! '.trimStart() = "Hello world! " // only start
```




### [[Regular expression#Regular Expression |Regex]] 

#### Match
```js
String.match(regexp) or .matchAll(regexp) 

const inputString = "Hello World!";
const matches = inputString.match(/[A-Z]/g); // get capital leeters Output: ["H", "W"]
```
#### Match All
```js
const regexp = /t(e)(st(\d?))/g;
const str = 'test1test2';

const array = [...str.matchAll(regexp)];

console.log(array[0]);
// Expected output: Array ["test1", "e", "st1", "1"]

console.log(array[1]);
// Expected output: Array ["test2", "e", "st2", "2"]

/**
[
Array ["test1", "e", "st1", "1"], 

Array ["test2", "e", "st2", "2"]
]
*/
```


```javascript
String.search(regexp) 

String 
.replace(regexp, newSubstr) 
.replaceAll       

String 
.replace(regexp,replacerFunction)  
.replaceAll    

String 
.replace(substr, newSubstr) 
.replaceAll  

String
.replace(substr, replacerFunction) 
.replaceAll
```


```javascript
RegExp.prototype.test()  executes a search for a match between a regular expression and a specified string returns true or false 

const str = 'table football';   
const regex = new RegExp('foo*');                                                           
const globalRegex = new RegExp('foo*', 'g');                           
regex.test(str) 

RegExp.prototype.exec(string)              
const regex1 = RegExp('foo*', 'g');        

const str1 = 'table football, foosball';         
regex1.exec(str1)

```
The string against which to match the regular expression. If the match succeeds, the exec() method returns an array or null if fail 

# Common [[Arrays |Array]] Functions  

### Array to String 
```javascript
Array.join(optionalSeparator) 
```

### Array Sort
in place sort reduces writes
```javascript
Array
.sort() 
.sort(a,b) 
.sort(compareFunc) 
.sort(inlineCompFunc)

let sortedNumsAscending = nums.sort((a, b) => a - b);
a(1) - b(2) = -1  < 0 
// sort smaller before bigger lower value placed first

let sortedNumsDescending = nums.sort((a, b) => b - a);
b(2) - a(1) = 1  > 0 
// sort bigger before smaller higher value placed first 

if a(1) - b(2) || b(2) - a(1) ==== 0 
// keep original order of a and b 
```

### Array at
alt approach to array notation access`array[0]`
The negative index `-2` corresponds to the second-to-last element in the array. 
```js
const array1 = [5, 12, 8, 130, 44];

let index = 2;

array1.at(index) // output: "An index of 2 returns 8"

index = -2;

array1.at(index)// output: "An index of -2 returns 130" 
```

### Array concat
returns a shallow copy
```js 
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
// output: Array ["a", "b", "c", "d", "e", "f"]
```

### Array entries
```js 
const array1 = ['a', 'b', 'c'];

const iterator1 = array1.entries();

console.log(iterator1.next().value);
// output: Array [0, "a"]

console.log(iterator1.next().value);
// output: Array [1, "b"]
```

### Array every
```js 
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold)); // output: true
```

### Array Flat 
```js
const arr1 = [0, 1, 2, [3, 4]];

console.log(arr1.flat());
// output: Array [0, 1, 2, 3, 4]

const arr2 = [0, 1, [2, [3, [4, 5]]]];

console.log(arr2.flat());
// output: Array [0, 1, 2, Array [3, Array [4, 5]]]

console.log(arr2.flat(2));
// output: Array [0, 1, 2, 3, Array [4, 5]]

console.log(arr2.flat(Infinity));
// output: Array [0, 1, 2, 3, 4, 5]
```

### Array Fill
returns mutated array not shallow copy
```js
const array1 = [1, 2, 3, 4];

// Fill with 0 from position 2 until position 4
array1.fill(0, 2, array1.length) // output: Array [1, 2, 0, 0]

// Fill with 5 from position 1
array1.fill(5, 1) // output: Array [1, 5, 5, 5]

array1.fill(6)// output: Array [6, 6, 6, 6]

//start & end Optional 
Array.fill
(value) 
(value, start) 
(value, start, end) 

```

### Array Pop
returns removed last element
```js
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

let test = plants.pop() // output: "tomato"
// ['broccoli', 'cauliflower', 'cabbage', 'kale'];
```

### Array Shift
returns removing first element
```js
const array1 = [1, 2, 3];

const firstElement = array1.shift(); // output: Array [2, 3]
```


### Array push
returns mutated array by appending values at end
```js
const animals = ['pigs', 'goats', 'sheep'];
animals.push('cows')
// output: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
// output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]
```

### Array UnShift
returns array with values appended to the beginning
```js
const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// Expected output: 5

console.log(array1);
// Expected output: Array [4, 5, 1, 2, 3]
```

### Array Slice
returns shallow copy array of `optional` given start and end
```js
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

animals.slice()
// output: Array ["ant", "bison", "camel", "duck", "elephant"]

animals.slice(2)
// output: Array ["camel", "duck", "elephant"]

animals.slice(2, 4)
// output: Array ["camel", "duck"]

animals.slice(1, 5)
// output: Array ["bison", "camel", "duck", "elephant"]

animals.slice(-2)
// output: Array ["duck", "elephant"]

animals.slice(2, -1) 
// output: Array ["camel", "duck"]

```

### Array Splice
```js
const months = ['Jan', 'March', 'April', 'June'];

// Inserts at index 1
months.splice(1, 0, 'Feb');
// output: Array ["Jan", "Feb", "March", "April", "June"]

// Replaces 1 element at index 3
months.splice(3, 1, 'May');
// output: Array ["Jan", "Feb", "March", "May", "June"]

months.splice(3, 2, 'May');
// output: Array ["Jan", "Feb", "March", "May"]

months.splice(3, 1, 'May', 'Dec'); // moves June over
// output: Array ["Jan", "Feb", "March", "May", "Dec", "June"]

months.splice(3, 2, 'May', 'Dec'); // removes June 
// output: Array ["Jan", "Feb", "March", "May", "Dec"]
```


### Array From
returns shallow copy array 
an array of length 26 is generated 65 and + 1 is mapped to each element 
```javascript
const alpha = Array.from(Array(26)).map((e, i) => i + 65);
```

### Array Map
returns shallow copy with update values
```js
const alphabet = alpha.map((x) => String.fromCharCode(x)); // outputs capitalized alphabet [A, B, C, ..., Z]
```

#### Array Includes
```javascript
const array1 = [1, 2, 3];

array1.includes(2) // output: true

const pets = ['cat', 'dog', 'bat'];

pets.includes('cat') // output: true

pets.includes('cat', 1) // output: false

pets.includes('at') // output: false
```

#### Array Reverse 
```javascript
const array1 = ['one', 'two', 'three'];
const reversed = array1.reverse();
// output: "reversed:" Array ["three", "two", "one"]
```

## Array Func with [[Callback]] Params
thisArg is a `optional` param for most built in functions that take in callback functions     

#### Array Filter
This method empowers you to assess if each element in an array meets a specific condition, yielding a new array with the elements that fulfill the test or an empty array if the condition isn't met.
```javascript
const words = ["apple", "banana", "grape", "kiwi"];
const shortWords = words.filter(word => word.length < 6);// Result: shortWords = ["apple", "grape", "kiwi"]

shortWords.forEach((element) => console.log(element));
// "apple"  
// "grape"  
// "kiwi"
```

### Array Find
```javascript
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);
// output: 12

const isLargeNumber = (element) => element > 13;
array1.findIndex(isLargeNumber) // output: 3



const found = array1.findLast((element) => element > 45); // output: 130


const isLargeNumber = (element) => element > 45;
array1.findLastIndex(isLargeNumber)
// output: 3
// Index of element with value: 130
```


#### Array FlatMap
both maps and flattens the result in a single step.
```js
const arr1 = [[1], 2, [1]];

const result = arr1.flatMap((num) => (num === 2 ? [2, 2] : 1));
// output: Array [1, 2, 2, 1]
```

#### Array Reduce 
reduce an array to a single value iterating over each element of the array, applying a callback function that you provide, and accumulates a result. The callback function takes four parameters: accumulator, current value, current index, and the array itself.

```javascript
array.reduce(callback(accumulator, currentValue, currentIndex, array), initialValue);
```

- `callback`: A function that is called once for each element in the array. It takes four parameters:
  - `accumulator`: The accumulated result.
  - `currentValue`: The current element being processed in the array.
  - `currentIndex`: The index of the current element being processed.
  - `array`: The array `reduce` was called upon.

- `initialValue` (optional): An initial value for the accumulator. If not provided, the first element of the array is used as the initial accumulator value.


```javascript
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 15
```

In this example:
- `accumulator` starts at `0` (provided as the second argument to `reduce`).
- The callback function adds each `currentValue` to the `accumulator`.
- The final result is the sum of all elements in the array.

### Object 

#### Entries
Object iterate using for In loop 
```js
const object1 = {
  a: 'somestring',
  b: 42,
};

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// output:
// "a: somestring"
// "b: 42"
```


#### Freeze
```js
const obj = {
  prop: 42,
};

Object.freeze(obj);

obj.prop = 33;
// Throws an error in strict mode

console.log(obj.prop);
// Expected output: 42
```

#### getOwnPropertyNames
```js
const object1 = {
  a: 1,
  b: 2,
  c: 3,
};

Object.getOwnPropertyNames(object1) 
// output: Array ["a", "b", "c"]
```

#### Keys
```js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false,
};

console.log(Object.keys(object1));
// output: Array ["a", "b", "c"]
```

 both methods provide the names of properties belonging directly to an object, but `Object.keys()` is limited to enumerable properties and does not include Symbol keys, while `Object.getOwnPropertyNames()` includes all own properties, regardless of enumerability, and includes Symbol keys.

#### hasOwnProperty
```js
const object1 = {};
object1.property1 = 42;

console.log(object1.hasOwnProperty('property1'));
// output: true

console.log(object1.hasOwnProperty('toString'));
// output: false

console.log(object1.hasOwnProperty('hasOwnProperty'));
// output: false
```

### Set
Iterable object
#### Add
```js
const set1 = new Set();

set1.add(42);
set1.add(42);
set1.add(13);

for (const item of set1) {
  console.log(item);
  // output: 42
  // output: 13
}
```

#### Clear 
```js
const set1 = new Set();
set1.add(1);
set1.add('foo');

set1.size // output: 2

set1.clear();

set1.size// output: 0
```

#### Delete 
```js
const set1 = new Set();
set1.add({ x: 10, y: 20 }).add({ x: 20, y: 30 });

Set {
  { x: 10, y: 20 },
  { x: 20, y: 30 }
}


// Delete any point with `x > 10`.
set1.forEach((point) => {
  if (point.x > 10) {
    set1.delete(point);
  }
});

set1.size // output: 1
```

#### has
```js
const set1 = new Set([1, 2, 3, 4, 5]);

console.log(set1.has(1));
// Expected output: true

console.log(set1.has(5));
// Expected output: true

console.log(set1.has(6));
// Expected output: false
```

### Map
Iterable object
#### ForEach
```javascript
let myMap = new Map();

myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

// Using forEach on Map
myMap.forEach((value, key) => {
  console.log(`Key: ${key}, Value: ${value}`);
});
```

#### Get
```js
const map1 = new Map();
map1.set('bar', 'foo');

map1.get('bar') // output: "foo"
map1.get('baz')// output: undefined
```

#### has
```js
const map1 = new Map();
map1.set('bar', 'foo');

map1.has('bar') // output: true
map1.has('baz') // output: false
```


#### Set
```js
const map1 = new Map();
map1.set('bar', 'foo');
```








