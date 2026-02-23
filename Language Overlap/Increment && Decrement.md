---
tags:
  - looping
  - codeFlow
  - languageOverlap
  - CodingProblem
  - MicroCodebaseDecision
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses incrementing and decrementing in business logic.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: "[[Flow of Control]]"
Peer Reviewed: 0
dg-publish:
---
### Pre Increment (++x) 1 to 10

The pre-increment operator (++x) increments the value and returns it immediately. So, for values 1 through 10:

1, 2, 3, 4, 5 ..., 10

```javascript
let a = 2; // a = 3
let b = ++a; // b = 3 (immediate increment)
```

### Post Increment (x++) 1 to 10

The post-increment operator (x++) increments the value but returns the original value. For values 1 through 10:

1+1 = 2, 2+1 = 3, 3+1 = 4, 4+1 = 5, ..., 9+1 = 10

```javascript
let x = 3; // x = 4
let y = x++; // y = 3 (delayed increment, returns original value)
```

When logging after initialization, the value of y would be 3 because the post-increment returns the original value, resulting in a slight delay. The concept applies similarly for decrementing, with the main distinction being the timing of the return, where pre-decrement (++x) involves one less step compared to post-decrement (x--).