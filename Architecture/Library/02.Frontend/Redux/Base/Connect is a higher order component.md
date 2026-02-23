---
tags:
  - web
  - frontend
  - library
  - react
  - HOC
  - redux
  - javascript
  - typescript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing connect higher order component.
Status: Final
Started: 
EditDate: 2024-02-07
Relates: "[[Props#Higher Order Components (HOC) and Render Prop Pattern |HOC]]"
Peer Reviewed: 1
dg-publish:
---
```jsx
import React, { Component } from 'react';

const withCounter = (WrappedComponent, incrementNumber) => {
  class WithCounter extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        count: 0
      };
    }

    incrementCount = () => {
      this.setState(prevState => {
        return { count: prevState.count + incrementNumber };
      });
    }

    render() {
      console.log('HOC', this.props.name);
      return (
        <WrappedComponent
          count={this.state.count}
          incrementCount={this.incrementCount}
          {...this.props.name}
        />
      );
    }
  }

  return WithCounter;
};

class ClickCounter extends Component {
  render() {
    const { count, incrementCount } = this.props;
    return <button onClick={incrementCount}>{this.props.name} Clicked {count} times</button>;
  }
}

export default withCounter(ClickCounter, 5);
```

