---
description: estándar para la generación de componentes con Atomico
---

# Guías de estilo

En esta  guía define un estándar para la generación de componentes con Atomico, con el objetivo facilitar el desarrollo colaborativo, escalabilidad y mantenimiento de sus componentes, lo entregado en esta guía no se define como regla, ya que lo aplicado puede variar entre desarrollador.

### Estructura recomendada

La distribución directorio es un elemento importante al momento de construir componentes, lo ideal es que este sea declarativo en contenido, eg:

```bash
src
├───components
│   └───${my-component}
│           ${my-component}.js
│           ${my-component}.css
│           ${my-component}.md # export with dev:doc
└───custom-hooks
    └───${my-hook}
            ${my-hook}.js
            ${my-hook}.md # export with dev:doc
```

**Recuerde**

1. Sola incluya un componente por archivo.
2. Solo incluya un componente por directorio
3. Defina los custom-hooks de forma asilada a los componentes, en un archivo y directorio diferente, un archivo si puede contener mas de un hook

### Nombre de componente

Es ideal que como autor ud **defina un nombre o prefijo que agrupé uno o mas componente**, siempre defina a continuación del nombre principal el objetivo a representar en la UI, ej:

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
​
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
```



