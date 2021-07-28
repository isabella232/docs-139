# ✨ Design systems

Atomico to facilitate the use of webcomponents through a functional API, but the result is always a Standard and Optimized Custom Element useful for representing design systems.

With Atomico you can achieve the following objectives:

1. **scalable and reusable interfaces**: with Atomico the code is simpler and you can apply practices that facilitate the reuse of your code.
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

Now suppose that `MyButton` button is part of our design system and we must modify before the arrival of a new project but without completely rewriting the code.

## How to modify the appearance of my Custom element created with Atomico?

The techniques that you can apply with Atomico are:

1. Custom properties\(Variables de css\)
2. Herencia de clase
3. Selector part

### Custom properties \(CSS variables\) 

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

The custom element created by atomico has the static get styles property, which before an inheritance allows to completely modify the appearance of its component, example:

```javascript
import { css } from "atomico";
import { MyButton } from "./src/my-button/my-button.js";

class MyNewButton extends MyButton {
  static styles = [
    /**
     * super.styles allows to load the previous styles
     * this static property is created internally by atomico
     */
    ...super.styles,
    /**
     * In the following way we are associated with a new
     * styleSheet to our customElement
     */
    css`
      :host {
        --button-background: teal;
      }
    `,
  ];
}
```

From the example we will highlight the following:

1. MyNewButton heredara todo del componente anterior props estilos siempre y cuando use `super.styles`.
2. The created css associates the custom properties `--button-background: teal`, creating a variation on the main component.

Learn more about inheritance in the [**class inheritance guide**](../class-inheritance.md)\*\*\*\*

### **Selector ::part**

This allows us to modify the appearance of the elements within the shadowDOM that make use of the `part="<identificador>"` attribute, example:

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

Thanks to the use of the part attribute, we will be able to modify the entire appearance of the Element that the attribute references, example:

```css
my-card::part(header){
    padding: 1rem;
    font-size: 50px;
}

```

It is probable that your component has variable appearances, for example a dark mode and the problem is that part limits its effect to only a [**pseudoclass**](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes), to escape this limitation you can use the reflect property in the props \(Properties\) of your component, example:

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

Atomico seeks to facilitate the creation of useful webcomponents for design systems in the following guide you will learn how to structure and document Design Systems

