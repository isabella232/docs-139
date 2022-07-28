# Design systems

Al crear sistemas de diseño o sistemas de componentes, como te recomendamos mantener una estructura de distribución centralizada en un solo package de exportación con múltiples path de importación

{% tabs %}
{% tab title="Caso 1" %}
```javascript
import { Button, Input } from "my-ds";
```
{% endtab %}

{% tab title="Caso 2" %}
```javascript
import { Button } from "my-ds/button";
import { Input } from "my-ds/input";
```
{% endtab %}
{% endtabs %}

### What are the benefits of this type of distribution?

Aesthetic coherence, the entire design system leverages itself and thanks to this we gain aesthetic coherence.

While a monorepo might seem like an ideal path, it actually increases the complexity of maintenance, whether it be component versioning and dependency maintenance.

We move faster and reduce implementation errors if you don't rely on individual versioning at the component level and leave this only defined at the design system level.

This has its pros and cons:

**Pros:**&#x20;

1. It speeds up the creation of components, since it avoids the individual publication process and centralizes all this at the design system level.

**Cons**

1. you will not be able to update a component individually, since it is leveraged at the design system level.



### Recommended file structure for webcomponents

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

**why?** The NPM-oriented [`@atomico/exports`](../../../atomico/atomico-exports.md) packaging tool allows automatic export from the recommended structure,`@atomico/exports` will generate a modern package.json to current standards, automatically generating all (main, types, exports and more) what is necessary for your package to be distributed correctly.
