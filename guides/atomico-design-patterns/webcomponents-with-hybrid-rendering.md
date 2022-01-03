---
description: >-
  Improve the interaction of your inputs with forms using hybrid rendering
  (LightDOM and ShadowDOM)
---

# ♻ Webcomponents with hybrid rendering

Normally we create webcomponents that only work with lightDOM or shadowDOM, example:

```jsx
function componentWithLightDom() {
  return (
    <host>
      <h1>I am in the lightDOM</h1>
    </host>
  );
}

function componentWithShadowDom() {
  return (
    <host shadowDom>
      <h1>I am inside the shadowDOM</h1>
    </host>
  );
}
```

With atomico you can go further thanks to the hook [`@atomico/hooks/use-render`](../../atomico/atomico-hooks/use-render.md) which allows you to execute renders independent of the main one, example:

```jsx
import { useRender } from "@atomico/hooks/use-render";

function componentWithLightDomAndShadowDom() {
  useRender(() => <h1>I am in the lightDOM</h1>);
  return (
    <host shadowDom>
      <h1>I am inside the shadowDOM</h1>
    </host>
  );
}
```

### What benefit does useRender have?

1. Encapsulate DOM fragments within custom Hooks and then render to any webcomponent.
2. Patch webcomponents limitations with shadowDOM when working with forms

### Patch webcomponents limitations with shadowDOM when working with forms

```jsx
import { css, useProp } from "atomico";
import { useRender } from "@atomico/hooks/use-render";

function componentWithLightDomAndShadowDom(props) {
  const [value, setValue] = useProp("value");

  useRender(() => (
    <input {...props} oninput={({ target }) => setValue(target.value)} />
  ));

  return (
    <host shadowDom>
      <slot />
    </host>
  );
}

componentWithLightDomAndShadowDom.props = {
  type: {
    type: String,
    reflect: true,
    value: "text",
  },
  value: String,
};

componentWithLightDomAndShadowDom.styles = css`
  ::slotted([type="text"]) {
    border: 1px solid black;
  }
  ::slotted([type="checked"]) {
    width: 30px;
    height: 30px;
    border: 1px solid black;
  }
`;
```

With the `useRender(...)` fragment we are managing to render an input in the lightDOM, thanks to this we will be able to control said input from inside the webcomponent.

### Conclucion

Thanks to useRender you will be able to work together with LightDOM and shadowDOM from the scope of the webcomponent created with Atomico.

