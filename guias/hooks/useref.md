---
description: permite crear una referencia que se mantiene mutable entre renders.
---

# useRef

### Sintaxis

```javascript
let ref = useRef(optionalCurrent);
```

Donde:

* `ref` es un objeto que no muta entre renders
* `opcionalCurrent` es el estado inicial de la propiedad `ref.current`

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

