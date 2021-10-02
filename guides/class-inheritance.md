# Class inheritance

### Classes external to Atomico

```javascript
import { c, html } from "atomico";

function component() {
  return html`<host shadowDom> ...my content </host>`;
}

class VanillaElement extends HTMLElement {
  constructor() {
    super();
    console.log("create");
  }
  connectedCallback() {
    console.log("mount");
  }
  disconnectedCallback() {
    console.log("mount");
  }
  attributeChangedCallback() {
    console.log("my-attr update");
  }
  static get observedAttributes() {
    return ["my-attr"];
  }
  // ⚠️ not native but valid within Atomico.
  // this is just an example the ideal is to 
  // have a shared reference of the CSSStyleSheet
  static get styles(){
    const sheet= new CSSStyleSheet();
    sheet.replace('a { color: blue; }');
    return sheet;
  }
}


const Component = c( component,  VanillaElement );
```

`component`: function that declares the webcomponent for Atomico. 

`VanillaElement`: class that will be extended by Atomico to create Component, Atomico will not break the life cycle of the component, allowing them to interact freely.

### Classes internal to Atomico

classes produced by the Atomico function `c`, these can be extended between components, example:

```javascript
import { c, html, css } from "atomico";

function component1({ prop1 }) {
  return html`<host shadowDom> ...my content, ${prop1} </host>`;
}

component1.props = {
  prop1: String,
};

component1.styles = css`
  :host {
    font-size: 100px;
  }
`;

function component2({ prop1, prop2 }) {
  return html`<host shadowDom> ...my content, ${prop1} and ${prop2} </host>`;
}

component2.props = {
  prop2: String,
};

const Component1 = c(component1);

const Component2 = c(component2, Component1);

customElements.define("component-2", Component2);

```

Consider the following effects when using this inheritance model:

1. The `render` will be rewritten. 
2. The `props` are inherited, Atomico will reuse the previously declared props. 
3. `Styles` are inherited. Atomico will merge the stylesheets.

### Inheritance outside of Atomico

The `c` function creates an optimized standard custom element, which can be extended to modify its behavior, be:

1. Adding methods.
2. Creating or replacing style sheets.
3. Creando nuevas propiedades.

Suppose we have a `MyButton` product of the function `c`, we can extend this component to modify its appearance without the need to completely rewrite it, example:

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

The benefit of this inheritance is to simplify the modification of the appearance of a component created with Atomico, since it avoids its rewriting.

