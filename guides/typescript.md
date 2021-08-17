---
description: Types for functional webcomponents created with Atomico + Typescript.
---

# 📜 Typescript

## Tsx or Ts?

Typescript supports React with a type system for JSX leveraged to TS, Atomico inherits those benefits when using JSX allowing to win jsx-runtime, autocompletion of properties, attributes and events when building its code using TSX. This does not invalidate the use of TS when creating webcomponents with Atomico, the selection will depend directly on the developer.

### Configuration example

```javascript
{
  "compilerOptions": {
    "checkJs": true,
    "allowJs": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictPropertyInitialization": true,
    "noImplicitReturns": true,
    "alwaysStrict": true,
    "esModuleInterop": true,
    "declaration": true,
    "target": "ES2017",
    "jsx": "react-jsx",
    "jsxImportSource": "atomico",
    "module": "ESNext",
    "moduleResolution": "Node"
  }
}
```

Where:

1. `jsx` and `jsxImportSource` enables the use of jsx-runtime with Atomico in Typescript, eliminated the need to use jsxFactory when using JSX.
2. `noImplicitAny`, to complete the return of the props use the type `Props`. It is valid to eliminate the use of `noImplicityAny`, since sometimes it can be very strict in situations of various types, we must remember that JS by nature is dynamic.

{% hint style="info" %}
If you've used the Atomico CLI `npm init @atomico`, it already has Typescript support thanks to Vite.
{% endhint %}

## Component

### `Props<typeof component.props>`

Allows you to retrieve the types of the `props` object associated with the function.

```jsx
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

