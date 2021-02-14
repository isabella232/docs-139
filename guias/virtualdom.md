---
description: >-
  El virtualDOM  de Atomico se ha diseñado para potenciar el uso de
  webcomponents.
---

# VirtualDOM

## Sintaxis

### JSX

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

**Atomico soporta jsx-runtime**, alternativamente ud puede importar la funcion `h` para declarar manual del pragma JSX, ejemplo:

```javascript
/**@jsx h*/
import { h } from "atomico";
```

### Template String

Atomico soporta el uso de template-string gracias al uso de la libreria [htm ](https://github.com/developit/htm)

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

## Regla de retorno

```jsx
function component() {
  // The webcomponent should always return the host tag
  return <host></host>;
}
```

Una regla importante del virtualDOM de Atomico es que **todo webcomponent debe retornar el tag `<host/>`**. El tag host representara el estado del DOM del webcomponent, como:

1. Declaración del shadowDOM, mediante el atributo `shadowDom`
2. Declaración de eventos, atributos o propiedades.
3. Template del webcomponent.

## Template

### Asociación de eventos

Atomico considera que una propiedad debe ser asociada como evento si esta es del tipo función y comienza con el prefijo 'on', ejemplo:

```jsx
<host onclick={() => console.log("click!")}></host>;
<host onMyEvent={() => console.log("MyEvent!")}></host>;
<input oninput={() => console.log("click!")} />;
<slot onslotchange={() => console.log("update slot!")} />;
```

### Listas simples

```jsx
<host>
  {[1, 2, 3].map((value) => (
    <span>{value}</span>
  ))}
</host>;
```

### Listas con clave

```jsx
<host>
  {[1, 2, 3].map((value) => (
    <span key={value}>{value}</span>
  ))}
</host>;
```

la propiedad key puede recibir valores del tipo de cualquier tipo que permita generar una referencia d el nodo, ejemplo:

```jsx
<host>
  {listaInmutable.map((objeto) => (
    <span key={objeto}>{objeto.value}</span>
  ))}
</host>;
```

### Propiedad shadowDom

Esta propiedad permite declarar el uso del shadowDom, ejemplo:

```jsx
<host shadowDom></host>;
// El uso de shadowDom no es esclusivo para el tag host 
// puede ser usado para cualquier nodo que lo soporte
<div shadowDom></div>;
```

### Asociación de métodos

Puede declarar un método declarando en el tag host una función  sin el uso del prefijo on en su nombre, ejemplo:

```jsx
// Template
<host myMethod={() => console.log("method!")}></host>;
// Uso desde el nodo
document.querySelector("my-component").myMethod();
```

Si al momento de la creacion o actualización del DOM no detecta la propiedad en el prototipo se asociara como un método del nodo permitiendo asi que este pueda ser recuperado desde el nodo, ejemplo:

```jsx
const myElement = new MyElement();

await myElement.updated;

myElement.myMethod();
```

Para acceder al DOM de forma segura espere la resolución de la propiedad updated creada por el [ciclo de render de Atomico](testing/test-dom.md)

