---
description: The Keen-slider api but with WebComponents
---

# keen-slider

This webcomponent reflects part of the [**keen-slider**](https://keen-slider.io/) library API using Atomico

## Modulo

{% tabs %}
{% tab title="Default" %}
```javascript
import { KeenSlider } from "@atomico/components/keen-slider";
```
{% endtab %}

{% tab title="React" %}
```javascript
import { KeenSlider } from "@atomico/components/keen-slider/react";
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
