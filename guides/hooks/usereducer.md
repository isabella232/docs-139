---
description: >-
  An alternative to useState. Accept a reduce and return the current state
  paired with a dispatch method. (If you are familiar with Redux, you know how
  does it work
---

# useReducer

### Syntax

```javascript
let[state, dispatch] = useReducer(reducer, initialState);
```

Where:

* `reducer` : Function reducer
* `initialState`: initial state of reducer

#### Example

```javascript
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <host>
      Count: {state.count}
      <button onclick={() => dispatch({type: 'decrement'})}>-</button>
      <button onclick={() => dispatch({type: 'increment'})}>+</button>
    </host>
  );
}
```

