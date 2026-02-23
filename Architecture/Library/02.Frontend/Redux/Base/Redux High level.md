---
tags:
  - web
  - frontend
  - library
  - redux
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Redux.
Status: Done
Started: 
EditDate: 2024-02-07
Relates: "[[StateChange(view)]]"
Peer Reviewed: 0
dg-publish:
---
![[Redux state flow.gif]]

A state management library that adheres to three fundamental principles:

1. **One Source of Truth:**
   - A store of state serves as the singular source of truth. This state is immutable, read-only, and undergoes changes exclusively through the use of pure functions. Imagine this structure resembling a tree.

2. **Immutable and Read-Only State:**
   - The store, representing the entire application or website's state, is immutable, fostering predictability and minimizing unexpected errors. After each action, a new state is generated.

3. **[[Pure Functions vs Impure Functions |Pure Function]] for State Changes:**
   - Changes to the state occur solely through pure functions. These functions take input and produce output predictably. The flow typically involves User Action > Reducer > Store > State Changes.

In the Redux architecture, actions trigger state changes through reducers, which are pure functions. This follows a Flux pattern: Action > Dispatcher > Store > View.

**Scaling Up:**
As applications scale, the number of reducers and actions increases. The solution involves creating a root reducer in the store to manage the growing complexity.

**Middleware:**
Between actions and reducers lies middleware, a tunnel allowing action modification. The `react-redux` `Provider` component becomes essential to avoid passing the store repetitively.

**Library Recommendations:**
- [Gatsby](https://www.gatsbyjs.com/)
- [Reselect](https://github.com/reduxjs/reselect)
- [Redux-Saga](https://redux-saga.js.org/)
- [Immutable.js](https://immutable-js.com/)

**Documentation:**
- [Redux Introduction](https://redux.js.org/introduction/getting-started)
- [Redux Toolkit Introduction](https://redux-toolkit.js.org/introduction/getting-started)
- [Redux Logger](https://github.com/LogRocket/redux-logger)

**Transition:**
Begin with learning Redux boilerplate code and then transition to Redux Toolkit for more streamlined development.

**Notes:**
- The `Provider` component facilitates access to the state.
- `connect` is a higher-order function that makes a component aware of the Redux state store.