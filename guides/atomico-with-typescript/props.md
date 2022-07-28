# Props

The Props type allows you to infer the types of props already declared in the props object, example:

```typescript
import { Props } from "atomico";

function myComponent(props: Props<typeof myComponent>) { // {checked: boolean}
    return <host>Hello {props.checked?"Yes":"No"}</host>
}

myComponent.props = {
    checked: Boolean,
}
```

The main difference with the Component type is that Props does not generate stricture rules for the component, it only infers the props object to be used as an argument.

At the Typescript Props level, it does evaluate the structure of the component, in order to correctly infer the props, so if the component has a writing error, a warning about this type will be displayed.\
