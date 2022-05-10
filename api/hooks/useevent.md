---
description: Dispatch events from the webcomponent without referencing the context(this)
---

# useEvent

## Syntax

```javascript
const dispatchEvent = useEvent(myEvent, eventInit);
```

Where:

* dispatchEvent: **callback,** dispatches the event from the webcomponent and allows defining the detail by receiving a first parameter
* myEvent: **string**, name of the event to dispatch.
* eventInit: **optional object**, event configuration.

## Examples

{% tabs %}
{% tab title="Basic" %}
```jsx
import { useEvent } from "atomico";

function component() {
  const dispatchEvent = useEvent("clickButton", {
    bubbles: true,
    composed: true,
  });
  return (
    <host>
      <button onclick={() => dispatchEvent()}>button</button>
    </host>
  );
}
```
{% endtab %}

{% tab title="Detail" %}
```javascript
import { useEvent } from "atomico";

function component() {
  const dispatchEvent = useEvent("clickButton", {
    bubbles: true,
    composed: true,
  });
  return (
    <host>
      <button onclick={() => {
        const detail = "my-component"; // 👈
        dispatchEvent(detail);         // 👈
      }}>button</button>
    </host>
  )c
```
{% endtab %}

{% tab title="Typescript + detail" %}
```typescript
import { useEvent } from "atomico";

function component() {
  //                             👇 type for detail
  const dispatchEvent = useEvent<{id:number}>("clickButton", {
    bubbles: true,
    composed: true,
  });
  return (
    <host>
      <button onclick={() => {
        //            👇 Detail
        dispatchEvent({id:100});
      }}>button</button>
    </host>
  );
}
```
{% endtab %}
{% endtabs %}

## Event customization

The second parameter of `useEvent` allows customizing the behavior of the even:

```typescript
interface EventInit {
  // Allows the event to be dispatched upstream to the node's containers.
  bubbles?: boolean;
  // Allows the event to traverse the shadowDOM event capture.
  composed?: boolean;
  // Allows the event to be canceled.
  cancelable?: boolean;
  // Allows customizing the event builder, ideal for event instance-based communication.
  base?: Event | CustomEvent;
}
```
