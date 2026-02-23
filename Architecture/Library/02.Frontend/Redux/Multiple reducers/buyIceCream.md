---
tags:
  - web
  - frontend
  - library
  - redux
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing a Redux action for buying ice cream.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
export const BUY_ICECREAM = 'BUY_ICECREAM'

import { BUY_ICECREAM } from './iceCreamTypes';

export const buyIceCream = () => {
  return {
    type: BUY_ICECREAM
  };
};
```

