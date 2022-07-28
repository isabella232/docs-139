# @atomico/lottie

**Webcomponent** built with [Atomico JS](https://atomicojs.dev/) to use lottie as webcomponent. Includes additional support for React and Preact.



**Differences with lottie file**

1. Faster and smaller
2. Non-blocking, thanks to lazy loading.

### Modules

{% tabs %}
{% tab title="Default" %}
```javascript
import { Lottie } from "@atomico/components/lottie";
```
{% endtab %}

{% tab title="Elements" %}
```javascript
// Import that does not associate the tagName by default
import { Lottie } from "@atomico/lottie/elements";
```
{% endtab %}

{% tab title="React" %}
```javascript
import { Lottie } from "@atomico/components/lottie/react";
```
{% endtab %}

{% tab title="Preact" %}

{% endtab %}

{% tab title="Html CDN" %}

{% endtab %}
{% endtabs %}

### Properties

**cdn**: `boolean` , importa lottie-web desde un CDN, por default [https://cdnjs.cloudflare.com/ajax/libs/lottie-web/5.9.1/lottie.min.js](https://cdnjs.cloudflare.com/ajax/libs/lottie-web/5.9.1/lottie.min.js), este puede ser modificado mediante el objeto cdn existente en el modulo, por defecto es false.

**path**: string, path de la animacion, compatible con [lottiefile](https://lottiefiles.com/)

loop: boolean, la animacion se reproduce en loop.

lazyload: boolean, la animacion se descarga al ocurrir una intercepción

intersectionOffset : string ,define el offset para la carga por intercepcion o reproduccion de animacion

intersectionControl: boolean, si es true la animacion se reproducira solo en intercepción.&#x20;

intersectionControlReplay: boolean, cada intercepción reinicia la animación.&#x20;

### Examples

**React**

{% embed url="https://stackblitz.com/edit/atomico-lottie-react?file=src/App.tsx" %}
