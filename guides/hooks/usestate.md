---
description: Create a local state in the web-component
---

# useState

### Syntax

```javascript
let [state, setState] = useState(initialState);
```

Where:

* `state` : Any,  is the current state of the hook.
* `setState` : Function, allows to modify the current state.

  > if it is a function it will be executed receiving as argument the current state to return the next state

* `initialState` : Any, is the initial state.

  > If it is a function, it will be executed to return the initial state

### Example

```jsx
import { h, useState } from "atomico";

function WebComponent(){
  let [count, setCount] = useState(0);
  
  function increment() {
    setCount(count + 1);
  }
  
  return <host>
    count : {count}
    <button onclick={increment}>increment</button>
  </host>;
}
```

Where:

* `count` : Number, is the current state,  initialized as 0.
* `increment` : Function, callback dispatching the state increase .

