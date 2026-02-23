---
tags:
  - dataType
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses primitive types.
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Primitive.gif]]

In JavaScript, a primitive (primitive value, primitive data type) is data that is not an Object and has no methods.  

Most of the time, a primitive value is represented directly at the lowest level of the language implementation. 

All primitives are *Immutable(pure/no-mutation)*, i.e., they cannot be altered. It is important not to confuse a primitive itself with a variable assigned a primitive value which are *mutable(mutate/impure)*. The variable may be reassigned a new value, but the existing value can not be changed in the ways that objects, arrays, and functions can be altered. 
>[!note] 
>Assignment gives the primitive a new vale it is not being mutated 

## Number 

Number wrapper 
```javascript
let number = new Number()
```

>[!note] 
>Unlike many other programming languages, **JavaScript does not define different types of numbers**, like integers, short, long, floating-point etc.

Long has a higher max value vs int has a low max but takes of less space but the overall space isn't that much

```java
Long
```

## String 
adding ascii values to a sum and comparing math and sub tracing and adding at different times 


"If you choose to use single quotes (') for string delimiters, it allows you to easily include double quotes (\") within your strings when necessary. It's a good practice to use single quotes as the primary string delimiter and double quotes for nested quotations, like this: ' \" '."

or use Backticks, often referred to as template literals
" \` "

"test" 

String wrapper is `String('test "123"')` can convert non string to string like an array 

`new String("test")` is reference to object  

```javascript
let testPrim = "name" 

let testObj = new String(name) 
```

`testPrim.toUpperCase()` the reason this works is because string wrapper since primitives don’t have properties which means no built in methods 

In the background the sting is being typecast to the string wrapper internally 
Something like this `(new String(testPrim)).toUpperCase())   `

```javascript
testPrim.length = 10 
// a temp wrapper is created like above and overrides the length 4 with 10 but since this is a primitive & no props once line is done executing that wrapper is deleted & we default to previous length which is 4 
```

```javascript
testPrim.info = "sample" 
// is undefined because we create a wrapper that gets deleted but there wasn’t a previous value before  
```

>[!note] 
>Using a string method doesn't mutate the string because string is a primitive values which  are immutable . 
```javascript
var bar = "baz"; 
console.log(bar);               // baz 
bar.toUpperCase(); 
console.log(bar);               // baz 
```

>[!note] 
>Assignment gives the primitive a new (not a mutated) value
```javascript
bar = bar.toUpperCase();       // BAZ 
== // compares values and converts type 
=== // only compares types 
```


>[!note] 
>But using an array method mutates the array 
```javascript
var foo = []; 
console.log(foo);               // [] 
foo.push("plugh"); 
console.log(foo);               // ["plugh"] 
```

With testObj  we would print "sample because be it can be mutated but length prop in object can't be so we will get undefined if we try & reassign length " 

Combining prim with wrapper 

```javascript
let tempTest = testObj   + "Test" will be "name Test" 
```



## Boolean 
```
Boolean wrapper is Boolean(true) 

Undefined(means no return value) 

Non-null terminated (C programming language specific)  

Null represents the absence of a value.  

Symbol 
```

> primitive types > array > object 

primitive haves no properties so using a wrapper like the ones above provides these primitives with properties making them objects or object references



## Weird math with numbers and numbers in string

3 + "2" concat = "32" (new string not original since you can mutate string)

instead of 5

5 - "2" = 3 actual subtraction

5 / "2" = 2.5 actual division

5 * "2" = 10 actual multiplication

JavaScript adds left to right