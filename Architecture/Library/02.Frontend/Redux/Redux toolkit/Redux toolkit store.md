---
tags:
  - web
  - frontend
  - library
  - redux
  - stateStore
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing how redux toolkit store works.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
import store from './app/store';
import { cakeActions } from './features/cake/cakeSlice';
import { icecreamActions } from './features/icecream/icecreamSlice';
import { fetchUsers } from './features/user/userSlice';

console.log('Initial State:', store.getState());

const unsubscribe = store.subscribe(() => {
  console.log('Updated State:', store.getState());
});

store.dispatch(cakeActions.ordered());
store.dispatch(cakeActions.ordered());
store.dispatch(cakeActions.ordered());
store.dispatch(cakeActions.restocked(3));

store.dispatch(icecreamActions.ordered());
store.dispatch(icecreamActions.ordered());
store.dispatch(icecreamActions.ordered());
store.dispatch(icecreamActions.restocked(3));

store.dispatch(fetchUsers());
// unsubscribe();
```

