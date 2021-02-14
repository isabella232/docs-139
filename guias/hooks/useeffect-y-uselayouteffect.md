---
description: Ejecute efectos secundarios después del render sincrona o asincronamente.
---

# useEffect y useLayoutEffect

### Sintaxis

```typescript
useEffect(effectCallback, optionalArgumentList);
```

Donde :

1. `effectCallback` : Función que se ejecuta una o mas veces según `optionalArgumentList`, `effectCallback`  puede retornar una función que será ejecutada solo si ```effectCallback`` \` es nuevamente ejecutado o el wecomponents es desmontado.
2. `optionalArgumentList`: Array de argumentos a observar por `useEffect`, si uno de estos argumentos cambia entre renderizaciones `effectCallback` será ejecutado nuevamente. Si `optionalArgumentList` se define como una array vacío\(`[]`\),  useEffect solo ejecutara `effectCallback`  al crear el webcomponent .

### Ejemplo

```javascript
const listenerClickWindow = () => {
  const handlerClick = () => {
    console.log("Click window!");
  };

  window.addEventListener("click", handlerClick);

  const unlistenerClickWindow = () =>
    window.removeEventListener("click", handlerClick);

  return unlistenerClickWindow;
};

useEffect(listenerClickWindow, []);
```

### useLayoutEffect

Comportamiento idéntico a useEffect, pero con ejecución síncrona a la finalización del render.

