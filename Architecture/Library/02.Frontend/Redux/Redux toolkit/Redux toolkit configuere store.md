---
tags:
  - web
  - frontend
  - library
  - redux
  - stateStore
  - reduxToolKit
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing how to configure store.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
import { configureStore, getDefaultMiddleware } from '@reduxjs/toolkit';
import logger from 'redux-logger';
import cakeReducer from '../features/cake/cakeSlice';
import icecreamReducer from '../features/icecream/icecreamSlice';
import userReducer from '../features/user/userSlice';

const store = configureStore({
  reducer: {
    cake: cakeReducer,
    icecream: icecreamReducer,
    user: userReducer,
  },
  middleware: getDefaultMiddleware().concat(logger),
});

export default store;
```

The statement "takes in slices which are acting as reducers" refers to the `reducer` property in the `configureStore` function. In the given code, each feature (cake, ice cream, and user) has its own slice, which acts as a reducer for that specific feature's state management.

- The `reducer` property is an object where each key represents a slice of the state (feature), and the corresponding value is the reducer function responsible for managing that part of the state.

- `cakeReducer`, `icecreamReducer`, and `userReducer` are the reducer functions for the cake, ice cream, and user features, respectively. These reducer functions are created using the `createSlice` function from `@reduxjs/toolkit`.

- A slice in Redux is essentially a reducer, but it also includes the action creators and the initial state. It encapsulates the logic for managing a specific piece of the overall application state.

- When you configure the store with these slices (reducers), each slice is responsible for handling actions and updating the state related to its specific feature. For example, the `cakeReducer` manages the state related to cakes, the `icecreamReducer` manages the state related to ice creams, and so on.

So, in summary, the statement means that the `configureStore` function takes in an object where each key-value pair represents a slice (reducer) responsible for managing a specific part of the overall state in the Redux store.