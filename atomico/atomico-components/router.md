---
description: Manage routes for applications simply and declaratively.
---

# router

## Modulo

```javascript
import {
  getPath, // ()=>string
  redirect, // (path:string)=>void
  RouterCase, // HTMLElement
  RouterSwitch, // HTMLElement
  RouterRedirect, // HTMLElement
} from "@atomico/components/router";
```

## Example

{% tabs %}
{% tab title="HTML" %}
```markup
<router-redirect>
    <a href="/">home</a>
    <router-switch>
        <router-case path="/" load="./component.js"></router-case>
        <router-case path="/[...notFound]" for="notFound"></router-case>
        <h1 slot="notFound">Not Found</h1>
    </router-switch>
</router-redirect>
```
{% endtab %}

{% tab title="IMPORT" %}
```javascript
import {
  RouterCase,
  RouterSwitch,
  RouterRedirect,
} from "@atomico/components/router";

customElements.define("router-redirect", RouterRedirect);
customElements.define("router-switch", RouterSwitch);
customElements.define("router-case", RouterCase);
```
{% endtab %}
{% endtabs %}

### router-redirect

Redirect every `onclick` event that declares the`href` property in its target, example tag `<a>`.

| Property | Type | Description |
| :--- | :--- | :--- |
| path | String | Define a `path` to concatenate to the nested`path`, either by redirection or router-switch. |

### router-switch

Controla la ruta a mostrar o montar según la expresión del path

| Property | Type | Description |
| :--- | :--- | :--- |
| path | String | Define a `path` to concatenate to the nested`path`, either by redirection or router-switch. |

### router-case

| Property | Type | Description |
| :--- | :--- | :--- |
| load | \`String | \(\)=&gt;Promise\` |
| for | String | Content to show at the time of the match by `path`,`for` must point to a slot within the parent. |

### router-link

Allows redirection in shadowDOM situations, `router-link` will inherit the top `path` from `router-redirect` or `router-switch`.

| Property | Type | Description |
| :--- | :--- | :--- |
| href | String | path a enviar a redirect |

