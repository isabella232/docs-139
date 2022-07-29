# @atomico/lottie

**Webcomponent** built with [Atomico JS](https://atomicojs.dev/) to use lottie as webcomponent. Includes additional support for React and Preact.

{% embed url="https://codepen.io/uppercod/pen/MWVOOxW" %}

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
```html
<script 
    type="module" 
    src="http://esm.sh/@atomico/lottie"></script>
    
<atomico-lottie></atomico-lottie>
```
{% endtab %}
{% endtabs %}

### Properties

**cdn**: `boolean` , import lottie-web from a CDN, by default [https://cdnjs.cloudflare.com/ajax/libs/lottie-web/5.9.1/lottie.min.js](https://cdnjs.cloudflare.com/ajax/libs/lottie-web/5.9.1/lottie.min.js), this can be modified through the existing cdn object in the module, by default it is false.

**path**: `string`, animation path, compatible with lottiefiles

**loop**: `boolean`, the animation plays in a loop.

**lazyload**: `boolean`, the animation is downloaded when an interception occurs

**intersectionOffset** : `string`, defines the offset for interception loading or animation playback.

**intersectionControl**: `boolean`, if true the animation is played only on interception.

**intersectionControlReplay**: `boolean`, each intercept restarts the animation.

### Examples

**React**

{% embed url="https://stackblitz.com/edit/atomico-lottie-react?file=src/App.tsx" %}
