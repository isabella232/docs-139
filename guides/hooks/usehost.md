---
description: >-
  Hook that creates a reference that curren is the instance of the webcomponent.
---

# useHost

### Syntax

```javascript
const refHost = useHost();
```

Returns the instance of the webcomponent in reference format, this reference allows to extend behaviors when creating customHooks.

### Example

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

From the example we can highlight that **useListener is a customHook** that allows listening to an event from the webcomponent without the need to link said event to the VirtualDOM.
