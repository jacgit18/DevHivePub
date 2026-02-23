---
tags:
  - languageOverlap
  - math
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Modulo.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 1
dg-publish:
---
Division involves the relationship: dividend / divisor = quotient. For long division, it's expressed as divisor * quotient = dividend. Think of long division as the backend of regular division, introducing remainders. Take, for instance, 228 / 4:

```
4 ⟌ 228
  - 20
--------
   28

```
Here, 4 goes into 22 five times, resulting in 20. The difference in long division is 28, obtained by subtracting 4 * 5 from 22.

```
4 ⟌ 228
  - 20
--------
   28
  - 28
--------
    0 (remainder)
```
Further, 4 goes into 28 seven times with a quotient of 57.

```
4 ⟌ 228
  - 20
--------
   28
  - 28
--------
    0
```
This process results in a remainder of 0.

Modulo essentially mirrors long division. While dividend / divisor = quotient may yield a decimal (e.g., 10 / 3 = 3.333), modulo returns an integer remainder. For instance, 10 % 4 equals 2, indicating that 4 goes into 10 twice (8), leaving a remainder of 2. If the initial division isn't exact, the remainder is derived by subtracting the closest multiple of the divisor from the dividend.


```
   57
__________
4 | 228
   - 0         (4 goes into 2 zero times)
   ------------
      2         (Bring down the next digit)
   ------------
     22         (4 goes into 22 five times)
   ×  5
   ------------
      20        (Subtract 20 from 22, giving us 2)
   ------------
       8        (Bring down the next digit)
   ------------
      28        (4 goes into 28 seven times)
   ×  7
   ------------
       0        (No remainder)
```

This layout includes the quotient 57 at the top and details each step in the long division process.


```
   2
__________
30 | 60
   - 60      (30 goes into 60 two times)
   --------
      0
```

In this case, the quotient is 2, and there is no remainder.

The modulo operation, represented by the `%` symbol, gives the remainder of the division of one number by another. Let's break down the example `30 % 60` step by step:  
  
1. **Divide:** Divide 30 by 60: `30 / 60 = 0.5`.  
2. **Take Integer Part:** Keep only the integer part of the result: `0`.  
3. **Multiply:** Multiply the integer part by the divisor (60): `0 * 60 = 0`.  
4. **Subtract:** Subtract the result from the original number (30): `30 - 0 = 30`.  
  
So, `30 % 60` is equal to `30` because when 30 is divided by 60, the remainder is 30. In general, if `a % b` is performed, the result is the remainder when `a` is divided by `b`. If the result is `0`, it means that `a` is evenly divisible by `b`.