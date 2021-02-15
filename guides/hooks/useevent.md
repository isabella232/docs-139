---
description: Dispatch events from the webcomponent without referencing the context(this)
---

# useEvent

### Syntax

```javascript
const dispatchEvent = useEvent(myEvent, eventInit);
```

Where:

- dispatchEvent: **callback,** dispatch the event from the webcomponent.
- myEvent: **string**, name of the event to dispatch.
- eventInit: **optional object**, event configuration.

### Example

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

### Event customization

The second parameter of `useEvent` allows customizing the behavior of the even:

```typescript
interface EventInit {
  // Allows the event to be dispatched upstream to the node's containers.
  bubbles?: boolean;
  // Allows the event to traverse the shadowDOM event capture.
  composed?: boolean;
  // Allows the event to be canceled.
  cancelable?: boolean;
  // Allows customizing the event builder, ideal for event instance-based communication.
  base?: Event | CustomEvent;
}
```
