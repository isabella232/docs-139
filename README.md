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

Atomico se presenta como una micro librería para un desarrollo moderno, con una curva baja curva de aprendizaje y sintaxis heredada de React, que busca solucionar los problemas tradicionales al momento de crear web-components de forma inteligente, algunos de los beneficios de Atomico son:

#### virtual-dom pensado para el web-component

El virtual-dom de Atomico se diferencia de otras bibliotecas\(Preact, Lit-html o React\), en que permite la manipulación desde el mismo contenedor asignado , en el caso general de Atomico el web-component, esto permite que ud declare el estado total del web-component desde el mismo virtual-dom mediante el tag host, ej:

```jsx
<host
    shadowDom 
    onclick={handler}
    styleSheet={style}
    >
    ...children
</host>
```

Done:

* host\[shadowDom\] : permite activar o desactivar el shadowDom de su web-component.
* host\[styleSheet\] : permite relacionar el css a un web-component de forma eficiente, usando por ejemplo Constructable Stylesheets cuando este disponible.
* host\[onclick\] : permite asociar un evento al web-component

#### Declaración de propiedades atributos como objeto

Atomico permite definir comportamientos especiales como : 

1. Validación de tipos en tiempo de ejecución. 
2. Reflejo de propiedades como atributos.
3. Valores por default.
4. Asociación de eventos simples y avanzados

```jsx
WebComponent.props = {
    myString : String, // 
    myObject : {
        type : Object,
        reflect : true,
        event : true,
        value : ()=>({...initialState})
    }
}
```

#### Hooks

Este patrón moderno le permitirá crear logica reutilizable  que mejora la experiencia de composición  funcional, este modelo de programacion supera las limitaciones naturales de una clase, sea contexto\(this\) y mejora la modularizacion de funcionalidades mediante custom-hooks\(scope logicos\).

#### Render asíncrono

Atomico procesa las actualizaciones de forma eficiente, agrupándola y ejecutándolas en función de la concurrencia, manejando las tareas de forma inteligente, esto logra un efecto similar al de React Fiber.

#### Tree shaking

Atomico posee código débilmente acoplado, lo que facilita la eliminación de funcionalidades y reducción de su tamaño sin generar conflicto.

#### Sistema de distribución moderno.

La distribución de Atomico es centralizada en un solo package en formato msj, esto permite que los módulos internos como atomico/html, atomico/use-lazy, atomico/use-router y otros.  se puedan ejecutar directo en el navegador, esto facilita la generación de prototipos, ej:

```javascript
import { customElement } from "https://unpkg.com/atomico";
import html from "https://unpkg.com/atomico/html"

function WebComponent(){
    return html`<host>no bundle!</host>`
}

customElement("my-tag",WebComponent);
```



