---
description: Wrapper to use web components in React
---

# @atomico/react

This module provides 2 ways to create a wrapper for react, the generated wrapper fixes the following react problems when using webcomponents

1. fixes the association of events, any property that starts with the prefix `in` and its value is of the function type will be associated as an event of the component.
2. Children are always transmitted as nodes of the component.
3. references are always transmitted to the webcomponent



### Example wrapper

Manual wrapping this requires knowing the tagName, Element and options

```jsx
import { wrapper } from "@atomico/react";
import { HTMLMyComponent } from "./my-component.js";

const tagName = "my-component";

customElements.define(tagName, HTMLMyComponent);

export const MyComponent = wrapper(tagName, HTMLMyComponent);
```

The second parameter for `wrapper` is optional, but will allow react to infer Atomico types, improving the Autocomplete and Typescript experience.

### Example auto

Auto captures the parameters associated with the use of customElements.define to retrieve the tagName or generate an id as tagName, to instantiate the webcomponent.

```jsx
import { auto } from "@atomico/react/auto";
import { Component as ElementComponent } from "./my-component";

export const Component = auto(ElementComponent);
```

{% embed url="https://codesandbox.io/s/atomico-react-example-cizcy" %}
