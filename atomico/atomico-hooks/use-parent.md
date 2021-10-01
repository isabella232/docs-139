---
description: Retrieve a node higher than the current webcomponent.
---

# use-parent

### Module

```javascript
import { useResponsiveState } from "@atomico/hooks/use-responsive-state";
```

### Syntax

```jsx
const selector = "form";
const parent = useParent(selector);
```

Where:

* `selector`: `String`, Selector to be used by [**Element.matches**](https://developer.mozilla.org/en-US/docs/Web/API/Element/matches) when searching for the parent.
* `parent`: `Element`, ascending search result according to selector.

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/OVpU1DQvmGjhYSf3Iqbu/src/index.jsx" %}



