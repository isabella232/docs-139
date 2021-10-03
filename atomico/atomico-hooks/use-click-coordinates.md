---
description: Captures the click event coordinates (Touch)
---

# use-click-coordinates

### Module

```javascript
import { useClickCoordinates } from "@atomico/hooks/use-click-coordinates";
```

### Syntax

```javascript
useClickCoordinates(ref, handlerClick);
```

where:

1. `ref`: node reference to observe the click event.
2. `handlerClick`: Callback that receives the coordinates of the click event.

### Coordinates

```typescript
interface Coordinates {
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

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/J9YAAYlyqBw47z2twgAj/src/index.jsx" %}



