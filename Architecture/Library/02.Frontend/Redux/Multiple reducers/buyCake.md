---
tags:
  - web
  - frontend
  - library
  - redux
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing a Redux action for buying cake.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
export const BUY_CAKE = 'BUY_CAKE'

import { BUY_CAKE } from './cakeTypes';

export const buyCake = (number = 1) => {
  return {
    type: BUY_CAKE,
    payload: number
  };
};
```

