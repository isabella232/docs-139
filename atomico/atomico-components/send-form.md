---
description: Send forms using fetch and know the status of this and its response
---

# send-form

## Modulo

{% tabs %}
{% tab title="Default" %}
```javascript
import {
  SendForm // HTMLElement
} from "@atomico/components/send-form";
```
{% endtab %}

{% tab title="React" %}
```javascript
import {
  SendForm 
} from "@atomico/components/send-form.react";
```
{% endtab %}
{% endtabs %}

## Example

{% tabs %}
{% tab title="HTML" %}
```markup
<send-form action="https://api.any/data" json>
    <form>
        <input type="text"/>
        <button>Enviar</button>
    </form>
    <h1 slot="pending">Loading...</h1>
    <h1 slot="rejected">rejected!</h1>
    <h1 slot="fulfilled">fulfilled!</h1>
</send-form>
```
{% endtab %}

{% tab title="IMPORT" %}
```javascript
import {
  SendForm, // HTMLElement
} from "@atomico/components/send-form";

customElements.define("send-form", SendForm);
```
{% endtab %}
{% endtabs %}

### Properties

| Property    | Type                                           | Description                                                           |
| ----------- | ---------------------------------------------- | --------------------------------------------------------------------- |
| response    | Any                                            | Reflect the response of the fetch in the response property.           |
| action      | String                                         | Request destination                                                   |
| json        | Boolean                                        | Sends the content serialized in JSON, by default the FormData is sent |
| mode        | String                                         | Request.mode                                                          |
| cache       | String                                         | Request.mode                                                          |
| headers     | Object                                         | Request.mode                                                          |
| method      | String                                         | Request.mode                                                          |
| credentials | String                                         | Request.mode                                                          |
| status      | `"" \| "pending" \| "rejected" \| "fulfilled"` | Promise.status                                                        |
