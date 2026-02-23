---
tags:
  - MicroCodebaseDecision
  - casting
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses type casting.
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
## Widening Casting or Implicit(Js) conversion/Coercion

^3799d1

Widening casting is done automatically when passing a smaller size type to a larger size type:

Implicit type ***Coercion*** happens when the compiler or runtime automatically converts data types. JavaScript is loosely typed language and most of the time operators automatically convert a value to the right type.
#### ***Widening Casting*** (automatically) 
converting a smaller type to a larger type size
> byte -> short -> char -> int -> long -> float -> double

This is the simplest form of type casting, where a primitive data type with a smaller range is automatically converted to a larger data type. Widening primitive conversions are performed implicitly by the Java compiler.

> Meaning converts one way double converts int  but int might not convert double


if you add a string to a num it will convert to string

```javascript
let x = 8

x=x +"" // gives you string basically concatenation


// if you subtract you get number so depending on what operator you news will determine the type of output

let bool = Boolean(3)  any number outside of 0 will be true other wise 0 is false

null and undefined is also false

let varchar = Number("11226 abc") typeOf will return NaN

let varchar = ParseInt("11226 abc") typeOf will return number

let varchar = parseInt("a1226 abc") typeOf will return NaN
```
### Example this might be slightly different in JavaScript

```Java
Public class Main{

	Public static void main(String[]args){

		Int myInt =9;

		double myDouble =myInt;// Automatic casting: int to double

		System.out.println(myInt);// Outputs 9

		System.out.println(myDouble);// Outputs 9.0

	}

}
```

## Narrowing Casting or Explicit(js) conversion/Casting 

^13a274

Narrowing casting must be done manually by placing the type in parentheses in front of the value:

Type casting means transferring data from one data type to another by explicitly specifying the type to convert the given data to. Explicit type casting is normally done to make data compatible with other variables. Examples of typecasting methods are <mark style="background: #FFF3A3A6;">parseInt(), parseFloat(), toString()</mark>. This is  done by the developer (or) programmer

#### ***Narrowing Casting*** (manually)
converting a larger type to a smaller size type
double -> float -> long -> int -> char -> short -> byte

> Narrowing conversions may result in data loss or truncation if the value being cast cannot be represented in the target data type.


<mark style="background: #FFF3A3A6;">The most common conversion is String, Numeric, Boolean, & Symbol conversions</mark>

```javascript
//whenever you don't want to do something with a number store it in a string like phone number or zip code
let string = String(11226) 

let num = Number("11226") 

console.log(typeof string); // number
```

### Example this might be slightly different in JavaScript

```Java
Public class Main{

	Public static void main(String[]args){

		Double myDouble =9.78d;

		int myInt =(int)myDouble;// Manual casting: double to int

		System.out.println(myDouble);// Outputs 9.78

		System.out.println(myInt);// Outputs 9

	}

}
```


In TypeScript, you can cast types using the `as` keyword or angle brackets `<>`. To cast a value to a different type, you might write it like this:

```typescript
let value: any = "Hello, World!";
let length: number = value as string; // or <string>value;

// Now, value is cast to a string and assigned to length
```


```typescript
let value: any = "42";
let length: number = parseInt(value as string); // or <string>value

// Now, value is cast to a string and then parsed as an integer
```

This code will correctly cast the string "42" to the number 42.

##  [[Boxing and Unboxing]]
- Java also supports automatic conversion between primitive types and their corresponding wrapper classes, known as boxing and unboxing.
- Boxing is the process of converting a primitive value to its corresponding wrapper class (e.g., `int` to `Integer`).
- Unboxing is the reverse process, converting a wrapper class object to its corresponding primitive value.
- Java performs boxing and unboxing automatically when needed, allowing seamless conversion between primitives and their wrapper classes.

## [[Boxing and Unboxing#Reference Type Casting Example |Reference Type Casting]]
   - Reference type casting is used when working with objects and class hierarchies. It is applicable to classes and interfaces in Java. Reference type casting can be performed between two types related by inheritance or implementation.
	   - Upcasting ([[#^3799d1 |implicit]] casting): It involves casting an object to one of its superclasses or implemented interfaces.
		   - Upcasting is safe and can be done implicitly without an explicit cast.
		   - For example, casting a `Circle` object to a `Shape` object, where `Circle` extends `Shape`.

	   - Downcasting ([[#^13a274 |explicit]] casting): It involves casting an object to one of its subclasses.
		   - Downcasting requires an explicit cast and may result in a `ClassCastException` if the object being cast is not actually an instance of the target class.
		   - For example, casting a `Shape` object to a `Circle` object, where `Shape` is a superclass of `Circle`.



It's important to note that type casting should be used carefully and only when necessary. Inappropriate or incorrect casting can lead to runtime errors and unexpected behavior. It's always recommended to perform type checks (`instanceof` operator) before attempting downcasting to ensure the cast is valid and avoid `ClassCastException` at runtime.





