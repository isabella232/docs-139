---
description: >-
  A micro library inspired by React Hooks, designed and optimized for the
  creation of webcomponents.
---

# 👋 Atomico

```jsx
import { c } from "atomico"; // 2.5kB

function component({ name }) {
  return <host shadowDom>Hello, {name}</host>;
}

component.props = {
  name: String,
};

customElements.define("my-component", c(component));
```

Atomico simplifies learning, workflow and maintenance when creating webcomponents and achieves it with:

1. Functional behavior: Forget the use of classes, setter/getter property declarations, and complicated lifecycle methods. Atomico achieves everything you need from a simple function.
2. Hook-based logic: Atomico implement React's hooks API, thus achieving an efficient and highly reusable functional composition.
3. VirtualDOM designed for webcomponents.

### Api

{% page-ref page="api/props.md" %}

{% page-ref page="api/virtualdom.md" %}

{% page-ref page="api/hooks/" %}

{% page-ref page="api/testing/" %}

