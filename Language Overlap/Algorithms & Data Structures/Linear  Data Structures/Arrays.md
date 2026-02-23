---
tags:
  - linear
  - dataStructure
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different aspects of arrays
Status: Refinement
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
An array is a data structure in programming that represents a collection of elements, where each element can be accessed by an index or a key. It is a fundamental and versatile data structure used in many programming languages, including JavaScript, Python, Java, C++, and more.

Arrays are object literals or key value pairs 

Here are some examples in Java and TypeScript:

```java
ArrayList<Object> x = new ArrayList<Object>();
ArrayList[][] = new ArrayList();
```



```typescript
let a: Array<Array<Object>> = new Array<Array<Object>>();
```

Or you can use a shorter syntax:

```typescript
let a: Object[][] = new Array<Object[]>();
```


The code you provided declares a variable `a` and initializes it with an empty 2D array. Here's an explanation of the code:

1. `let a`: This declares a variable named `a`.

2. `Object[][]`: This is the type annotation for the variable `a`. It specifies that `a` is of type "2D array of objects." In TypeScript, `Object` is a generic type that can represent any object. The `[][]` notation indicates a 2D array, meaning an array of arrays.

3. `new Array<Object[]>()`: This part initializes the variable `a`. It creates a new empty array of arrays that can hold objects. It's equivalent to using an empty 2D array.

So, after this line of code, `a` is a variable that holds an empty 2D array capable of storing objects. You can add objects to it by pushing arrays into `a` or by assigning specific values to its elements. For example:

```typescript
a.push([1, 2, 3]); // Push an array with numbers
a.push(["a", "b", "c"]); // Push an array with strings
a[0][0] = { key: "value" }; // Assign an object to a specific element
```

You can work with this 2D array to store and manipulate data, and it can contain elements of any data type as long as they are objects.

### Avoid Arrays For
- Inserting or deleting data, as these operations are O(n) other data structures are better for this.
- In some languages, arrays can be static, with a fixed size, resulting in O(n) time complexity if made dynamic.

## Array Sizes
- Array sizes are often hardcoded and don't dynamically change like in java if you decide to use array of a dynamic array list.
- Resizing an array involves copying data to new memory, which can be inefficient.

## Performance Benefits
- Arrays are fast due to indexing, making them efficient for binary searches and sorting.

## String Handling
- Consider whether strings are ASCII or Unicode, as this distinction can impact certain tasks.
- if you have an array of string and you want to check the sub string of words in array you can use string methods or store current word in variable 

```javascript
const char = substring[right]; 

// If comparing two arrays you can depending on what your asked to do you can  

// Store array value at current index in a variable use for of which gets value with out worrying about index in this case we care about index only for sequence array  

function isValidSubsequence(array: number[], sequence: number[]) { 

let index = 0 

WHEN LOOPing Ask YourSelf IF YOU need to Mess with index 

  for(let num of array) if(num === sequence[index]) index++ 

  return index === sequence.length; 

}
```


## Multidimensional Arrays
- JavaScript doesn't natively provide multidimensional arrays.
- They can be created by defining an array of elements, where each element is itself another array.

## Efficiency Tips
- Consider using hash tables for tracking visited elements in matrix-related questions, similar to memoization.

## Specialized Scenarios
- Fixed-length arrays may be encountered, especially in scenarios like merging intervals.

## Additional Techniques
- Use the spread operator for manipulating strings and storing the result in an array for array destructuring.
- You can shrink an array by reassigning its length to a smaller value.

```javascript
var array = [1, 2, 3, 4, 5, 6]; // length of 6 
array.length = 3 // array now [1,2,3] 
```
## Special Handling with Optional Chaining
- Optional chaining and null coalescing operators can handle cases where arrays may not exist or their length is unknown.

In JavaScript, the optional chaining (`?.`) and nullish coalescing (`??`) operators are used to handle cases where properties or values might be `null` or `undefined`. Here's an example that demonstrates the usage of both operators:

```javascript
// Example object with nested properties
const user = {
  name: 'John',
  address: {
    street: '123 Main St',
    city: 'Cityville',
    // No state property
  },
  preferences: {
    language: 'en',
    // No timeZone property
  },
};

// Using optional chaining and null coalescing operators

// Access a deeply nested property and provide a default value
const state = user.address?.state ?? 'Unknown';
console.log(`State: ${state}`); // Output: State: Unknown (because address.state is not defined)

// Access a nested property that doesn't exist and provide a default value
const timeZone = user.preferences?.timeZone ?? 'GMT';
console.log(`Time Zone: ${timeZone}`); // Output: Time Zone: GMT (because preferences.timeZone is not defined)

// Accessing a defined property
const language = user.preferences?.language ?? 'Unknown';
console.log(`Language: ${language}`); // Output: Language: en (because preferences.language is defined)

// Accessing a property with null value
const nullProperty = user.preferences?.nullProperty ?? 'Default';
console.log(`Null Property: ${nullProperty}`); // Output: Null Property: Default (because preferences.nullProperty is null)
```

In this example:

- We use optional chaining to access nested properties in the `user` object without worrying about potential `null` or `undefined` values.

- The null coalescing operator (`??`) is used to provide default values when a property doesn't exist or is `null`.

- When accessing non-existent properties like `address.state` and `preferences.timeZone`, the default values are used.

- When accessing a defined property like `preferences.language`, its value is used.

- When accessing a property with a `null` value like `preferences.nullProperty`, the default value is used.

Optional chaining cannot be used on a non-declared root object, but can be used with an undefined root object. 

```javascript
myArray = [] 

myArray?.length ? true : false 

// check array position 

  myArrayTwo = [{"id": 1}] 

  myArrayTwo?.[0]?.id ? true : false 

// using null coalescing operator 

  myArrayTwo?.[0]?.id ?? "no property" // returns id value 

  myArrayTwo?.[0]?.name ?? "no property" // returns"no property" 

fakeArray ="[jgjgj]" 

Array.isArray(fakeArray) // returns true 

//if not sure of type 

Array.isArray(myArrayTwo) && myArrayTwo[0]?.id ? true : false 

Array.isArray(myArrayTwo) && myArrayTwo[0]?.name ? true : false
```
