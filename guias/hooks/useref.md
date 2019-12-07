---
description: >-
  Permite crear un objeto que puede contener referencias persistentes entre
  renders
---

# useRef

### Sintaxis

```javascript
let ref = useRef(optionalCurrent);
```

Donde:

* `ref`  : Object, que puede contener referencias persistentes entre renders
* `opcionalCurrent` : Any, es el estado inicial de la propiedad `ref.current`

### Ejemplo

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

 El en ejemplo la variable `ref` se entrega al virtual-dom, este definirá en el momento de la renderización el nodo como `ref.current`, permitiendo acceder a este después del render.

