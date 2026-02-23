---
tags:
  - web
  - frontend
  - library
  - react
  - hooks
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses useContext hook.
Status: Done
Started: 
EditDate: 2024-02-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Using Context in React:

When dealing with nested components and the need to pass props to deeply nested components, manual [[Props#Prop-Drilling and Modification |prop drilling]] can lead to performance issues. This process, known as prop drilling, can become cumbersome.

**Context API and useContext Hook:**

The Context API, along with the `useContext` hook, offers a solution to this problem by allowing the passing of data through the component tree without manual prop passing at every level.

**Re-render Triggers:**

After the initial render, React monitors changes in state and the React context provider. When a new value is provided to the context due to a state alteration, React notes the need to re-render components consuming that context, including their child components.

The subsequent render phase follows the typical stages of behavior, involving the render and commit phases. Memoization can be employed to optimize performance by preventing unnecessary re-renders of components that consume the context.

**Same Element Reference:**

Context provides a means to share data globally without the need to pass props manually at every level. This global sharing is especially useful for data like the current authenticated user, theme, or preferred language.

### When to Use Context:

Context is designed for scenarios where data can be considered "global" for a tree of React components. Examples include the current authenticated user, theme, or preferred language. The following code demonstrates using context to manage the theme:

```jsx
import React, { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

function App() {
  return (
    <div className="App">
      <ThemeContext.Provider value={'red'}>
        <Content />
      </ThemeContext.Provider>
    </div>
  );
}

function Content() {
  const theme = useContext(ThemeContext);

  return (
    <div className={theme}>
      <h2>Hello, World</h2>
    </div>
  );
}

export default App;
```

In this example, the `ThemeContext.Provider` allows the `Content` component and its children to consume the theme without manual prop passing, demonstrating the simplicity and power of the Context API in managing global state.