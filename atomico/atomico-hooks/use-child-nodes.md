---
description: >-
  Captures all nodes not created by the webcomponent render, ideal for  apply
  slot polyfill in LightDOM.
---

# use-child-nodes

## Modulo

```javascript
import { useChildNodes } from "@atomico/hooks/use-child-nodes";
```

## Syntax

```javascript
const [childNodes, update] = useChildNodes();
```

Where :

1. `childNodes` : List of nodes that do not belong to the webcomponent render.
2. `update`: Callback that forces a new `childNodes` scan.

## Example

```jsx
function component() {
  const [childNodes] = useChildNodes();
  return (
    <host>
      {childNodes
        .filter((node) => node.localName == "h1")
        .map((Title) => (
          <Title onclick={() => console.log("click h1!")} />
        ))}
    </host>
  );
}
```

From the example we can highlight that the webcomponent will use all the children not created by the `h1` type and will associate the onclick handler with them.

