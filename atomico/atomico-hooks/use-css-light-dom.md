---
description: share your style sheets between LightDOM and ShadowDOM
---

# use-css-light-dom

This hook creates a style tag in the lightDOM of the component, in order to insert that directly affect the lightDOM, before using this hook consider:

1. The css is not isolated as if it occurs in the shadowDOM.
2. It does not support the use of ::slotted selector.

### Module

```javascript
import { useCssLightDom } from "@atomico/hooks/use-css-light-dom";
```

### Syntax

```tsx
useCssLightDom(sheets: import("atomico").Sheets);
```

### Example

```jsx
import { css } from "atomico";
import { useCssLightDom } from "@atomico/hooks/use-css-light-dom";

const sheet = css`
  :host {
    display: block;
    background: black;
    color: white;
    padding: 100px;
    border-radius: 1rem;
  }
  :host(:hover) {
    background: crimson;
  }
`;

function myExample() {
  useCssLightDom(sheet);
  return (
    <host>
      <h1>Hello</h1>
    </host>
  );
}
```

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/odaNplBxuGgwsqkbHiLu/src/index.jsx" %}

***
