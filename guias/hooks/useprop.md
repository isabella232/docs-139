---
description: Reactividad en el scope del webcomponent sin el uso de contexto(this)
---

# useProp

useProp permite trabajar con una prop\(propiedad\) del webcomponent de forma similar a useState.

### Sintaxis

```typescript
const [value, setValue] = useProp<PropType>(myProp);
```

Donde : 

* value: Valor actual de la prop.
* setValue: Callback que actualizar el valor de la prop.
* myProp: string, define el nombre de la prop a usar por el hook.
* PropType: Solo para Typescript, permite definir la regla de tipo para value y setValue.

### Ejemplo

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

Del ejemplo podemos deducir:

1. **useCounter es un customHook** y que este puede trabajar con cualquier propiedad del webcomponent del tipo Number,
2. useCounter retorna 2 métodos increment y decrement que modifican valor de la prop
3. **useCounter puede ser instanciado múltiples veces** para distintas propiedades. 



