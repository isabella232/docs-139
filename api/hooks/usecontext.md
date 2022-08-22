---
description: >-
  Since version Atomico@1.62.0  has introduced a context api as part of the
  core.
---

# useContext

With the new contexts API you will be able to easily communicate components without the need to handle events, by default the communication is top down, but through it you can share anything as long as it is defined as an object.

Atomico's api is similar to React's Context api, let's explore the behavior of Atomico's context api:

### createContext

create a custom Element as a context, this will serve to synchronize all the components nested within it, you must always remember to declare the tagname of this customElement, example

```tsx
import { createContext } from "atomico";

export const Theme = createContext({
    color: "white",
    background: "black"
});

customElements.define( "my-theme", Theme  );
```

### useContext

It allows to consume the return of createContext, let's go back to the previous example and suppose that we want to consume the customElement Theme created by createContext, the code for this would be the following:

```tsx
import { useContext } from "atomico";
import { Theme } from "./my-theme";

function card(){
    const {color, background} = useContext(Theme);
    return <host>
        color: { color }
        background: { background }
    </host>
}
```

In this way useContext captures the value of the parent component or reuses the value given by default to createContext.

### When to use the Context API?

It is ideal to always prioritize a conversation between parent and child through events or props api, but sometimes the depth of the DOM makes this process difficult, for this the context api has been introduced. To remove DOM depth limitations and ensure synchronization based on a unique identifier, some ideal cases to solve with the context api are:

1. Synchronize states or private methods between components.
2. Share a value or states inherited from the parent regardless of DOM depth.



