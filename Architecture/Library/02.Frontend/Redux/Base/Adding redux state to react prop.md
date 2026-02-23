---
tags:
  - web
  - frontend
  - library
  - react
  - redux
  - props
  - javascript
  - typescript
  - stateStore
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing how add redux state to react props.
Status: Final
Started: 
EditDate: 2024-02-07
Relates: "[[Props]]"
Peer Reviewed: 1
dg-publish:
---
```jsx
const logger = createLogger();

const rootReducers = combineReducers({ requestRobots, searchRobots }); // Assuming searchRobots is a reducer in a separate file

const store = createStore(rootReducers, applyMiddleware(thunkMiddleware, logger));

ReactDOM.render(
// Provider use react context in the background
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);

// APP

const mapStateToProps = (state) => {
  return {
    searchField: state.searchRobots.searchField,
    robots: state.requestRobots.robots,
    isPending: state.requestRobots.isPending
  };
}

const mapDispatchToProps = (dispatch) => {
  return {
    onSearchChange: (event) => dispatch(setSearchField(event.target.value)),
    onRequestRobots: () => dispatch(requestRobots())
  };
}

class App extends Component {
  componentDidMount() {
    this.props.onRequestRobots();
  }

  render() {
    const { robots, searchField, onSearchChange, isPending } = this.props;

    const filteredRobots = robots.filter(robot => {
      return robot.name.toLowerCase().includes(searchField.toLowerCase());
    });

    return (
      <div className='tc'>
        <h1 className='f1'>RoboFriends</h1>
        <SearchBox searchChange={onSearchChange} />
        <Scroll>
          {isPending ? <h1>Loading</h1> :
            <ErrorBoundary>
              <CardList robots={filteredRobots} />
            </ErrorBoundary>
          }
        </Scroll>
      </div>
    );
  }
}

export default connect(mapStateToProps, mapDispatchToProps)(App);
```




