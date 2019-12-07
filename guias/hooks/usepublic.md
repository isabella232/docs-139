---
description: >-
  Permite dar acceso como propiedad a una variable o funcion del scope de
  render.
---

# usePublic

### Sintaxis

```javascript
function toggle(){
    setState((state)=>!state)
}

usePublic("toggle",toggle);
```

{% hint style="warning" %}
para una ejecución segura fuera de la caja de Atomico debera esperar la microtask render usando la promesa, ej: `await nodeWebComponent.rendered`
{% endhint %}



