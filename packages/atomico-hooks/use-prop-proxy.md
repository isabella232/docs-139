---
description: Share values from the scope via setter and getters
---

# use-prop-proxy

allows to create a setter and getter for a property of the webcomponent, this is useful for:

1. Reflect elements internal to the scope as part of the instance, example references.
2. Observe from the scope the mutations external to Atomico.

### Example

```typescript
import { Props, useRef } from "atomico";
import { useRender } from "@atomico/hooks/use-render";
import { usePropProxy } from "@atomico/hooks/use-prop-proxy";

function component(props: Props<typeof component>) {
  const refInput = useRef();

  useRender(() => (
    <input
      slot="input"
      class="reset"
      ref={refInput}
      type={props.type}
      value={props.value}
    />
  ));

  usePropProxy("value", {
    get() {
      return refInput.current?.value;
    },
  });

  return (
    <host shadowDom>
      <slot name="input"></slot>
    </host>
  );
}

component.props = {
  type: String,
  value: String,
};

```
