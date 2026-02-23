---
tags:
  - Vue
  - React
  - library
  - Framework
author:
  - jacgit18
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-06-09
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
React does not have a built-in `scoped` property for CSS styles like Vue.js. However, React developers often use various techniques and libraries to achieve scoped or component-specific styles. Here are some common approaches:  
  
### CSS Modules  
  
CSS Modules allow you to write CSS that is scoped to a particular component. When you import a CSS Module into a component, the styles are automatically namespaced to avoid conflicts.  
  
```jsx  
// styles.module.css  
.example {  
color: blue;  
}  
  
// MyComponent.jsx  
import React from 'react';  
import styles from './styles.module.css';  
  
function MyComponent() {  
return <div className={styles.example}>Scoped styles in React</div>;  
}  
  
export default MyComponent;  
```  
  
### Styled Components  
  
Styled Components is a popular CSS-in-JS library that enables you to write component-level styles using tagged template literals.  
  
```jsx  
// MyComponent.jsx  
import React from 'react';  
import styled from 'styled-components';  
  
const Example = styled.div`  
color: blue;  
`;  
  
function MyComponent() {  
return <Example>Scoped styles in React</Example>;  
}  
  
export default MyComponent;  
```  
  
### Emotion  
  
Emotion is another CSS-in-JS library that allows for writing scoped styles within your components.  
  
```jsx  
// MyComponent.jsx  
/** @jsxImportSource @emotion/react */  
import { css } from '@emotion/react';  
  
const exampleStyle = css`  
color: blue;  
`;  
  
function MyComponent() {  
return <div css={exampleStyle}>Scoped styles in React</div>;  
}  
  
export default MyComponent;  
```  
  
### Inline Styles  
  
React also supports inline styles, which can be useful for applying styles directly within the component's JSX. While not technically scoped, inline styles are limited to the elements they are applied to.  
  
```jsx  
// MyComponent.jsx  
import React from 'react';  
  
function MyComponent() {  
return <div style={{ color: 'blue' }}>Scoped styles in React</div>;  
}  
  
export default MyComponent;  
```  
  
### Summary  
  
While React does not have a built-in `scoped` attribute for styles like Vue.js, it offers several powerful alternatives through CSS Modules, CSS-in-JS libraries (such as Styled Components and Emotion), and inline styles. These approaches allow you to achieve component-specific styling effectively.