# Design systems

Atomico to facilitate the use of webcomponents through a functional API, but the result is always a Standard and Optimized Custom Element useful for representing design systems.

With Atomico you can achieve the following objectives:

1. **Scalable and reusable appearance**: with Atomico the code is simpler and you can apply practices that facilitate the reuse of your code.
2. **Open communication**: with Atomico you can communicate states by events, properties or methods.
3. **Agnostic**: your custom Element will work in any web-compatible library, eg React, Vue, Svelte or Angular.
4. **Performance**: Atomico has a comparative performance at Svelte levels, winning the third position in performance according to [**webcomponents.dev**](https://twitter.com/atomicojs/status/1391775734641745929) in a comparison of 55 libraries among which is React, Vue, Stencil and Lit.

I want to show you how Atomico behaves when used for the creation of DS \(Design System\), starting with a button.

```jsx
import { c, css } from "Atomico";

// Logic and template
function myButton() {
  return (
    <host shadowDom>
      <slot>button</slot>
    </host>
  );
}

// Properties and attributes
myButton.props = { small: { type: Boolean, reflect: true } };

// Static styles
myButton.styles = css`
  :host {
    font-size: var(--button-fontSize, 1rem);
    padding: var(--button-padding, 0.5rem 1rem);
    background: var(--button-background, #000);
    color: var(--button-color, #fff);
  }
`;

// CustomElement
export const MyButton = c(myButton);
```

From the example we will highlight the following practices:

1. `myButton.styles`: allows us to statically associate styles, this is highly efficient, because styles process only once and can be inherited.
2. The use of Custom properties \(css variables\) to reference properties of the css that we want to keep variables.
3. The button content is referenced by using the slot tag.
4. `MyButton` is a Custom Element, so it can be instantiated or extended.

Now suppose that this button is part of our design system, which we must modify before the arrival of a new project

### How to modify the appearance of my Custom element created with Atomico?

The techniques that you can apply with Atomico are:

1. Custom properties\(Variables de css\)
2. Herencia de clase
3. Selector part

Custom properties \(CSS variables\) 

These allow us to modify aspects already referenced through the customProperties declarations. The greatest potential of these is descending inheritance, example:

```markup
<style>
  .theme {
    --theme-primary: black;
    --button-background: var(--primary);
    --button-padding: 0.5rem 1rem;
  }

  .theme-dark {
    --theme-primary: #fff;
  }

  my-button[small] {
    --button-padding: 0.25rem 0.5rem;
    --button-fontSize: 0.75rem;
  }
</style>
<body class="theme">
  <my-button>content</my-button>
  <my-button small>content</my-button>
</body>
```

From the example we will highlight the following:

1. The selector `.theme` declares custom properties visible only to the selector, this has a positive effect vs: root because it reduces the name conflict of the custom properties and limits its use only to the associated container.
2. The `my-button[small]` selector activates custom properties only if we declare the `small` prop in the custom element instance.

### Class inheritance outside of Atomico

El custom element creado por atomico posee la propiedad `static get styles`, que ante una herencia permite modificar completamente la apariencia de su componente, ejemplo:

```javascript
import { css } from "atomico";
import { MyButton } from "./src/my-button/my-button.js";

class MyNewButton extends MyButton {
  static styles = [
    /**
     * super.styles permite cargar los estilos anteriores
     * esta propiedad estática es creada internamente por atomico
     */
    ...super.styles,
    /**
     * De la siguiente manera estamos asociados a un nuevo
     * styleSheet a nuestro customElement
     */
    css`
      :host {
        --button-background: teal;
      }
    `,
  ];
}
```

Del ejemplo destacaremos lo siguiente:

1. MyNewButton heredara todo del componente anterior props estilos siempre y cuando use `super.styles`.
2. El css creado asocia la customPropertie `--button-background: teal`, creando una variación en el componente principal.

**Esta herencia también es valida entre componentes de Atomico**, pero esta rescribirá el render, considérela si su busca referenciar variables de css o props\(Propiedades\).

**Selector ::part -** [**compatibilidad del 90%**](https://caniuse.com/mdn-api_element_part)\*\*\*\*

Este nos permite modificar la apariencia de los elementos dentro del shadowDOM que hagan uso del atributo `part="<identificador>"`,  ejemplo:

```jsx
import { c } from "atomico";

function card() {
  return (
    <host shadowDom>
      <header part="header">
        <slot name="header" />
      </header>
    </host>
  );
}

customElements.define("my-card", c(card));
```

Gracias al uso del atributo `part`, podremos modificar toda la apariencia del Elemento que referencie el atributo, ejemplo:

```css
my-card::part(header){
    padding: 1rem;
    font-size: 50px;
}

```

Es probable de que su componente posea apariencias variables, ejemplo un modo dark y el problema es que part limita su efecto a solo a estados nativos, por lo que \`::part\(header\).dark\` no funcionara, para escapar de esto solo aplique lógica en su plantilla, ejemplo

```jsx
function card({ dark }) {
  return (
    <host shadowDom>
      <header part={dark ? "theme-dark" : "theme"}>
        <slot name="header" />
      </header>
    </host>
  );
}

cart.props = {
  dark: Boolean,
};
```

### Conclusión

hemos conocido brevemente el como  a estilizar componentes para sistemas de diseño, en la siguiente guía conocerás como estructurar y documentar Sistemas de diseño 

