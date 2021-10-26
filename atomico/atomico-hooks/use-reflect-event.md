---
description: >-
  the useReflectEvent hook reflects the event from the reference origin to the
  reference destination
---

# use-reflect-event

the useReflectEvent hook reflects the event from the reference origin to the reference destination, the captured event will be canceled

One of the possibilities of this hook is to reflect the events inside shadowDOM to lightDOM, example when using forms

### module

```javascript
import { useReflectEvent } from "@atomico/hooks/use-reflect-event";
```

### Syntax

```
useReflectEvent(
    refFrom: Ref<Element>,
    refTo: Ref<Element>,
    event: string,
    filter?: (event:Event)=>boolean
);
```

### Example

