---
description: Implement SSR and SST without friction
---

# 💧 SSR / SSG

Atomico and automatic SSR support, you will not need additional packages, example:

```javascript
import "atomico/ssr";
import { html } from "atomico";
import { http } from "http";
import { MyComponent } from "./my-component";

http.createServer((req, res) {
  res.writeHead(200);
  res.end(html`
    <script src="./my-component" type="module"></script>
    <${MyComponent }>
      <h1>Yes, this is SSR with Atomico 🤯</h1>
    </${MyComponent }>
  `);
})
.listen(8080);

```

Unlike other libraries, Atomico automatically hydrates when mounting the component in the DOM, so no additional client configuration is required.

### SSR/SSG a travez de @atomico/react

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

