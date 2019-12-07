---
description: >-
  Atómico es una micro librería de 3.7kB que permite la creación de
  web-components a base de código funcional potenciado con el uso de Props y
  Hooks
---

# Introducción

### Vista general

```jsx
import { h, customElement } from "atomico";

function WebComponent({ value }) {
  return <host>Hi! {value}!</host>;
}

WebComponent.props = {
  value: { type: String, value: "Atomico" }
};

customElement("any-name", WebComponent);

```

### ¿Por que Atomico?

Atómico se presenta como una micro librería para  un desarrollo moderno, con una curva de aprendizaje baja, logica altamente componetizable y sintaxis heredada de React, algunos de los beneficios de Atomico son: 

#### virtual-dom pensado para el web-component

Atomico introduce el uso del tag `host`, el que permite manipular el estado del web-component, como cualquier nodo del virtual-dom, ej:

```jsx
<host
    shadowDom 
    onclick={handler}
    styleSheet={style}
    >
    ...inside web-component
</host>
```

#### Propiedades como objeto

Ud podra declarar propiedades y atributos mediante un objeto, esto beneficia le uso de validación de tipos, reflejo de propiedades como atributos, valores por default, asociación de eventos y más.

#### Render asíncrono

Atomico procesa las actualizaciones de forma eficiente, agrupándola y ejecutándolas en función de la concurrencia, esto logra un efecto similar al de React Fiber.

#### Tree shaking

Atomico posee código débilmente acoplado, lo que facilita la eliminación de funcionalidades y reducción de su tamaño sin generar conflicto.

#### Ejecutable en browser

La distribución de Atomico es centralizada en un solo package, esto permite que los módulos internos como atomico/html, atomico/use-lazy, atomico/use-router y otros.  se puedan ejecutar directo en el navegador, esto facilita la generación de prototipos, ej:

```javascript
import { customElement } from "https://unpkg.com/atomico";
import html from "https://unpkg.com/atomico/html"

function WebComponent(){
    return html`<host>no bundle!</host>`
}

customElement("my-tag",WebComponent);
```







 









