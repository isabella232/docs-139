---
description: >-
  This guide will know the essentials to start developing webcomponents with
  Atomico
---

# 🚀 Getting started with Atomico

Thanks for being here and getting started with Atomico. Let's talk a little about what Atomico offers today: 

1. Development agility, Atomico's functional approach simplifies code at all stages of development. 
2. Lightweight inside and out, Atomico allows you to create a component with less code and with a low dependency impact. Approximately 3kb. 
3. Really fast, Atomico has a [good performance](https://twitter.com/atomicojs/status/1391775734641745929) in the browser and an agile development experience. Let's understand what a webcomponent created with Atomico looks like:

```javascript
// IMPORT
import { c, html, css } from "atomico";

// WEBCOMPONENT
function component({ message }) {
  return html`<host shadowDom>${message}</host>`;
}

// WEBCOMPONENT PROPERTIES AND ATTRIBUTES
component.props = {
  message: String,
};

// WEBCOMPONENT APPEARANCE
component.styles = css`
  :host {
    font-size: 30px;
  }
`;

// DEFINITION OF THE WEBCOMPONENT AS A TAG
customElements.define("my-component", c(component));
```

Let's analyze the code in parts ...

### Import <a id="importacion"></a>

```javascript
import { c, html, css } from "atomico";
```

What have we imported?

1. `c`: Function that transforms the functional component into a standard customElement.
2. `html`: Function to declare the template of our component, you can also use JSX.
3. `css`: Function that allows creating the CSSStyleSheet \(CSS\) for our component as long as it declares the shadowDom.

### Webcomponent <a id="webcomponent"></a>

```javascript
function component({ message }) {
  return html`<host shadowDom>${message}</host>`;
}
```

Our component function receives all the props \(Properties and Attributes\) declared in component.props, the component function declares all the logic and template of the webcomponent. An important rule within Atomico is **"every component created with Atomico must always return the  tag"**.

### Reactive properties and attributes of the webcomponent

Atomico detects the prop \(Properties and Attributes\) of the component thanks to the association of the props object, this through the use of index and value allows you to define:

1. **index**: Name of the property and attribute.
2. **value**: type of the prop.

```javascript
component.props = {
  message: String,
};
```

From the example we can infer that Atomico will create in our webcomponent a property and attribute called `message` and this can only receive values of the `String` type.

### Appearance of the webcomponent.

Atomico detects the static styles of your component thanks to the association of the `styles` property:

```javascript
component.styles = css`
  :host {
    font-size: 30px;
  }
`;
```

styles accepts individual or list CSSStyleSheet \(CSS\) values, the return from the css function is a standard CSSStyleSheet, so it can be shared outside of Atomico.

### Definition of your webcomponent

```javascript
customElements.define("my-component", c(component));
```

To create our standard customElement we will have to deliver our functional component to the c function of the Atomico module, the `c` function will generate as a return a customElement that can be defined or extended.

### Example <a id="ejemplo"></a>

{% embed url="https://webcomponents.dev/edit/collection/wuKH7azM3kT3jqKv9ZV9/7dNVyEXrCpmpKF9NXAAY/src/index.jsx" %}



[  
](https://atomico.gitbook.io/doc/v/es/)

