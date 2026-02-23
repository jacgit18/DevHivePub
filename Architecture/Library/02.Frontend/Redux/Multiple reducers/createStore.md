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
Purpose: This documentation is a code snippet showing how to create a store with root reducers and applying middleware.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
import { createStore, applyMiddleware } from 'redux';
import { composeWithDevTools } from 'redux-devtools-extension';
import logger from 'redux-logger';
import thunk from 'redux-thunk';
import rootReducer from './rootReducer';

const store = createStore(
  rootReducer,
  composeWithDevTools(applyMiddleware(logger, thunk))
);

export default store;
```
