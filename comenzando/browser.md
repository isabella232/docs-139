---
description: >-
  Ud puede comenzar a prototipar web-components con Atomico sin la necesidad de
  un empaquetador, el siguiente script es ejecutable en el navegador.
---

# Uso sin bundle

### Ejemplo

```javascript
import { customElement } from "https://unpkg.com/atomico";
import html from "https://unpkg.com/atomico/html"

function WebComponent(){
    return html`<host>no bundle!</host>`
}

customElement("my-tag",WebComponent);
```

Ud tambien puede comenzar en las siguientes plataformas:

### Webcomponents.dev

{% embed url="https://webcomponents.dev/embed/KsE6rPxDyaLvG4pUCPGP" %}

### Codepen

{% embed url="https://codepen.io/uppercod/pen/XLqyVO" %}



