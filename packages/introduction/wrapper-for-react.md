# Wrapper for React

Atomico allows distributing webcomponnets with extended react support, automatically creating wrappers for each component and import paths for react.&#x20;

For this to be possible you must follow the following rules.

### 1. The file that declares the customElement must export the customElement.

{% tabs %}
{% tab title="Ejemplo 1" %}
```javascript
import {Component} from "./component";
export {Component} from "./component";

customElements.define("my-component", MyComponent);
```
{% endtab %}

{% tab title="Ejemplo 2" %}
```javascript
import {c} from "./my-component";

function component(){
    return <host></host>;
}

export const Component = c(c);

customElements.define("my-component", Component);
```
{% endtab %}
{% endtabs %}

### 2. The expression for exports must point to the declaration files and associate the export flags.

```
exports ./src/components/*/*.{jsx,js} --types --analyzer --exports
```

Remember that the use of the --types flag requires the local or global installation of Typescript



The result of this process will be:

1. The association of exports for React inside the package.json
2. The creation of the files of use for React, if the component is created with Atomico adds support to types.
