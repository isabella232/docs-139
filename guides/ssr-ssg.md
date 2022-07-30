---
description: Implement SSR and SST without friction
---

# 💧 SSR / SSG

### Node

Atomico and automatic SSR support, you will not need additional packages, example:

{% tabs %}
{% tab title="Example" %}
{% embed url="https://stackblitz.com/edit/atomico-ssr-express?embed=1&file=index.js&hideExplorer=1&view=preview" %}
{% endtab %}

{% tab title="Express js" %}
```javascript
// If your version of node accepts top-level await just point to 'atomico/ssr'
import 'atomico/ssr/load'; 
import { html } from 'atomico';
import { Component } from './static/component.js';
import express from 'express';

const app = express();
const port = 3010;

app.use(express.static('static'));

app.get('/', (req, res) => {
  res.send(`
    <script type="importmap">
    {
      "imports": {
        "atomico": "https://unpkg.com/atomico"
      }
    }
    </script>
    <script src="./component.js" type="module"></script>
    ${html`<${Component} value=${100}>
      <h1>Message from server!</h1>
     </${Component}>`.render()}
  `);
});

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`);
});

```
{% endtab %}

{% tab title="Component.js" %}
For this case we are using a JS-only component to avoid compilation in the example. you can achieve the same with JSX or TSX.

&#x20;

```javascript
import { c, html, css, useProp } from 'atomico';

function component() {
  const [value, setValue] = useProp('value');
  return html`<host shadowDom>
    <h1>Atomico webcomponent</h1>    
    <button onclick=${() => setValue(value + 1)}>${value} Increment</button>
    <slot/>
  </host>`;
}

component.props = {
  value: { type: Number, value: 0 },
};

component.styles = css`
  :host{
    font-size: 32px;
    font-family: arial;
  }
`;

export const Component = c(component);

customElements.define('my-element', Component);

```
{% endtab %}

{% tab title="package.json" %}
You will not need any additional package, atomic internally understands that the component must be hydrated



```json
{
  "name": "node-starter",
  "type": "module",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "@atomico/site": "^0.1.0",
    "atomico": "^1.61.1",
    "express": "^4.17.1"
  }
}

```
{% endtab %}
{% endtabs %}

Unlike other libraries, Atomico automatically hydrates when mounting the component in the DOM, so no additional client configuration is required.

{% hint style="info" %}
Remember that for node Node without tools like Next.js, Fresh or Astro you should import the path `atomico/ssr/load` from the server
{% endhint %}

### SSR/SSG via @atomico/react

The @atomico/react package allows you to take advantage of support for SSR or SSG designed for React/Preact, example:

1. **Next.js**:&#x20;
   * Example: [https://example-next-js-mocha.vercel.app/](https://example-next-js-mocha.vercel.app/)
   * Repo: [https://github.com/atomicojs/example-next-js](https://github.com/atomicojs/example-next-js)
2. **Fresh**:&#x20;
   * Example: [https://atomico-webcomponents-tgd58wd8ntcg.deno.dev/](https://atomico-webcomponents-tgd58wd8ntcg.deno.dev/)
   * Repo: [https://github.com/atomicojs/example-fresh-deno](https://github.com/atomicojs/example-fresh-deno)

### **Astro build**

[@atomico/astro](https://github.com/atomicojs/astro) allows to integrate SSR and SSG support to Astro build, We have used this integration to create the [atomicojs.dev](https://atomicojs.dev/) site.

{% embed url="https://github.com/atomicojs/atomicojs.dev" %}

