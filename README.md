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

Atomico is presented as a micro library for a modern development, with a low learning curve and syntax inherited from React, some of the benefits of Atomico are:

#### virtual-dom designed for the web-component

Atomico introduces the use of the `host` tag and the use of special properties such as `shadowDom` or `styleSheet` that allows you to better manipulate the state of the web-component, eg:

```jsx
<host
    shadowDom 
    onclick={handler}
    styleSheet={style}
    >
    ...inside web-component
</host>
```

#### Declaration of properties and attributes using an object

Atomico allows you to define special behaviors such as type validation, reflection of properties such as attributes, default values, association of events and more.

#### Hooks

This modern pattern will allow you to create reusable logic that improves the experience of functional composition

#### Asynchronous render

Atomico processes the updates efficiently, grabbing it and running according to the concurrence, this achieves an effect similar to that of React Fiber.

#### Tree shaking

Atomico has weakly coupled code, which facilitates the elimination of functionalities and reduction of its size without generating conflict.

#### Use without bundle tools

The distribution of Atomico is centralized in a single package, this allows internal modules such as atomico/html, atomico/use-lazy, atomico/use-router and others. can be run directly in the browser, this facilitates the generation of prototypes, eg:

```javascript
import { customElement } from "https://unpkg.com/atomico";
import html from "https://unpkg.com/atomico/html"

function WebComponent(){
    return html`<host>no bundle!</host>`
}

customElement("my-tag",WebComponent);
```

