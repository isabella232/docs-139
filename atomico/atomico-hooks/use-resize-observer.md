---
description: Observe the size change of a reference.
---

# use-resize-observer

### Modulo

```javascript
import {
  useResizeObserver,
  useResizeObserverState,
} from "@atomico/hooks/use-resize-observer";
```

### Syntax

#### useResizeObserver

```javascript
useResizeObserver(
  ref,
  (rect) => void
);
```

Where:

- `ref`: `Ref`, reference to observe the resizing.
- `rect`: `Object`, the return of `DOMRectReadOnly.toJSON()`, documentation of [DOMRect](https://developer.mozilla.org/en-US/docs/Web/API/DOMRectReadOnly)
  - width
  - height
  - x
  - y
  - top
  - right
  - bottom
  - left

#### useResizeObserverState

```javascript
const rect = useResizeObserverState(ref);
```

Where:

- `ref`: `Ref`, reference to observe the resizing.
- `rect`: `Object`, the return of `DOMRectReadOnly.toJSON()`, documentation of [DOMRect](https://developer.mozilla.org/en-US/docs/Web/API/DOMRectReadOnly)
  - width
  - height
  - x
  - y
  - top
  - right
  - bottom
  - left
