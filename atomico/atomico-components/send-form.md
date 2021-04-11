---
description: Send forms using fetch and know the status of this and its response
---

# send-form

## Modulo

```javascript
import {
  SendForm, // HTMLElement
} from "@atomico/components/send-form";
```

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

| Props       | Tipo                                           | Descripción                                                              |
| :---------- | :--------------------------------------------- | :----------------------------------------------------------------------- |
| response    | Any                                            | Refleja la respuesta del fetch en la propiedad response.                 |
| action      | String                                         | destino del request                                                      |
| json        | Boolean                                        | Envia el contenido serializado en JSON, por defecto se envia el FormData |
| mode        | String                                         | Request.mode                                                             |
| cache       | String                                         | Request.mode                                                             |
| headers     | Object                                         | Request.mode                                                             |
| method      | String                                         | Request.mode                                                             |
| credentials | String                                         | Request.mode                                                             |
| status      | `"" \| "pending" \| "rejected" \| "fulfilled"` | Promise.status                                                           |
