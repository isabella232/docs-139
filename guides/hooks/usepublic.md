---
description: >-
  Allows access to a variable or function of the render scope as property of the
  web-component.
---

# usePublic

### Syntax

```javascript
function toggle(){
    setState((state)=>!state)
}

usePublic("toggle",toggle);
```

{% hint style="warning" %}
para una ejecución segura fuera de la caja de Atomico debera esperar la microtask render usando la promesa, ej: `await nodeWebComponent.rendered`
{% endhint %}

