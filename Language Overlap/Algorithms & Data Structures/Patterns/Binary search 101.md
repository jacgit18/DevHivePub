---
tags:
  - looping
  - traversal
  - search
  - binary
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses in and outs about Binary search
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
## Key Decisions in Binary Search

Binary search is a powerful algorithm, but making the right decisions is crucial to its success. A single misstep in these decisions can break your code. To avoid such pitfalls, I've developed a set of rules that ensure consistency and predictability in all edge cases.

### Question to ask yourself
- Do I use left or right mid? 
- Do I use < or <= , > or >=? 
- How much do I shrink the boundary? is it mid or mid - 1 or even mid + 1 ? 


### 1) Choice of Boundaries (lo and hi)

The initial boundary, represented by 'lo' and 'hi', is fundamental in binary search. Typically, we set it to encompass all elements in the array:

```javascript
let lo = 0, hi = nums.length - 1;
```

However, keep in mind that the boundary defines the range of elements to search from. It should include all potential answers. For some problems, like LeetCode 35 (inserting into an array), you may need to adjust the boundary:

```javascript
let lo = 0, hi = nums.length;
```

### 2) Calculating the Midpoint (mid)

Calculating the midpoint is another critical aspect of binary search, but it can lead to overflow with large numbers. Here are different ways to calculate 'mid', from worst to best:

```javascript
let mid = Math.floor((lo + hi) / 2); // Worst, prone to overflow
let mid = lo + Math.floor((hi - lo) / 2); // Better but still has potential issues
let mid = (lo + hi) >>> 1; // The best, but less intuitive
```

Additionally, when dealing with an even number of elements, you have the choice of selecting the left or right midpoint. As we'll discuss later, choosing the wrong one can lead to an infinite loop:

```javascript
let mid = lo + Math.floor((hi - lo) / 2); // Left/lower midpoint
let mid = lo + Math.floor((hi - lo + 1) / 2); // Right/upper midpoint
```

### 3) Shrinking the Boundary

I aim to keep the logic as simple as possible, typically using a single pair of 'if...else' statements. The rule of thumb here is to use logic that allows you to exclude the 'mid' element. For example:

```javascript
if (target < nums[mid]) {
    hi = mid - 1; // Exclude mid
} else {
    lo = mid; // Include mid
}
```

You can also rewrite the logic as follows:

```javascript
if (target > nums[mid]) {
    lo = mid + 1; // Exclude mid
} else {
    hi = mid; // Include mid
}
```

### 4) While Loop

I always employ the 'while (lo < hi)' loop. It ensures that the loop only exits when 'lo' and 'hi' point to the same element, which I know always exists.

### 5) Avoiding Infinite Loops

Selecting the wrong midpoint and using incorrect shrinking logic can lead to infinite loops. Let's address this with an example:

```javascript
let mid = lo + ((hi - lo) / 2); // Bad! Should use the right/upper midpoint

if (target < nums[mid]) {
    hi = mid - 1;
} else {
    lo = mid;
}
```

In situations with only two elements remaining in the boundary, the logic falls into the 'else' statement, leading to an infinite loop.

Choose the midpoint and shrinking logic to ensure that, each time, at least one element is excluded:

```javascript
let mid = lo + ((hi - lo + 1) / 2); // Bad! Should use left/lower midpoint

if (target > nums[mid]) {
    lo = mid + 1; // Exclude mid
} else {
    hi = mid; // Include mid
}
```

If your binary search gets stuck, consider whether the boundary is shrinking correctly when there are only two elements left.

In summary, my rules for successful binary search are:

- Include all possible answers when initializing 'lo' and 'hi'.
- Avoid mid-calculation overflows.
- Use shrinking logic that excludes 'mid'.
- Choose the correct midpoint and shrinking logic.
- Always consider the case when only two elements remain.

```javascript
var search = function (nums, target) {
    let lo = 0,
        hi = nums.length - 1;
    while (lo < hi) {
        let mid = lo + Math.floor((hi - lo + 1) / 2);
        if (target < nums[mid]) {
            hi = mid - 1;
        } else {
            lo = mid;
        }
    }
    return nums[lo] == target ? lo : -1;
}
```

These guidelines will help you approach binary search with confidence and precision.