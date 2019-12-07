---
description: >-
  crea un efecto secundario asociado, útil para controlar efectos que
  interactivo con el DOM o asincronía
---

# useEffect

### Sintaxis

```javascript
function afterRender() {
  console.log("after render");
  return function beforeNewRender() {
    console.log("new render");
  }
}

useEffect(afterRender, optionalArgument);
```

Donde:

* `afterRender` es una función que se ejecuta después del render asociado al hook
* `beforeNewRender` es el retorno de la funcion `afterRender` y esta sera ejecutada solo si se genera un nuevo render o se desmonta el hook

### Ejemplo

```javascript
let [route, setRoute] = useState(location.pathname);

useEffect(() => {
  function handler() {
    setRoute(location.pathname);
  }
  window.addEventListener("popstate", handler);
  return () => window.removeEventListener("popstate", handler);
}, []);
```

