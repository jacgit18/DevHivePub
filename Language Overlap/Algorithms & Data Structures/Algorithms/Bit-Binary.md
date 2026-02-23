---
tags:
  - linear
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what bit binary is.
Status: Refinement
Started: 
EditDate: 2024-02-27
Relates: 
Peer Reviewed: 0
dg-publish:
---
"Bit binary" typically refers to binary representation, which is a linear representation of data. Binary representation uses a base-2 numeral system, where data is represented using only two symbols (usually 0 and 1). In this system, each digit is a power of 2, making it a linear representation of data.

So, "bit binary" is a linear representation and is part of the broader concept of binary representation in computing.


**Bitwise Operators**

Bitwise operators work on binary representations of numbers, treating them as sequences of zeros and ones. They perform operations at the binary level but return standard numerical values in JavaScript. The main bitwise operators in JavaScript include:

- `&` (AND)
- `|` (OR)
- `^` (XOR)
- `~` (NOT)
- `<<` (Left SHIFT)
- `>>` (Right SHIFT)
- `>>>` (Zero-Fill Right SHIFT)

**BigInt Operators**

Most operators that work with the `Number` data type can also be used with `BigInt` values, including arithmetic and comparison operators. However, the unsigned right shift operator `>>>` is not supported for `BigInt`. Some operators may have slight differences in behavior, such as division with `BigInt`, which rounds towards zero.


**Binary Conversion (Base 2)**

To convert a decimal number (e.g., 13) to binary (base 2), follow these steps:

1. Start by focusing on powers of 2: 2^0, 2^1, 2^2, and so on. 

2. Let's take the example of converting 13 to binary. Begin with the highest power of 2, which doesn't exceed the number. In this case, 2^3 (8) is the highest power, so we start there.

3. Move to the next lower power of 2, which is 2^2 (4), and continue until you reach 2^0 (1).

4. For each power of 2, check if it can fit into the remaining number. If it can, mark it with a "1"; otherwise, mark it with a "0."

   - 2^3 (8) goes into 13, leaving a remainder of 5. So, the binary digit is "1."
   - 2^2 (4) goes into 5, leaving a remainder of 1. Another "1."
   - 2^1 (2) doesn't go into 1, so it's marked as "0."
   - 2^0 (1) goes into 1, leaving no remainder. Mark it as "1."

5. Combining these binary digits, we get "1101."

This binary representation corresponds to the decimal number 13. The process involves determining which powers of 2 fit into the number and recording the remainders as binary digits.

The sum of these powers (8 + 4 + 1) is 13, which is consistent with the original decimal value.

Understanding this process is essential for working with binary representation.


https://algodaily.com/lessons/bitwise-operators-and-bit-manipulation-for-interviews  

https://www.purplemath.com/modules/numbbase.htm



**Understanding Binary Addition in Base 10**

Binary addition works similarly to decimal addition but operates in base 2. Here's an example to help you understand:

1. We have two decimal numbers, 123 and 39, that we want to add together.

2. First, we need to convert these numbers into their binary representations:

   - 123 in binary is 1111011.
   - 39 in binary is 100111.

3. To add these binary numbers, start from the right (the least significant bit) and work towards the left (the most significant bit).

4. Add the bits at each position:

   - 1 + 1 = 10 in binary (2 in decimal).
   - 3 in binary is 11.

5. When adding binary numbers, if the result is 2 or greater, carry the extra bit to the next position to the left.

6. Continue adding the carried bit to the next bit:

   - 1 (from the carried bit) + 1 = 10 in binary (2 in decimal).
   - 2 in binary is 10.

7. Repeat the process:

   - 1 (from the carried bit) + 0 = 1 in binary (1 in decimal).
   - 0 in binary remains 0.

8. Finally, complete the addition:

   - 0 (from the carried bit) + 0 = 0.


**Comma Operators**

The comma operator `,` evaluates each of its operands from left to right and returns the value of the last operand. It's useful for creating compound expressions where multiple expressions are evaluated, and the final value is that of the rightmost expression.

Example:
```javascript
let x = 1;
x = (x++, x);
console.log(x); // Output: 2
```

**Arguments Object**

The `arguments` object is an array-like object available within functions that contains the values of the arguments passed to the function. It's especially useful in non-arrow functions to access function arguments.

**Rest Parameters**

Rest parameters allow a function to accept an indefinite number of arguments as an array. It's a way to represent variadic functions in JavaScript, simplifying the handling of multiple arguments within a function.

Example:
```javascript
function sum(...theArgs) {
  let total = 0;
  for (const arg of theArgs) {
    total += arg;
  }
  return total;
}
console.log(sum(1, 2, 3)); // Output: 6
```

Rest parameters make it easier to work with variable numbers of arguments within a function.



