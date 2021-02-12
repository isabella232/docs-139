---
description: Emite eventos desde el webcomponent sin referenciar el contexto(this)
---

# useEvent

### Sintaxis

```javascript
const dispatchEvent = useEvent(myEvent, eventInit);
```

Donde:

* dispatchEvent: **callback,** despacha el evento desde el webcomponent.
* myEvent: **string**, nombre del evento a emitir.
* eventInit: **objeto opcional**, configuración del evento.

### Ejemplo

```jsx
import { useEvent } from "atomico";

function component() {
  const dispatchEvent = useEvent("clickButton", {
    bubbles: true,
    composed: true,
  });
  return (
    <host>
      <button onclick={() => dispatchEvent()}>button</button>
    </host>
  );
}
```

### Customización del evento

La configuración del evento se memoriza al momento de crear dicho evento, mediante un objeto ud puede dar comportamientos especiales como:

```typescript
interface EventInit {
  bubbles?: boolean;
  composed?: boolean;
  cancelable?: boolean;
  base?: Event | CustomEvent;
}
```

* **bubbles**: permite que el evento sea despachado de forma ascendente hacia los contenedores del nodo.
* **composed**: permite que el evento atraviese la captura de eventos del shadowDOM.
* **cancelable**:  permite que el evento sea cancelado.
* **base**: permite personalizar el constructor del evento, ideal para comunicación basada en instancia de eventos.

