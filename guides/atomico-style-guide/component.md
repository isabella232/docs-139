# Component

### &#x20;Component name as function.

```jsx
function myButton() {
  return <host />;
}

const MyButton = c(myButton);
```

you prefer to use camelCase(`myButton`) to declare your function as webcomponent and the resulting customElements from function c in PascalCase (Button).

**why?** `MyButton` is the only one that can be instantiated as a constructor of the web component, example:

```js
// Vanilla JS
const node = new MyButton();

//JSX
<MyButton />;
```

### Prefers the use of static style

```jsx
function component() {
  return <host shadowDom />;
}

component.styles = css`
  :host {
    display: block;
  }
`;
```

This does not rule out the use within the style tag, since it is sometimes the solution to the definition of conditional styles or variables to the logic and outside the scope of the custom properties.
