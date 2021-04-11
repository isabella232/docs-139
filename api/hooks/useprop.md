---
description: Reactivity in the scope of the webcomponent without the use of context(this)
---

# useProp

useProp allows you to work with a prop\(property\) of the webcomponent in a similar way to useState.

## Syntax

```javascript
const [value, setValue] = useProp(myProp);
```

Where :

* value: Current value of the prop.
* setValue: Callback to update the value of the prop.
* myProp: string, defines the name of the prop to be used by the hook.

## Example

```jsx
import { useProp } from "atomico";

function useCounter(prop) {
  const [value, setValue] = useProp(prop);
  return {
    value,
    increment: () => setValue((value) => value + 1),
    decrement: () => setValue((value) => value - 1),
  };
}

function component() {
  const counter = useCounter("value");
  return (
    <host>
      <button onClick={counter.increment}>+</button>
      <strong>{counter.value}</strong>
      <button onClick={counter.decrement}>-</button>
    </host>
  );
}

component.props = {
  value: { type: Number, value: 0 },
};
```

Where:

1. **useCounter is a customHook** and that it can work with any property of the webcomponent of type Number.
2. useCounter returns 2 methods increment and decrement that modify the value of the prop.
3. **useCounter can be instantiated multiple times** for different properties.

