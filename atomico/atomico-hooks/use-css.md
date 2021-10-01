---
description: Inject CSS into the shadowRoot
---

# use-css

Inject tag style into shadowRoot with content given as parameter to use CSS.

### Import

```javascript
import { useCss } from "@atomico/hooks/use-css";
```

### Sintaxis 

```typescript
useCss(cssText: string);
```

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/oNvNMr8qcl3h2FjtFdhd/src/index.jsx" %}

### Note

This hook was not created as a replacement for component.styles, it is rather a utility that seeks to facilitate the integration of css from a customHook, either by defining a state or another action.

