# Declare meta-types to the component

Meta-types allow you to define properties not covered by Atomico's Automatic support, such as:

* [x] Event definition.
* [ ] Definition of custom-properties.

## Event definition

By using JSX you benefit from the instance of your webcomponent without the use of the Tagname, this is really amazing as it allows:

1. Know the origin of the import of your webcomponent.
2. Know types when using properties and **Events**, If events!t.

## Meta type and DOMEvent.

The Meta type allows you to define meta properties of your WebComponent when instantiated in JSX, for example Events:

```tsx
import { Meta, DOMEvent, c } from "atomico";

function myComponent(): Meta<DOMEvent<"MyCustomEvent">> {
  return <host />;
}

export const MyComponent = c(myComponent);
```

In this case, the Meta type defines that the internal context of the component has an event named `MyCustomEvent`, which can be listened to, example:

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

```ts
function handlerMyCustomEvent(
  event: DOMEvent<"MyCustomEvent", typeof MyComponent>
) {
  event.currentTarget; //  < MyComponent
}
```

DOMEvent is really versatile since it has 3 uses:

1. Define an event as a parameter. example: `DOMEvent<HTMLElement, CustomEvent<{id:string}>>`.
2. Retrieve an event from a customElement, example: `DOMEvent<"MyCustomEvent", typeof MyComponent>`.
3. Create an event for a customElement, example `DOMEvent<"MyCustomEvent", CustomEvent<{id:string}>>`.

Very powerful!
