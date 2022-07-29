---
description: Retrieve a node higher than the current webcomponent.
---

# use-parent

### Module

```javascript
import { useParent, useParentPath } from "@atomico/hooks/use-parent";
```

### Syntax useParent

```jsx
const selector = "form";
const parent = useParent(selector);
```

Where:

* `selector`: `String`, Selector to be used by [**Element.matches**](https://developer.mozilla.org/en-US/docs/Web/API/Element/matches) when searching for the parent.
* `parent`: `Element`, ascending search result according to selector.

### Syntax useParentPath

```jsx
const parents = useParentPath(composed?: boolean);
```

Where:

* `parents:` parent nodes of the webcomponent
* `composed`: bypasses shadow DOM in parent capture.

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/OVpU1DQvmGjhYSf3Iqbu/src/index.jsx" %}

