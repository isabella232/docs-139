---
description: Emite eventos desde el webcomponent sin referenciar el contexto(this)
---

# useEvent

useEvent permite desde el webcomponent según la lógica del webcomponent. 

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



