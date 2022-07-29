---
description: creates a bottleneck to the definition of a state, limits concurrency.
---

# use-debounce-state

### Module

```javascript
import { useDebounceState } from "@atomico/hooks/use-debounce-state";
```

### Syntax

this hook is similar to useState, but the purpose of this hook is to bottleneck the state at update time

```javascript
const [state, setState] = useDebounceState(
    delay:number, 
    initialState: any,
    mode?: "fps" | "timeout" | "idle"
);
```

**mode differences**

1. **fps**:&#x20;
   1. if delay is set to 1, the update is executed for each cycle of requestAnimationFrame(60fps),  &#x20;
   2. if delay is defined as 2, the update is executed for every 2 cycle of requestAnimationFrame(30fps)
2. **timeout**: the delay will be the milliseconds for setTimeout
3. **idle** : the delay will be the milliseconds for requestIdleCallback



### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/0LxJOPQzUkiwU0TB8o2s/src/index.jsx" %}
