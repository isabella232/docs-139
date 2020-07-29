---
description: >-
  En esta  guía define un estándar para la generación de componentes con
  Atomico, con el objetivo facilitar el desarrollo colaborativo, escalabilidad y
  mantenimiento de sus componentes, lo entregado en
---

# Guías de estilo

### Estructura recomendada

La distribución del directorio es un elemento importante al momento de construir componentes, lo ideal es que este sea declarativo en contenido, ej:

```bash
src
├───components
│   └───${my-component}
│           ${my-component}.jsx
│           ${my-component}.css
│           ${my-component}.md
└───custom-hooks
    └───${my-hook}
            ${my-hook}.jsx
            ${my-hook}.md 
```

**Recuerde**

1. Sola incluya un componente por archivo.
2. Solo incluya un componente por directorio
3. Defina los custom-hooks de forma asilada a los componentes, en un archivo y directorio diferente, un archivo si puede contener mas de un hook

### Nombre de componente

Los componentes normalmente son unidades independientes

```bash
# Naming
${name}-${objective}-...
# Single
atomico-button
atomico-input
# Group
atomico-header
atomico-header-nav
atomico-header-logo
atomico-header-social
```

> El uso del nombre `atomico` es solo un ejemplo, no es recomendable su uso para la declaración de nombre de su componente.

### Declaración de componente

Los webcomponents son ideales para la generación de apis transparentes, permitiendo a trabes de attributos/propiedades manipular o conocer el estado actual del componente.

**Recuerde**

1. Defina siempre como nodo principal el tag `<host>`.
2. Prefiera el uso de `useProp` si ud busca manipular el estado de la prop y reflejar este en el webcomponent como atributo/propiedad, mantenga el uso de `useState` para estados privados.
3. Prefiera el uso de `reflect` si se busca transparentar el estado de su componente para un selector de css, eg `my-component[type="email"]` o `my-component[active]`
4. Prefiera el uso valores por default, si busca transparentar en todo momento el estado de su componente

**Ejemplo de componente**

```jsx
import { h, customElement, useProp } from "atomico";
import style from "./my-component.css";
/**
 * @type {import("atomico").Component}
 * @param {Object} props
 * @param {string} props.type
 * @param {value} props.value
 */
const MyComponent = ({ type }) => {
  let [value, setValue] = useProp("value");
  return (
    <host shadowDom>
      <style>{style}</style>
      <input
        type={type}
        value={value}
        oninput={({ target: { value } }) => setValue(value)}
      ></input>
    </host>
  );
};

MyComponent.props = {
  type: {
    type: String,
    reflect: true,
    options: ["number", "date", "email", "phone"],
    value: "text"
  },
  value: {
    type: String,
    value: "default message"
  }
};

export default customElement("my-component", MyComponent);

```

El uso de este fragmento `@type {import("atomico").Component}` en el jsdoc, importa las reglas de autocompletado para Typescript, **considérelo opcional**

