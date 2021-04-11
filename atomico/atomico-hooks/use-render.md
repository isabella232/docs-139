---
description: >-
  Run a second render before the webcomponent render, ideal for
   collaborative work between shadowDOM and lightDOM
---

# use-render

### Modulo

```javascript
import { useRender } from "@atomico/hooks/use-render";
```

### Syntax

```jsx
useRender(() => <input type="text" />, optionalArguments);
```

### Example

Sometimes you work with shadowDOM inputs, the shadowDOM prevents the communication of events with a form superior to the shadowDOM, `useRender`, it allows you to create inputs in the lightDOM and thus maintain the desired effects.

```jsx
import { useProp } from "atomico";
import { useRender } from "@atomico/hooks/use-render";

function myInput({ name }) {
  const [checked, setChecked] = useProp("checked");
  const toggle = () => setChecked(!checked);
  // The state of the webcomponent could be reflected
  // in the example form using formData
  useRender(() => <input type="checkbox" name={name} checked={checked} />);
  return (
    <host shadowDom>
      <button onclick={toggle}>{checked ? "✔️" : "❌"}</button>
    </host>
  );
}

myInput.props = {
  name: String,
  checked: Boolean,
};
```
