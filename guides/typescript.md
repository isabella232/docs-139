---
description: Type to structure a component from its creation
---

# Component

```typescript
import { Component } from "atomico";

// 📌 Parameters for the function and set 
//    the structure rules for myComponent.props
interface Props{
    checked: boolean;
    value: string
}

// 📌 Optional, improves the typing experience 
//    in JSX (Atomico, Preact and React)
interface MetaProps {
    myMethod:(value: number)=>void;
    onMyEvent: Event;
}

const myComponent: Component<Props, MetaProps> = (props) => {
    const myMethod = (value: number)=>{};
    return <host myMethod={myMethod }></host>
}

myComponent.props = {
    checked: Boolean,
    value: { type: String, event: {type: "MyEvent"} },
}
```

The declaration `const myComponent: Component<Props, MetaProps>` defines at the Typescript level the types of props and other options with which the component should be structured.&#x20;

This process is strict but makes autocompletion and error detection easier in the component declaration.

Some warnings that this type can create are:

1. The declaration of the prop in myComponents.props does not match the type declared in Props.
2. A props declaration is missing.
3. Props has invalid metadata, example reflect has been defined for a Promise type.
