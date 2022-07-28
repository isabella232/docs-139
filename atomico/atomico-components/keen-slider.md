---
description: The Keen-slider api but with WebComponents
---

# keen-slider

**Webcomponent** built with [Atomico JS](https://atomicojs.dev/) to use [keen-slider](https://keen-slider.io/) as webcomponent. Includes additional support for React and Preact.

{% embed url="https://codepen.io/uppercod/pen/MWVENee" %}

## Modulo

{% tabs %}
{% tab title="Default" %}
```javascript
import { KeenSlider } from "@atomico/keen-slider";
```
{% endtab %}

{% tab title="Elements" %}
```javascript
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

## Example

{% tabs %}
{% tab title="HTML" %}
```markup
<atomico-keen-slider
    slides-per-view="1, 2 520px"
    slides-spacing="15"
>
    <div slot="slide" class="slide">
        <h1>1</h1>
    </div>
    <div slot="slide" class="slide">
        <h1>2</h1>
    </div>
    <button slot="to-left">←</button>
    <button slot="to-right">→</button>
</atomico-keen-slider>

```
{% endtab %}

{% tab title="JSX" %}
```javascript
import {
    KeenSlider,
} from "@atomico/components/keen-slider";

<KeenSlider
    slidesPerView="1, 2 520px"
    slidesSpacing="15">
    <div slot="slide" class="slide">
        <h1>1</h1>
    </div>
    <div slot="slide" class="slide">
        <h1>2</h1>
    </div>
    <button slot="to-left">←</button>
    <button slot="to-right">→</button>
</KeenSlider>

```
{% endtab %}
{% endtabs %}
