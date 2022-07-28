---
description: Responsive generic modal component.
---

# @atomico/modal

**Webcomponent** built with [Atomico JS](https://atomicojs.dev/), Simple to use and customize modal. Includes additional support for React and Preact.

{% embed url="https://codepen.io/uppercod/pen/poLdyBZ" %}

{% embed url="https://github.com/atomicojs/components/tree/master/src/components/modal" %}

### Modules

{% tabs %}
{% tab title="Default" %}
```javascript
import {
  Modal // HTMLElement
} from "@atomico/modal";
```
{% endtab %}

{% tab title="React" %}
```jsx
import {
  Modal
} from "@atomico/modal/react";
```
{% endtab %}

{% tab title="Preact" %}
```javascript
import {
  Modal
} from "@atomico/modal/preact";
```
{% endtab %}

{% tab title="Html CDN" %}
```html
<script 
    type="module" 
    src="http://esm.sh/@atomico/modal"></script>
```
{% endtab %}
{% endtabs %}

### Properties

**showAfterMs / show-after-ms**: `String`, defines the milliseconds to wait for the activation of the modal.

**show**: `Boolean`, defines whether or not to show the modal.

**padding:** `String responsivo`, define a padding for the content of the modal, example:

1. `padding="1rem"`
2. `padding="1rem, 2rem 720px, 3rem 1080px"`

**position**: `String responsivo`, defines the position of the content within the modal, example:

1. `position="center"`
2. `position="center top"`
3. `position="center bottom"`
4. `position="left center"`
5. `position="right center"`
6. `position="center, right bottom 1080px"`

**fullSize / full-size**: `Boolean`, It enables the use of background in the modal, this is complemented by the background slot to attach personalized content in the background.

**fullSizeClosed / full-size-closed**: `Boolean`, defines whether clicking on the background hides the modal.



### Examples

**React**

{% embed url="https://stackblitz.com/edit/atomico-modal-react?file=src/App.tsx" %}
