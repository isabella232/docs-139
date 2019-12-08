---
description: >-
  You can start prototyping web-components with Atomico without the need for a
  bundle tool, the following script is executable in the browser.
---

# Without bundle

### Example

```javascript
import { customElement } from "https://unpkg.com/atomico";
import html from "https://unpkg.com/atomico/html"

function WebComponent(){
    return html`<host>no bundle!</host>`
}

customElement("my-tag",WebComponent);
```

You can also start on the following platforms:

### Webcomponents.dev

{% embed url="https://webcomponents.dev/embed/KsE6rPxDyaLvG4pUCPGP" %}

### Codepen

{% embed url="https://codepen.io/uppercod/pen/XLqyVO" %}



