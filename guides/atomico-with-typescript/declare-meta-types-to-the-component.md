# Event declaration

Meta-types allow you to define properties not covered by Atomico's Automatic support, such as:

1. Event declaration
2. Method declaration
3. Type declaration

## Event declaration

Atomico supports through the use of the Host type, the declaration of **events** and **methods**, this is useful for associating meta-types to the customElement instance when using JSX or TSX.

### Host to declare events

Host will be useful for you to declare your event using JSX or TSX regardless of its origin, example:

```tsx
import { Host, c, useEvent } from "atomico";

function myComponent(): Host<{
  onMyCustomEvent: Event
}> {
  const dispatch = useEvent("MyCustomEvent");
  return <host>
      <button onclick={dispatch}>click</button>
  </host>;
}

export const MyComponent = c(myComponent);
```

The use of Host allows that when using JSX or TSX your event is validated through Typescript, this also applies when using @atomico/react, example:&#x20;

```tsx
import { MyComponent } from "my-componnet";

<MyComponent
  onMyCustomEvent={(event) => {
    event.currentTarget; //  < MyComponent
  }}
></MyComponent>;
```

> Note event.currentTarget accesses the CustomElement, example properties and more.

That has another benefit, capturing the event as a type to be used in an external handler, example:

```typescript
function handlerMyCustomEvent(
  event: DOMEvent<"MyCustomEvent", typeof MyComponent>
) {
  event.currentTarget; //  < MyComponent
}
```



Very powerful!
