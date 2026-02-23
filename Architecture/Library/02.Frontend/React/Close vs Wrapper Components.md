---
tags:
  - web
  - frontend
  - "#CodebaseDecision"
  - library
  - react
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses when to use close components vs wrapper components.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
In React, the decision to use close components or wrapper components depends on the specific requirements and design of your application. Let's understand each concept:  
  
1. Close Components:  
	- Close components, also known as "presentational" or "dumb" components, focus solely on rendering the UI and receive data through props. They don't manage state or have any side effects. Close components are reusable and often represent a specific UI element or small component of your application.  
  
Use close components when:  
- You have a small, self-contained UI element that doesn't require state management or complex logic.  
- You need to encapsulate a specific part of your UI and make it reusable across multiple components.  
- You want to keep your codebase modular, allowing for easier maintenance and testing.  
  
Example close component:  
```jsx  
function Button(props) {  
return <button onClick={props.onClick}>{props.label}</button>;  
}  
```  

2. Wrapper Components:  
	- Wrapper components, also known as "container" or "smart" components, are responsible for managing state, handling data fetching, and orchestrating the behavior of one or more close components. They typically provide data and behavior through props to their child components.  
  
Use wrapper components when:  
- You need to manage state or handle data fetching for a specific part of your application.  
- You want to encapsulate complex logic and provide a clean interface to the close components.  
- You need to connect to external data sources or APIs and pass the relevant data to the close components.  
  
Example wrapper component:  
```jsx  
class TodoList extends React.Component {  
constructor(props) {  
super(props);  
this.state = {  
todos: [],  
};  
}  
  
componentDidMount() {  
// Fetch todos from API and update state  
// ...  
}  
  
render() {  
return <TodoItems todos={this.state.todos} />;  
}  
}  
```  
  
In summary, close components focus on UI rendering and reusability, while wrapper components handle state management and provide data and behavior to their child components. Striking a balance between these two types of components helps to maintain a modular and manageable codebase.





