---
tags:
  - bit
  - binary
  - memory
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses
Status: Done
Started: 
EditDate: 2024-03-04
Relates: "[[Bit-Binary]]"
Peer Reviewed: 0
dg-publish:
---
**Bits and Binary Representation:**

Bits, short for binary digits, are fundamental units of information that alternate between 0 and 1, forming binary numbers. A bit can represent either 0 or 1, and when combined, they create binary numbers. For instance, 10 is represented as 2 bits, and at maximum, it can be 8 bits, as seen in the example 10100011.

In binary format:
- 1 is represented as 00000001
- 2 is represented as 00000010
- 3 is represented as 00000011
- 4 is represented as 00000100

**Fixed-Width Integer:**

A fixed-width integer is represented by a set number of bits. For example, a 32-bit integer comprises 32 bits (4 bytes), and a 64-bit integer consists of 64 bits (8 bytes). The representation of the number 1 in a 32-bit integer is visually separated into bytes as follows:

```
00000000 00000000 00000000 00000001
```

Regardless of an integer's size, its fixed-width representation contains a constant number of bits. Operations on fixed-width integers involve a constant number of bit manipulations, as the integer is composed of a fixed number of bits.

**Memory:**

Memory is the foundational layer of computing where all data is stored. Key points in coding interviews related to memory include:

- Data is stored in memory in bytes and bits.
- Bytes in memory can "point to" other bytes, storing references to additional data.
- The machine's memory is bounded, emphasizing the importance of limiting algorithm memory usage.
- Accessing a byte or a fixed number of bytes (e.g., 4 or 8 bytes for 32-bit and 64-bit integers) is considered an elementary operation, akin to a single unit of operational work.