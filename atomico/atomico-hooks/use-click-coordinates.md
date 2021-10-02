---
description: Captures the click event coordinates (Touch)
---

# use-click-coordinates

This hook captures the click event coordinates \(Touch\) and gives a callback in the following format:

```typescript
interface Point {
  x: number;
  y: number;
  offset: {
    x: number;
    y: number;
  };
}
```

Where :

* x: MouseEvent.clientX
* y: MouseEvent.clientY
* offset.x : MouseEvent.offsetX
* offset.Y : MouseEvent.offsetY

### Module

```javascript
import { useClickCoordinates } from "@atomico/hooks/use-click-coordinates";
```

### Syntax

```javascript
useClickCoordinates(ref, handlerClick);
```

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/J9YAAYlyqBw47z2twgAj/src/index.jsx" %}



