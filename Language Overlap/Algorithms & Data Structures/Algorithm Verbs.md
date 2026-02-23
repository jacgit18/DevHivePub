---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Order can vary
Purpose: This documentation discusses language consistent language to use when solving problems.
Status: 
Started: 2024-03-14
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
## Step by Step Approach Breakdown

### Precondition
- Check if Read(access)
- Compare

### Swap  
```javascript
[arrayA[idx], arrayB[idx]] = [arrayB[idx], arrayA[idx]]
```
Or do a push or shift into another array

### Calculate
- Return

### Sort
- Initialize/Store some variable or data structure

### Bass Case recursion  
- Edge case extreme

### Search
- Search condition
- RELATIVE POSITION  
  - Increment LeftIdx  
  - Decrement rightIdx  
  - Increment rightIdx

### Check if Read(access)
- Compare
- Break(stops loop) or continue(skip iteration) 

### Initialize/Store 
- some variable or data structure

### Update
- insert/delete/reassignment 

### Search
- When stuck list out variables that need to be updated and see if there's anything missing from there
- Termination condition

### Post condition
- Check if Read(access)
- Update
- Sort
- Return

**Note:** 
- Things like search and read are common things to break out into helper functions.