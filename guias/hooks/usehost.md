---
description: >-
  Hook que crea una referencia en la que current es la instancia del
  webcomponent.
---

# useHost

### Sintaxis

```javascript
const refHost = useHost();
```

Retorna la instancia del webcomponent como una referencia, esta referencia permite extender comportamientos al momento de crear customHooks.

### Ejemplo

```typescript
import { useHost, useEffect } from "atomico";

function useListener(type: string, callback: (ev: Event) => void) {
  const ref = useHost();
  useEffect(() => {
    const { current } = ref;
    current.addEventListener(type, callback);
    return () => current.removeEventListener(type, callback);
  }, []);
}
```

Del ejemplo podemos destacar que **useListener es un customHook** que permite escuchar un evento del webcomponent sin la necesidad de vincular dicho evento al virtual-dom.

