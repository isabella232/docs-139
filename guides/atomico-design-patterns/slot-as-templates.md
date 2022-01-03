# 🔗 Slot as templates

### Introduction

Slots are a powerful feature when working with webcomponents that use the shadowDOM and thanks to the hook `@atomico/hooks/use-slot` you will be able to observe the state of the slot and know the childNodes of this to manage the logic of the template, example:

```jsx
import { useRef } from "atomico";
import { useSlot } from "@atomico/hooks/use-slot";

function component() {
  const refSlotIcon = useRef();
  const slotIcon = useSlot(refSlotIcon);
  return (
    <host shadowDom>
      <slot
        name="icon"
        ref={refSlotIcon}
        style={slotIcon.length ? null : "display: none"}
      />
      <slot />
    </host>
  );
}
```

Thus managing to easily condition parts of our template to define the slots.

Another trick that useSlot allows us is the interaction at the DOM level, example:

```jsx
import { useRef, useEffect } from "atomico";
import { useSlot } from "@atomico/hooks/use-slot";

function component() {
  const refSlotSlides = useRef();
  const slotSlides = useSlot(refSlotSlides);

  slotSlides.forEach((slide) => {
    slide.style.width = "100%";
    slide.style.height = "300px";
  });

  return (
    <host shadowDom>
      <slot name="slides" />
    </host>
  );
}
```

We can even apply filters per instance for a better identification of the node, example:

```js
useSlot(refSlotSlides).filter(
  (childNode) => childNode instanceof HTMLDivElement
);
```

⚠️ In case of high ui computation use prefer to use slot modifiers inside a `useEffect`.

### Slot pattern as a template

Slots are not only limited to a static definition, you can use them to identify a node and use it to create new nodes according to the logic of the webcomponent, example:

```jsx
import { useRef } from "atomico";
import { useSlot } from "@atomico/hooks/use-slot";
import { usePromise } from "@atomico/hooks/use-promise";

function userFetch() {
  const refSlotTemplateUser = useRef();
  const [Template] = useSlot(refSlotTemplateUser);
  const [result, status] = usePromise(
    () =>
      fetch("https://jsonplaceholder.typicode.com/users").then((res) =>
        res.json()
      ),
    true
  );

  return (
    <host shadowDom>
      <slot name="template" ref={refSlotTemplateUser} />
      <div class="list">
        {status === "fulfilled"
          ? !!Template &&
            result.map((props) => <Template {...props} cloneNode />)
          : "Pending..."}
      </div>
    </host>
  );
}
```

Thanks to `useSlot(refSlotTemplateUser)` we get the first node of the `Template` slot to be used in the iteration of the results obtained by fetch, with this we have eliminated the leverage of the webcomponent in charge of rendering the user at the level of our webcomponent `userFetch`

### `Example`&#x20;

{% embed url="https://webcomponents.dev/edit/w2hdZpjAG1V3K8TxdBw0/src/component-user-fetch.jsx" %}

⚠️ the `cloneNode` property is available from version `atomico@1.37.0`
