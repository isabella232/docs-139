---
description: >-
  First thanks for using Atomico 😉, in this guide you will find some useful
  tips when developing with Atomico, all with the aim that your webcomponents
  are sustainable and scalable over time.
---

# 🗺 Atomico style guide

### 1. Recommended file structure for webcomponents

you always prefer to keep each component isolated in a directory with names associative to the same component, example:

```
├── my-button
│   ├── my-button.{js,jsx,ts,tsx}
│   ├── my-button.test.{js,jsx,ts,tsx}
│   ├── my-button.stories.js
│   └── my-button.md
└── my-input
    ├── my-input.{js,jsx,ts,tsx}
    ├── my-input.test.{js,jsx,ts,tsx}
    ├── my-input.stories.js
    └── my-input.md
```

**why?** The NPM-oriented [`@atomico/exports`](../atomico/atomico-exports/atomico-exports.md) packaging tool allows automatic export from the recommended structure,`@atomico/exports` will generate a modern package.json to current standards, automatically generating all (main, types, exports and more) what is necessary for your package to be distributed correctly.

### 2. Component name as function.

```jsx
function myButton() {
  return <host />;
}

const MyButton = c(myButton);
```

you prefer to use camelCase(`myButton`) to declare your function as webcomponent and the resulting customElements from function c in PascalCase (Button).

**why?** `MyButton` is the only one that can be instantiated as a constructor of the web component, example:

```js
// Vanilla JS
const node = new MyButton();

//JSX
<MyButton />;
```

### 3. Prefers the use of static style

```jsx
function component() {
  return <host shadowDom />;
}

component.styles = css`
  :host {
    display: block;
  }
`;
```

This does not rule out the use within the style tag, since it is sometimes the solution to the definition of conditional styles or variables to the logic and outside the scope of the custom properties.
