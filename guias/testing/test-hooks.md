---
description: >-
  Realice test a hooks creados con Atomico con una instancia aislada y
  predecible
---

# Test hooks

Atomico ofrece un submodulo llamado "atomico/test-hooks", este modulo es parte directa del core de Atomico y agnóstica al uso de webcomponents.

```javascript
import { createHooks } from "atomico/test-hooks";
```

### createHooks

función que crea una colección que permite asociar hooks para ejecutarlos en un ciclo de vida controlado.

#### Instancia

```typescript
const hooks = createHooks(opcionalRender, opcionalHost);
```

Donde:

* **optionalRender**: Callback que permite reiniciar el ciclo de vida del hook, este callback será ejecutado cada vez que un hook como [useState ](../hooks/usestate.md)o [useReducer ](../hooks/usereducer.md)soliciten la actualización del scope.
* **opcionalHost**: ****permite dar un objeto a ser compartido mediante el hook [useHost](../hooks/usehost.md).

#### Retorno 

```typescript
interface Hooks {
    load<T>(callback: () => T): T;
    clearEffect(unmounted?: boolean): () => void;
}
```

Donde

* **load**:  función que asocia permite asociar el scope del callback a un habito de contexto global temporal. 
* **clearEffect:** funcion que permite recolectar los efectos de useLayoutEffect, **al ejecutar clearEffect se retornara un callback que permite finalizar la recoleccion final de useEffect cerrando el ciclo de efectos secundarios.**

  Opcionalmente clearEffect acepta un parámetro booleano que comunica que la colección de Hooks ha debe ser desmontada si este se define como true.

### Ejemplo:

**./use-counter.js**

```typescript
import { useState } from "atomico";

export function useCounter(initialValue) {
  const [value, setValue] = useState<number>(initialValue);
  return {
    value,
    increment: () => setValue((value) => value + 1),
    decrement: () => setValue((value) => value - 1),
  };
}
```

**./use-counter.test.js:** Se recomienda el uso del entorno de test [@web/test-runner](https://modern-web.dev/docs/test-runner/overview/) para realizar pruebas para Atomico.

```javascript
import { expect } from "@esm-bundle/chai";
import { createHooks } from "atomico/test-hooks";
import { useCounter } from "./use-counter.js";

it("Check return", () => {
  const hooks = createHooks();

  const counter = hooks.load(() => useCounter(10));

  expect(counter.value).to.equal(10);
  expect(counter.increment).to.be.an.instanceOf(Function);
  expect(counter.decrement).to.be.an.instanceOf(Function);
});
```

\*\*\*\*

