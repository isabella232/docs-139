---
description: Crea un estado local en el web-component
---

# useState

### Sintaxis 

```javascript
let [state, setState] = useState(initialState);
```

Donde :

* `state` es el estado actual del hook.
* `setState` es una función que modifica el estado actual.

  > **De ser función** será ejecutada recibiendo como argumento el estado actual para retornar el siguiente estado

* `initialState` es el estado inicial

  > **De ser función** será ejecutada para retornar el estado inicial

### Ejemplo

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

Donde :

* `count` es el estado actual, inicializando en `0`
* `increment` es el actualizador de estado mediante el uso de `setCount`

