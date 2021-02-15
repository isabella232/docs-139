---
description: >-
  Create a persistent object between renders to capture from a node from
  VirtualDOM
---

# useRef

## Syntax

```javascript
const ref = useRef(optionalCurrent);
```

## Example

```jsx
import { useRef, useEffect, useState } from "atomico";

function component() {
  const ref = useRef();
  const [message, setMessage] = useState();
  useEffect(() => {
    const { current } = ref;
    current.addEventListener("input", () => {
      if (current.validity.typeMismatch) {
        setMessage("Invalid!");
      }
      current.setCustomValidity("");
    });
  }, []);
  return (
    <host>
      <input type="email" ref={ref} />
      {message && <h1>{message}</h1>}
    </host>
  );
}
```

## Observation

The reference object is useful for referencing nodes between customHooks.

