---
tags:
  - web
  - frontend
  - library
  - redux
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing how reducer manages state change for cake actions being dispatch.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
import { BUY_CAKE } from './cakeTypes';

const initialState = {
  numOfCakes: 10
};

const cakeReducer = (state = initialState, action) => {
  switch (action.type) {
    case BUY_CAKE:
      return {
        ...state,
        numOfCakes: state.numOfCakes - action.payload
      };
    default:
      return state;
  }
};

export default cakeReducer;
```



