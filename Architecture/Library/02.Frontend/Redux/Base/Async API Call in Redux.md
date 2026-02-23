---
tags:
  - web
  - frontend
  - "#library"
  - redux
  - API
  - asynchronous
  - javascript
  - typescript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing how make API call in Redux with promises instead of Async Await.
Status: Final
Started: 
EditDate: 2024-02-07
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
const redux = require('redux');
const thunkMiddleware = require('redux-thunk').default;
const axios = require('axios');

const createStore = redux.createStore;
const applyMiddleware = redux.applyMiddleware;

// Initial State
const initialState = {
  loading: false,
  users: [],
  error: ''
};

// Action Types
const FETCH_USERS_REQUEST = 'FETCH_USERS_REQUEST';
const FETCH_USERS_SUCCESS = 'FETCH_USERS_SUCCESS';
const FETCH_USERS_FAILURE = 'FETCH_USERS_FAILURE';

// Action Creators
const fetchUsersRequest = () => ({
  type: FETCH_USERS_REQUEST
});

const fetchUsersSuccess = users => ({
  type: FETCH_USERS_SUCCESS,
  payload: users
});

const fetchUsersFailure = error => ({
  type: FETCH_USERS_FAILURE,
  payload: error
});

// Async HTTP Action
const fetchUsers = () => {
  return function (dispatch) {
    dispatch(fetchUsersRequest());

    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        const users = response.data.map(user => user.id);
        dispatch(fetchUsersSuccess(users));
      })
      .catch(error => {
        dispatch(fetchUsersFailure(error.message));
      });
  };
};

// Reducer
const reducer = (state = initialState, action) => {
  console.log(action.type);

  switch (action.type) {
    case FETCH_USERS_REQUEST:
      return {
        ...state,
        loading: true
      };

    case FETCH_USERS_SUCCESS:
      return {
        loading: false,
        users: action.payload,
        error: ''
      };

    case FETCH_USERS_FAILURE:
      return {
        loading: false,
        users: [],
        error: action.payload
      };

    default:
      return state;
  }
};

// Store
const store = createStore(reducer, applyMiddleware(thunkMiddleware));

// Subscribe to store changes
store.subscribe(() => {
  console.log(store.getState());
});

// Dispatch the async action
store.dispatch(fetchUsers());
```



