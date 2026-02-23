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
Purpose: This documentation discusses Redux stores.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
const { createStore, applyMiddleware, bindActionCreators } = redux;
const { createLogger } = reduxLogger;
const thunkMiddleware = reduxThunk.default;

const loggerMiddleware = createLogger();

const store = createStore(rootReducers, applyMiddleware(loggerMiddleware, thunkMiddleware));

// Initial state can be obtained with
store.getState();

// Registers listeners
store.subscribe(listeners);

const unsubscribe = store.subscribe(() => console.log('Updating state', store.getState()));

// Then dispatch, which takes an action as a param and causes a state transition
store.dispatch(doSomething());
store.dispatch(doSomething());
store.dispatch(doSomething());

// Alternatively, dispatch using Bind Action Creators (not commonly used)
const actions = bindActionCreators({ doSomething, otherAction }, store.dispatch);
actions.doSomething();

// Unsubscribe to reset state changes
unsubscribe();
```

## Store Short Description

The store is a read-only, immutable object serving as the single source of truth for the entire state of the application or website. It takes a reducer as a parameter, encapsulating the logic for state transitions. All interactions with the state occur through the store, particularly when invoking `store.dispatch()`.

When you dispatch an action, it flows through the store and into the reducer. The reducer, responsible for handling actions and updating the state accordingly, returns a new state. Crucially, the store remains unchanged; instead, a new state is created based on the existing state and the action dispatched.

This immutability ensures that the state is not modified directly. The store serves as a centralized hub where actions are dispatched, and the state is updated through the pure functions defined in the reducer. This unidirectional flow allows for better predictability, debugging, and management of application state.