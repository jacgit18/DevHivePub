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
Purpose: This documentation is a code snippet showing how to work with immer.
Status: Final
Started: 
EditDate: 2024-02-08
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
import { createStore } from 'redux';
import produce from 'immer';

// Initial state
const initialState = {
  name: 'Vishwas',
  address: {
    street: '123 Main St',
    city: 'Boston',
    state: 'MA',
  },
};

// Action type
const STREET_UPDATED = 'STREET_UPDATED';

// Action creator
const updateStreet = street => ({
  type: STREET_UPDATED,
  payload: street,
});

// Reducer
const reducer = (state = initialState, action) => {
  switch (action.type) {
    case STREET_UPDATED:
    // return {
	// ...state,
	// address: {
	// ...state.address,
	// street: action.payload
	//	 }
	// }
	
	// draft is a draft copy of the current state immer
	// allows us to update the draft stat like the state is
	// mutable but behind scenes immer translate the
	// to the nested state return above
	
      return produce(state, draft => {
        draft.address.street = action.payload;
      });
    default:
      return state;
  }
};

// Create Redux store
const store = createStore(reducer);

// Initial state log
console.log('Initial State ', store.getState());

// Subscribe to state changes
const unsubscribe = store.subscribe(() => {
  console.log('Updated State ', store.getState());
});

// Dispatch action to update street
store.dispatch(updateStreet('456 Main St'));

// Unsubscribe to stop listening to state changes
unsubscribe();
```

**Immer** is a JavaScript library that facilitates working with immutable data structures in a more convenient and mutable-looking way. It simplifies the process of updating nested data structures, making the code more readable and easier to write.

The main feature of Immer is its ability to produce a draft of the original state, allowing you to make modifications to this draft in a mutable fashion. Behind the scenes, Immer ensures that these modifications don't mutate the original state directly. Instead, it creates a new immutable state based on the modifications.

Immer is commonly used with Redux to simplify the process of updating the state within reducers. Instead of creating deeply nested copies of state objects, developers can use Immer to produce a draft, modify it as if it were mutable, and Immer takes care of generating the updated immutable state.

In the code snippet, `produce` takes the initial state and a callback function that mutates a draft of that state. The library ensures that the original state remains immutable, and the `newState` reflects the modifications made in the draft. This approach simplifies the process of working with immutable data structures, especially when dealing with deeply nested objects or arrays.