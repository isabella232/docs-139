# lottie

## Modulo

{% tabs %}
{% tab title="Default" %}
```javascript
import { Lottie } from "@atomico/components/lottie";
```
{% endtab %}

{% tab title="React" %}
```javascript
import { Lottie } from "@atomico/components/lottie/react";
```
{% endtab %}
{% endtabs %}

## Example

{% tabs %}
{% tab title="HTML" %}
```markup
<atomico-lottie
    cdn
    path="https://labs.nearpod.com/bodymovin/demo/markus/halloween/markus.json"
></atomico-lottie>

```
{% endtab %}

{% tab title="JSX" %}
```javascript
import { Lottie } from "@atomico/components/lottie";

<Lottie 
    cdn
    path="https://labs.nearpod.com/bodymovin/demo/markus/halloween/markus.json"
></Lottie>

```
{% endtab %}
{% endtabs %}
