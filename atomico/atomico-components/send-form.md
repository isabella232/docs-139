# lottie

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
