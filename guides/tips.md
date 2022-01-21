---
description: >-
  La siguiente guía define algunos Tips a considerar al momento de crear
  webcomponents con Atomico
---

# Tips

### Component name as function

Write the functional component using the first lowercase character, since the functional declaration is not instantiable as a constructor in JSX.

```jsx
function component() {
  return <host />;
}
```

This prevents confusion when identifying the constructor of the component instance.[ ](https://atomico.gitbook.io/doc/v/espanol/api/virtualdom/avanzado#constructor-con-custom-element)[Atomico if it supports instances as Constructors, see cases.​](https://atomico.gitbook.io/doc/api/virtualdom/advanced#constructor-with-custom-element)

### useProp <a href="#useprop" id="useprop"></a>

preferably use useProp in the following cases:

* By modifying the prop from inside the component.

```jsx
function useCounter(prop) {
  const [value, setValue] = useProp(prop);
  return {
    value,
    increment() {
      setValue(value + 1);
    },
  };
}
```

* By isolating the logic of the prop in a customHook.

```jsx
function useCounter(prop) {
  const [value, setValue] = useProp(prop);
  return {
    value,
    increment() {
      setValue(value + 1);
    },
  };
}
```

&#x20;In most cases downloading the prop from the first argument of the function is simpler and more declarative, example:

```jsx
function component({ value }) {
  return <host>{value}</host>;
}

component.props = {
  value: Number,
};
```

[Atomico has type support in both JSDOC and Typescript by inferring the types of the props.​](https://atomico.gitbook.io/doc/guides/typescript#props-less-than-typeof-component.props-greater-than)

### Prefers the use of static styles

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
