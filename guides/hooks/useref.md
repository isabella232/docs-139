---
description: >-
  allows you to create an object that can contain persistent references between
  renders
---

# useRef

### Syntax

```javascript
let ref = useRef(optionalCurrent);
```

Where:

* `ref` : Object, this may contain persistent references between renders.
* `opcionalCurrent` : Any optional, is the initial state of the ref.current property.

### Example

```jsx
let ref = useRef();

useEffect(
  () => {
    ref.current.addEventListener("click", ({ target }) => {
      console.log({ target });
    });
  },
  [ref]
);

<host>
  <button ref={ref}> click </button>
</host>;
```

In the example the variable ref is delivered to the virtual-dom, this will define at the time of rendering the node as ref.current, allowing access to it after the render.

