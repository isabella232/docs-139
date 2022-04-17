---
description: >-
  Atomico with Typescript will improve the scalability of your project thanks to
  a really productive type system when creating, distributing and maintaining
  webcomponents
---

# 🛡 Atomico with Typescript

With Atomico and Typescript you will be able to:

1. [Construct the props parameter of your functional component.](./#construct-the-props-parameter-of-your-functional-component.)
2. [Check the correct declaration of your component.](./#check-the-correct-declaration-of-your-component.)
3. [Check the correct use of hooks.](check-the-correct-use-of-hooks.md)
4. [Declare meta-types to the component.](declare-meta-types-to-the-component.md)

📌 **If you are a Typescript user I recommend using TSX vs the template-string, as you will benefit from:**

1. JSX runtime, Typescript will automatically import Atomico upon detecting the use of TSX.
2. Autocompletion and validation of attributes, properties and events of tags and webcomponents.
3. Validacion de instancia de webcomponents usando constructores.

## Construct the props parameter of your functional component.

Your component as a function does not infer the props, to help infer the props you should use the Props type, example:

**From an object**: Construct props directly from the declaring object.

```tsx
import { Props } from "atomico";

const props = {
  value: { type: Number, value: 0 },
};

function myComponent({ value }: Props<typeof props>) {
  return <host>{value * 10}</host>;
}

myComponent.props = props;
```

**From the component**: Build the props from the component, internally Atomico captures the property `component.props`.

```tsx
import { Props } from "atomico";

function myComponent({ value }: Props<typeof myComponent>) {
  return <host>{value * 10}</host>;
}

myComponent.props = {
  value: { type: Number, value: 0 },
};
```

**From another customElement component**: It's unusal, but when you extend another component you can infer the props from its constructor.

```tsx
import { Props, c } from "atomico";
import { MyOtherComponent } from "./my-other-component";

function myComponent({ value }: Props<typeof MyOtherComponent>) {
  return <host>{value * 10}</host>;
}

export const MyComponent = c(myComponent, MyOtherComponent);
```

## Check the correct declaration of your component.

Typescript checks the structure of your component by using the `c` function on it, thus validating which props and styles have been attached.

```tsx
import { Props, c, css } from "atomico";

function component(props: Props<typeof component>) {
  return <host>{props.value}</host>;
}

component.props = {
  value: Number,
};

component.styles = css`
  :host {
    color: tomato;
  }
`;

const MyComponent = c(component);

customElements.define("my-component", MyComponent);
```

The return of `c` is a CustomElement with the types of the associated props, example:

```typescript
const myComponent = new MyComponent();

myComponent.value = "abc";
```

It will report an error to Typescript since this component's props define that value is of type `number`, this validation also applies when instantiating your CustromElement in JSX or TSX.

```tsx
<MyComponent value="abc"></MyComponent>
```

Both TSX or JSX will help you to build better applications since it verifies the types according to the definition of its component, this verification is Free, it does not need plugins, only a `tsconfig.json` file and `Typescript` to automate the revision.
