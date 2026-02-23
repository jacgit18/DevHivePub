---
tags:
  - web
  - frontend
  - library
  - redux
  - reduxToolKit
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing how createSlice empowers you to mutate state without requiring explicit state return.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
import { createSlice } from '@reduxjs/toolkit';

const initialState = {
  numOfCakes: 20,
};

const cakeSlice = createSlice({
  name: 'cake',
  initialState,
  reducers: {
    ordered: state => {
      state.numOfCakes--;
    },
    restocked: (state, action) => {
      state.numOfCakes += action.payload;
    },
  },
});

export const { ordered, restocked } = cakeSlice.actions;
export default cakeSlice.reducer;
```

`createSlice` serves as a hybrid of action and reducer, streamlining state updates in the background. Additionally, createSlice automatically generates action creator functions and returns the main reducer."