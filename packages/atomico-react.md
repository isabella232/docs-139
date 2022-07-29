---
description: Wrapper to use web components in React
---

# @atomico/react

{% embed url="https://github.com/atomicojs/react" %}

This module provides 2 ways to create a wrapper for react, the generated wrapper fixes the following react problems when using webcomponents

1. fixes the association of events, any property that starts with the prefix `in` and its value is of the function type will be associated as an event of the component.
2. Children are always transmitted as nodes of the component.
3. references are always transmitted to the webcomponent

### Example wrapper

Manual wrapping this requires knowing the tagName, Element and options

```jsx
import "@atomico/react/proxy";
import { wrapper } from "@atomico/react";
import { HTMLMyComponent } from "./my-component.js";

export const MyComponent = wrapper("my-element", HTMLMyComponent );
```

The second parameter for `wrapper` is optional, but will allow react to infer Atomico types, improving the Autocomplete and Typescript experience.

### Example auto

Auto captures the parameters associated with the use of customElements.define to retrieve the tagName or generate an id as tagName, to instantiate the webcomponent.

```jsx
import "@atomico/react/proxy";
import { auto } from "@atomico/react";
import { HTMLMyComponent } from "./my-component.js";

export const MyComponent = auto( HTMLMyComponent );
```

{% embed url="https://codesandbox.io/s/atomico-react-example-cizcy" %}

### @atomico/exports

Another way to export your **webcomponents to React** is using `@atomico/exports` which will automatically detect the webcomponents and create the wrappers using `@atomico/react`.

Some benefits of @atomico/exports are:

1. export via expressions, example `./src/**.tsx`
2. create the `package.json#exports` automatically
3. create the types and associate the export paths for Typescript.
4. group the sub dependencies of the workspace
5. minimize the JS code.

We invite you to review in detail the @atomico/exports package for its use

{% content-ref url="introduction/" %}
[introduction](introduction/)
{% endcontent-ref %}
