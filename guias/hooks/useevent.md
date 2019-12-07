---
description: Permite crear un callback que despacha un evento desde el web-component
---

# useEvent

### Sintaxis

```jsx
let eventInit = {
    bubbles : true, 
    composed : true,
};

let dispatchMyEvent = useEvent("myEvent",eventInit)
```

Donde :

* `"myEvent"`: String requerido, nombre del evento a despachar por el callback
* `eventInit`: Objeto opcional, permite definir el comportamiento del evento mediante el [api nativa de eventInit](https://developer.mozilla.org/es/docs/Web/API/Event/Event).
* `dispatchMyEvent`: Callback, ejecuta el evento creado por useEvent, este recibe un parámetro opcional que define la propiedad **detail** del evento.

El callback generado por useEvent es inmutable, por lo que puede ser usado como argumento para otros hooks, ej:

```javascript
let dispatchMounted = useEvent("mounted",{bubbles:true,composed:true});

useEffect(dispatchMounted, []);
```

El ejemplo anterior permitiría una escucha global como esta:

```javascript
window.addEventListener("mounted",({target})=>{
    console.log("web-component mounted",target)
})
```

A diferencia del evento despachado por las props, este no se sincroniza con el ciclo de rendered, por lo que deberá usar useEffect si busca la lectura del dom asociado al cambio.

