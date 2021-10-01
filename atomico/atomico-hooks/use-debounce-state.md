---
description: 'creates a bottleneck to the definition of a state, limits concurrency.'
---

# use-debounce-state

### Module

```javascript
import { useDebounceState } from "@atomico/hooks/use-debounce-state";
```

### Syntax

this hook is similar to useState, but the purpose of this hook is to bottleneck the state at update time

```javascript
const [state, setState] = useDebounceState(delay:number, initialState: any);
```

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/0LxJOPQzUkiwU0TB8o2s/src/index.jsx" %}



