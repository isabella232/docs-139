---
description: >-
  Atomico is a micro library of 3.7kB in size that allows the creation of
  web-components based on functional code enhanced with the use of Props and
  Hooks
---

# Atomico

### Overview

```jsx
import { h, customElement } from "atomico";

function WebComponent({ value }) {
  return <host>Hi! {value}!</host>;
}

WebComponent.props = {
  value: String
};

customElement("any-name", WebComponent);

```

### Why Atomico?

Atomico is presented as a micro library for a modern development, with a low learning curve and syntax inherited from React, which seeks to solve traditional problems when creating web-components intelligently, some of the benefits of Atomico are:

#### virtual-dom designed for the web-component

The Atomico [**virtual-dom**](guides/virtual-dom.md) differs from other libraries \(Preact, Lit-html or React\), in that it allows manipulation from the same assigned container, in the general case of Atomico the web-component, this allows you to declare the state of the web-component from the same virtual-dom using the host tag, eg:

```jsx
<host
    shadowDom 
    onclick={handler}
    styleSheet={style}
    >
    ...inside web-component
</host>
```

Where:

* `host[shadowDom]` : Allows you to enable or disable the shadowDom of your web-component.
* `host[styleSheet]` : allows you to relate the css to a web-component efficiently, using for example Constructable Stylesheets when available.
* `host[onclick]` : allows you to associate an event with the web-component

#### Declaration of properties and attributes using an object

Atomico allows to define special behaviors such as:

1.  Type validation at runtime
2. Reflection of properties such as attributes, 
3. Default values.
4. Automatic event system with simple or advanced configuration

```javascript
WebComponent.props = {
    myString : String, // basic statement
    myObject : {       // advanced statement
        type : Object,
        reflect : true,
        event : true,
        value : ()=>({...initialState})
    }
}
```

#### Hooks

This modern pattern will allow you to create reusable logic that improves the experience of functional composition, this programming model overcomes the natural limitations of a Class such as context\(this\) and improves the modularization of functionalities through custom-hooks\(logical scope\).

#### Asynchronous render

Atomico processes the updates efficiently, grabbing it and running according to the concurrence, this achieves an effect similar to that of React Fiber.

#### Tree shaking

Atomico has weakly coupled code, which facilitates the elimination of functionalities and reduction of its size without generating conflict.

#### Modern distribution system

The distribution of Atomico is centralized in a single package, this allows internal modules such as atomico/html, atomico/use-lazy, atomico/use-router and others. can be run directly in the browser, this facilitates the generation of prototypes, eg:

```javascript
import { customElement } from "https://unpkg.com/atomico";
import html from "https://unpkg.com/atomico/html"

function WebComponent(){
    return html`<host>no bundle!</host>`
}

customElement("my-tag",WebComponent);
```

