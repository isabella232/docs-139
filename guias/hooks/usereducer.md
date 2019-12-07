---
description: >-
  Una alternativa a useState. Acepta un reducer  y devuelve el estado actual
  emparejado con un método dispatch. (Si está familiarizado con Redux, ya sabe
  cómo funciona
---

# useReducer

### Sintaxis

```javascript
let[state, dispatch] = useReducer(reducer, initialState);
```

 Donde : 

* `reducer` : Funcion reducer
* `initialState`: estado inicial de reducer

`useReducer` a menudo es preferible a `useState` cuando se tiene una lógica compleja que involucra múltiples subvalores o cuando el próximo estado depende del anterior.

### Ejemplo

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

