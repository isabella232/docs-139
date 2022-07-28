---
description: Types for functional webcomponents created with Atomico + Typescript.
---

# Typescript & JSDOC

## Component

### `Props<typeof component.props>`

Allows you to retrieve the types of the `props` object associated with the function.

{% tabs %}
{% tab title="Typescript" %}
```typescript
import { Props, c } from "atomico";

function component(props: Props<typeof component.props>) {
  return <host shadowDom>
    Atomico + Typescript
  </host>
}

component.props = {
    propString: String,
    propObject: {
        type: Object,
        value: (): { prop?: number } => ({}),
    },
};

customElements.define("my-component", c(component));
```
{% endtab %}

{% tab title="JSDOC" %}
```jsx
import { c } from "atomico";
/**
 * @param {import("atomico").Props<component.props>} props
 */
function component(props) {
  return <host shadowDom>
    Atomico + Typescript
  </host>
}

component.props = {
    propString: String,
    propObject: {
        type: Object,
        value: (): { prop?: number } => ({}),
    },
};

customElements.define("my-component", c(component));
```
{% endtab %}
{% endtabs %}

### Component\<props>

Create a strict contract that facilitates and checks the correct construction of props

{% tabs %}
{% tab title="Typescript" %}
```typescript
import { c, Component } from "atomico";

const component: Component<{ value: string }> = (props) => {
  return <host shadowDom></host>;
};

component.props = {
  value: String,
}
```
{% endtab %}

{% tab title="JSDOC" %}
```jsx
import { c } from "atomico";
/**
 * @type {import("atomico").Component<{ value: string }>}
 */
const component = (props) => {
  return <host shadowDom></host>;
};

component.props = {
  value: String,
};
```
{% endtab %}
{% endtabs %}

## Hooks

Most hooks infer the types, but others require a declaration to improve the typing experience, example:

### useProp

```typescript
const [value, setValue] = useProp<number>("value");
```

Forces the type `number` for `value` and `setValue`, according to the example `value` can only be of type `number`.

### useState

**useState infers the type in most cases,** but not using an initial state prevents strict typing, I was able to correct this as follows:

```typescript
const [value, setValue] = useState<number>();
```

Forces the type `number` for `value` and `setValue`, according to the example `value` can only be of type `number`.

### useRef

```typescript
const ref = useRef < HTMLInputElement > useRef();
```

Forces **ref.current** to be `HTMLInputElement`.
