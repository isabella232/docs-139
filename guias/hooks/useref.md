---
description: >-
  Permite crear una objeto persistente entre renders para capturar de un nodo
  desde el VirtualDOM
---

# useRef

### Sintaxis

```javascript
const ref = useRef(optionalCurrent);
```

### Ejemplo

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

### Observación

El objeto de referencia es útil para referenciar nodos entre customHooks.

