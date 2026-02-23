---
tags:
  - CodebaseDecision
  - CRUD
  - READ
  - AlgorithmComponent
  - testCases
  - javascript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses conditional logic.
Status: Refinement
Started: 
EditDate: 2024-02-11
Relates: "[[Flow of Control]]"
Peer Reviewed: 0
dg-publish:
---
Using not equal might be better than saying not equal or equal to in conditional statement for problem-solving in code because it's fewer lines of code and conditions but the same result 

Too many conditional statements approach doesn't address test cases very well 

A better approach may bring up a lot of test cases and doesn't addresses them so if you are thinking about a lot of conditional statements your approach might not be the best 

Conditional coding avoid else or else if and to many nested conditions  

always create a condition a to exit at begging of loop or method if variable doesn't meet a certain condition having more than one return is ok to do and can make code more efficient 

if you have a lot of conditions break your code down into helper functions to keep that main condition smaller and more readable 

If using other data structures in problem your conditional statements may end up focusing on that new data structure or both depending on the scenario 

loop through length and doing consecutive action on iteration means another loop that is nested 

Recursion can have multiple base cases, you can take in one param and convert into multiple variables divide and conquer especially tree and may use map 


### isLooselyEqual ==

Exclude type check

Converts types & compare value


### isStrictlyEqual===

Includes type check in comparison


Use triple equal sunset checks type and value

### Value Comparison Operators

In javascript, the <mark style="background: #BBFABBA6;">==</mark> operator does the type conversion of the operands before comparison, whereas the <mark style="background: #BBFABBA6;">===</mark> operator compares the values and the data types of the operands. The <mark style="background: #FFF3A3A6;">Object.is()</mark> method determines whether two values are the same value: <mark style="background: #FFF3A3A6;">Object.is(value1, value2)</mark>.

Object.is() is not equivalent to the <mark style="background: #BBFABBA6;">==</mark> operator. The <mark style="background: #BBFABBA6;">==</mark> operator applies various coercions to both sides (if they are not the same type) before testing for equality (resulting in such behavior as <mark style="background: #BBFABBA6;">"" ==</mark> false being true), but Object.is() doesn't coerce either value.

Object.is() is also not equivalent to the === operator. The only difference between Object.is() and === is in their treatment of signed zeros and NaN values. The === operator (and the == operator) treats the number values -0 and +0 as equal but treats NaN as not equal to each other.


## Conditional shortcuts 

```javascript
// check if value exist 

address && action like console.log  

same as if(address) console.log 

if else shortcut  

return (name || 'no name') 

Low-cost merge of arrays 

arr1 =[1,2] 

arr2 =[3,4 

arr1.push.apply(arr1,arr2) 

Default value with || 

let ogName = 'jake' 

let ogAge =null 

let name = ogName || 'fake name'  // jake 

let age = ogAge || 99 // 99

```


## Short circuit evaluation 
Short-circuit evaluation is a programming language feature where logical expression evaluation stops as soon as the result is determined. This depends on the logical operator used: `&&` (logical AND) or `||` (logical OR).

1. **Logical AND (`&&`):** If the left operand is `false`, the right operand is not evaluated, as both must be true for the entire expression to be true.

```javascript  
let result = false && someFunction(); // someFunction() won't be called  
```  
  
2. **Logical OR (`||`):** If the left operand is `true`, the right operand is not evaluated, as only one true operand is needed for the entire expression to be true.

```javascript  
let result = true || someFunction(); // someFunction() won't be called  
```  
  
Short-circuit evaluation optimizes efficiency, particularly with costly operations. For `&&`, put the most likely false condition first; for `||`, put the most likely true condition first. This decision involves a trade-off between readability and optimization.

### Optional Chaining Operator uses  Null Coalescing Operator ??

Check if data is in object very useful when dealing with Api  

example: 
```javascript
const person = { 

name: joe, 

age: 23 

vehicle:{ 

} 

} 

// Ternary version 

const vehicleYear = person.vehicle ?  person.vehicle.year : undefined 

//Optional Chaining Operator  version both properties not in object but if they were you would get vale of them 

const vehicleYear = person.vehicle? .year  // should be this 

const vehicleYear = person.vehicle? .year  ?? 1980 // you can set a default value if it doesnt exist 

const warrantyDate = person.vehicle? .warranty?.expireDate   

//can be used with methods to 

person.vehicle? .miles() 

person.vehicle? .miles?.() // check if it is a function


console.log([1]?.length ? true : false);

```