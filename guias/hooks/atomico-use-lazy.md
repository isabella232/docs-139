---
description: >-
  Permite facilitar la ejecución de procesos asincronos, sea para request o
  dinamic import
---

# atomico/use-lazy

## useLazy

```jsx
let Component = useLazy(asyncCallback,args);
```

Donde : 

* `asyncCallback` : Callback asincrono, useLazy mostrara el estado del proceso en función de la carga, pudiendo ser estos loading, success o error.
* `args` : lista de argumentos a comparar entre renders por useLazy para la regeneración del hook, efecto similar a useEffect.
* `Component`: Componente que representa el estado del proceso.

### Ejemplo

{% embed url="https://codepen.io/uppercod/pen/BaaMORB?editors=1010" %}

## useLazyNode

```javascript
let Component = useLazyNod(()=>import("./pages/any-page/any-page.js"))

return <host>
    <Component loading="...loading" error="...error"/>
</host>
```

Permite aplicar dinamic import solo si el nodo es representado en el DOM.



