---
description: >-
  El virtualDOM  de Atomico se ha diseñado para potenciar el uso de
  webcomponents.
---

# VirtualDOM

### Regla de retorno

Una regla importante del virtualDOM de Atomico es que **todo webcomponent debe retornar el tag `<host/>`**. El tag host representara el estado del DOM del webcomponent, ejemplo:

1. Declaración del shadowDOM, mediante el atributo `shadowDom`
2. Declaración de eventos, atributos o propiedades.
3. Template del webcomponent.

### Sintaxis JSX

```jsx
import { c } from "atomico";

function component() {
  const handlerClick = () => console.log("click!");
  return (
    <host shadowDom onclick={handlerClick}>
      <h1>content</h1>
      <slot></slot>
    </host>
  );
}

customElements.define("my-component", c(component));
```

**Atomico soporta jsx-runtime**, alternativamente ud puede importar la funcion `h` para declarar manual del pragma JSX.

### Sintaxis Template String

```javascript
import { c } from "atomico";
import html from "atomico/html";

function component() {
  const handlerClick = () => console.log("click!");
  return html`<host shadowDom onclick=${handlerClick}>
    <h1>content</h1>
    <slot></slot>
  </host>`;
}

customElements.define("my-component", c(component));
```



