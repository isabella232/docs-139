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
import { 
    useReflectEvent, 
    reflectEvent  
} from "@atomico/hooks/use-reflect-event";
```

### Syntax useReflectEvent

```typescript
useReflectEvent(
    refFrom: Ref<Element>,
    refTo: Ref<Element>,
    eventType: string
);
```

useRefectEvent will listen for the eventType of refFrom, to reflect it on refTo

### Syntax reflectEvent

```javascript
reflectEvent( target: Element, event: Event );
```

Reflects on an element the given event
