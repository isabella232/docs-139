---
description: Retrieve a node higher than the current webcomponent.
---

# use-parent

### Modulo

```javascript
import { useResponsiveState } from "@atomico/hooks/use-responsive-state";
```

### Syntax

```jsx
const selector = "form";
const parent = useParent(selector);
```

Where:

- `selector`: `String`, Selector to be used by `Element.matches` when searching for the parent.
- `parent`: `Element`, ascending search result according to selector.
