# Design systems

Al crear sistemas de diseño o sistemas de componentes, Atomico recomienda mantener una estructura de distribución centralizada en un solo package de exportacion con múltiples path de importación

{% tabs %}
{% tab title="Caso 1" %}
```
import { Button, Input } from "my-ds";
```
{% endtab %}

{% tab title="Caso 2" %}
```
import { Button } from "my-ds/button";
import { Input } from "my-ds/input";
```
{% endtab %}
{% endtabs %}

### Que gano con esta distribución

Coherencia estética, todo el sistema de diseño se apalanca en si mismo, ya que es un lenguaje  composición de la interfaz en el que la apariencia del componente esta apalancada a dicho sistema, gracias a esto ganamos coherencia estética.&#x20;

Si bien un monorepo podría parecer un camino ideal, realmente eleva la complejidad de mantenimiento, sea por versionamiento de los componentes y Mantenimiento de dependencias.

Entendiendo lo anterior te pregunto ¿ si un organismo requiere la existencia de una célula podemos prescindir de ella para componer dicho organismo? la respuesta es No, esto es lo que sucede con los sistemas de diseño.&#x20;

Avanzaras mas rapido y reducirás los errores de implementación si no dependes de un versionamiento individual a nivel de componente y dejas esto solo definido a nivel de sistema de diseño.

Esto tiene sus pros y contras:

**Pros:**&#x20;

1. Acelera la creacion de componentes, ya que evita el proceso de publicación individual y centraliza todo esto a nivel sistema de diseño.

**Contras**

1. no podrás actualizar un componente de forma individual, ya que este esta apalancado a nivel de sistema de diseño.



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
