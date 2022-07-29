---
description: Synchronize the state of the disabled prop with the fieldset tag
---

# use-disabled

Inherit the `disabled` status of a parent tag type `fieldset`, under certain rules:

1. The label must be on the lightDOM.
2. The component that uses this hook must declare the prop `{disabled: Boolean}`.

### Import

```javascript
import { useDisabled } from "@atomico/hooks/use-disabled";
```

### Sintaxis 

```typescript
const disabled:boolean = useDisabled(matches?: string = "fieldset");
```

Where:

1. `matches`: Optional string, allows to change the search of the parent tag fieldset for another tag or selector compatible with [**Element.matches**](https://developer.mozilla.org/en-US/docs/Web/API/Element/matches).

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/27OZ3Rbu02eJzcQe6C5G/src/index.jsx" %}



