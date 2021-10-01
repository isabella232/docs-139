---
description: use CSS in the lightDOM locally in the webcomponent.
---

# use-css-light-dom

This hook aims to give css coverage in situations where the use of the lightDOM is required, **you always prefer to use the shadowDOM to give a general appearance to your component.**

### Module

```javascript
import { useCssLightDom } from "@atomico/hooks/use-css-light-dom";
```

### Syntax

This hook will wrap each css instance in a different className

```jsx
const css = useCssLightDom();

return (
  <host
    class={css`
      width: 100px;
      height: 100px;
      :hover {
        background: red;
      }
    `}
  ></host>
);
```

### **Example** 

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/odaNplBxuGgwsqkbHiLu/src/index.jsx" %}

\*\*\*\*

