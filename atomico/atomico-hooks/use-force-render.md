---
description: >-
  Allows forcing the rendering of the webcomponent without the need to be  tied
  to a state or property
---

# use-force-render

{% hint style="danger" %}
Since the version of atomico@1.14.\* there is the [**useUpdate**](../../api/hooks/useupdate.md) hook, with the same functionality but in the core of Atomico.
{% endhint %}

### Modulo

```javascript
import { useForceRender } from "@atomico/hooks/use-force-render";
```

### Syntax

```javascript
const forceRender = useForceRender();
```

Where:

1. `forceRender`: `Callback` to force rendering of the webcomponent.

### Example

Sometimes the rendering of the webcomponent does not depend on a state or property of this, to reflect these changes you can use `useForceRender` to regenerate the DOM, example:

```jsx
function component() {
  const ref = useRef();
  const forceRender = useForceRender();

  return (
    <host>
      {ref.current.anyProp}
      <my-component ref={ref} onclick={forceRender}></my-component>
    </host>
  );
}
```

