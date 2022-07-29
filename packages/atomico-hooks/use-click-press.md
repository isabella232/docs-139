# use-click-press

The useClickPress hook will allow you to execute a callback with acceleration according to the click time, for example in the input type number we have 2 buttons by default, an up arrow and a down arrow, these allow us to modify the input value, either:

1. Increase the value before a click in a unit.
2. Increase the value by more than one unit according to the click pressure time.

### Example

```jsx
import { useClickPress } from "@atomico/hooks/use-click-press";

function counter() {
  const refButton = useRef();

  const [value, setValue] = useProp("value");

  const increment = () => setValue((value) => value + 1);

  useClickPress(refButton, increment);

  return (
    <host>
      <h1>value: {value}</h1>
      <button ref={refButton}>Increment</button>
    </host>
  );
}

counter.props = { value: { type: Number, value: 0 } };j
```

### Live example

{% embed url="https://webcomponents.dev/edit/fAF79tN9yepvKZir822t" %}
