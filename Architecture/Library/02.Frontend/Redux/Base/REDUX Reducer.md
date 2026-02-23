---
tags:
  - web
  - frontend
  - library
  - redux
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Redux reducers.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
const initialState = {
  countToNothing: 10
};

function reducer(state = initialState, action) {
  switch (action.type) {
    // returns a new object, no mutation, thus a pure function
    // Changes are only made with pure functions, meaning a function that takes in an input and gives an output that is predictable
    case DO_ACTION:
      return {
        ...state, // copy state, update countToNothing
        countToNothing: state.countToNothing - 1
      };
    default:
      return state;
  }
}

const combineReducers = redux.combineReducers;

// similar structure
function counterReducer(state = initialState, action) {}
function otherCounterReducer(state = initialState, action) {}

const rootReducers = combineReducers({
  counter: counterReducer,
  otherCounter: otherCounterReducer
});
```

