---
description: The Keen-slider api but with WebComponents
---

# @atomico/keen-slider

**Webcomponent** built with [Atomico JS](https://atomicojs.dev/) to use [keen-slider](https://keen-slider.io/) as webcomponent. Includes additional support for React and Preact.

{% embed url="https://codepen.io/uppercod/pen/MWVENee" %}

{% embed url="https://github.com/atomicojs/components/tree/master/src/components/keen-slider" %}

### Modulo

{% tabs %}
{% tab title="Default" %}
```javascript
import { KeenSlider } from "@atomico/keen-slider";
```


{% endtab %}

{% tab title="Elements" %}
```javascript
// Import that does not associate the tagName by default
import { KeenSlider } from "@atomico/keen-slider/elements";
```
{% endtab %}

{% tab title="React" %}
```javascript
import { KeenSlider } from "@atomico/keen-slider/react";
```
{% endtab %}

{% tab title="Preact" %}
```javascript
import { KeenSlider } from "@atomico/keen-slider/preact";
```
{% endtab %}

{% tab title="CDN" %}
```html
<script 
    type="module" 
    src="http://esm.sh/@atomico/keen-slider"></script>
```
{% endtab %}
{% endtabs %}

### Properties / attributes

| Prop/Attr                       | Type / default                  | Description |
| ------------------------------- | ------------------------------- | ----------- |
| loop                            | boolean                         |             |
| drag                            | boolean                         |             |
| disabled                        | boolean                         |             |
| vertical                        | boolean                         |             |
| rtl                             | boolean                         |             |
| rubberband                      | boolean                         |             |
| autoplay                        | boolean                         |             |
| autoplayLoop / autoplay-loop    | number / 2000                   |             |
| initial                         | number                          |             |
| mode                            | "snap" \| "free" \| "free-snap" |             |
| slidesPerView / slides-per-view | string                          |             |
| slidesSpacing / slides-spacing  | string                          |             |
| slidesOrigin / slides-origin    | string                          |             |
| slider                          | KeenSliderInstance              |             |

### Events

**CreateSlider**

dispatched when defining the slider prop, useful for accessing the keen-slider instance

### Methods

`KeenSlider.next()`

next slide

`KeenSlider.prev()`

prev slide

****
