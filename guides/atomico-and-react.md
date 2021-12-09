# 🤝 Atomico and React

### React and webcomponents

[React has begun to support the use of webcomponents in an experimental way](https://github.com/facebook/react/issues/11347#issuecomment-988970952), this will allow to use custom tag with association of events and more, example:

```jsx
import React from "react";
import "@formilk/components";

export default function App() {
  return (
    <fm-button>Click!<fm-button>
  );
}
```

**Advantages**: The react team will take care of the coverage of this characteristic.

**Disadvantages**: (Optional) The maintainer of the component must declare the types of the custom tag.

Although the use of the custom tag is a way of instantiating the component, many times it does not define the import path at the time of its use, complicating the resolution of the component's origin, **to avoid this we recommend the use of the Atomico wrapper for React**.

### Atomico wrapper for React

Atomico the package [@atomic/react](../atomico/atomico-react.md) allows:

1. Create a Wrapper component for the custom Element
2. Avoid react conflicts with webcomponents, such as association of events, attributes, properties and children.
3. Reflect the types declared in Atomic to React, valid for JSX or TSX

Coverage is automatic if you decide to share your package using [@atomico/exports](../atomico/atomico-exports.md) under the following [export conditions.](../atomico/atomico-exports/wrapper-for-react.md)

### Atomico inside Next.js

All webcomponents work in Next if it escapes from SSR

#### Example of custom tag usage

```jsx
import  "@formilk/components/button";

export default function Home() {
  return (
    <div>
      <fm-button name="Matias">
        <h1>Hello Next.js</h1>
      </fm-button>
    </div>
  );
}
```

#### Example of use of the wrapper.

{% tabs %}
{% tab title="Next.js" %}
```jsx
import dynamic from "next/dynamic";

const Button = dynamic(() => import("./wrapper-button.js"), {
  ssr: false,
});

export default function Home() {
  return (
    <div>
      <Button  name="Matias">
        <h1>Hello Next.js</h1>
      </Button>
    </div>
  );
}
```
{% endtab %}

{% tab title="wrapper-button.js" %}
```javascript

import { auto } from "@atomico/react/auto";
import { Button } from "@formilk/components/button";

export default auto(Button);
```
{% endtab %}
{% endtabs %}

Remember if you use the `auto` module, it should always be imported first than the customElement to use, otherwise `auto` will generate an id as a custom tag to instantiate the component within react
