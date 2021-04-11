---
description: use CSS in the lightDOM locally in the webcomponent.
---

# use-css-light-dom

### Modulo

```javascript
import { useCssLightDom } from "@atomico/hooks/use-css-light-dom";
```

### Syntax

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
  >
    <slot ref={ref}></slot>
  </host>
);
```

{% hint style="info" %}
The CSS format is Atomico to class, so avoid using tree selectors.
{% endhint %}
