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

most of the properties are homologous to [keen-slider documentation](https://keen-slider.io/docs)

| Prop/Attr                           | Type / default                  | Description                                                                                                                                                      |
| ----------------------------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **loop**                            | boolean                         | Enables or disables carousel/loop functionality of the slider.                                                                                                   |
| **drag**                            | boolean                         | Enables or disables mouse and touch control. Default is **tru**                                                                                                  |
| **disabled**                        | boolean                         |                                                                                                                                                                  |
| **vertical**                        | boolean                         | Changes the direction of the slider from horizontal to vertical. (Note: The height of the `container` must be defined if vertical is true) Default is **false**. |
| **rtl**                             | boolean                         | Changes the direction in which the slides are positioned, from left-to-right to right-to-left. Default is **false**.                                             |
| **rubberband**                      | boolean                         | Enables or disables the rubberband behavior for dragging and animation after a drag. Default is **tr**                                                           |
| **autoplay**                        | boolean                         |                                                                                                                                                                  |
| **autoplayLoop / autoplay-loop**    | number / 2000                   |                                                                                                                                                                  |
| **initial**                         | number                          |                                                                                                                                                                  |
| **mode**                            | "snap" \| "free" \| "free-snap" |                                                                                                                                                                  |
| **slidesPerView / slides-per-view** | string                          |                                                                                                                                                                  |
| **slidesSpacing / slides-spacing**  | string                          |                                                                                                                                                                  |
| **slidesOrigin / slides-origin**    | string                          |                                                                                                                                                                  |
| **slider**                          | KeenSliderInstance              |                                                                                                                                                                  |

The slidesPerView, slidesSpacing and slidesOrigin props accept responsive expressions, example:

```html
<atomico-keen-slider 
    slider-per-view="1, 2 520px, 3 720px"
></atomico-keen-slider>
```

### Events

**CreateSlider**

dispatched when defining the slider prop, useful for accessing the keen-slider instance

### Methods

`KeenSlider.next()`

next slide

`KeenSlider.prev()`

prev slide

### Examples

#### React

{% embed url="https://stackblitz.com/edit/atomico-keen-slider-react?file=src/App.tsx" %}

****
