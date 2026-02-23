---
tags:
  - web
  - frontend
  - library
  - react
  - redux
  - javascript
  - typescript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation is a code snippet showing how mapStateToProps and mapDispatchToProps are used.
Status: Final
Started: 
EditDate: 2024-02-07
Relates: 
Peer Reviewed: 1
dg-publish:
---
```jsx
// mapStateToProps & mapDispatchToProps has second param called ownProps which is rarely used but is used with conditional rendering

function ItemContainer(props) {
  return (
    <>
      <h2>Item - {props.item}</h2>
      <div>
        <button onClick={props.buyItem}>Buy Items</button>
      </div>
    </>
  );
}

const mapStateToProps = (state, ownProps) => {
  const itemState = ownProps.cake
    ? state.cake.numOfCakes
    : state.iceCream.numOfIceCreams;

  return {
    item: itemState
  };
};

// there will be a situation where you don't want to subscribe to state and only pass dispatch to connect
const mapDispatchToProps = (dispatch, ownProps) => {
  const dispatchFunction = ownProps.cake
    ? () => dispatch(buyCake())
    : () => dispatch(buyIceCream());

  return {
    buyItem: dispatchFunction
  };
};

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(ItemContainer);

// APP
<ItemContainer cake />
<ItemContainer /> // since no cake ice cream
```

