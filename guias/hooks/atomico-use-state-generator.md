---
description: >-
  use generadores recursivos y asíncronos para componer logica de stream, en
  resumen una monada.
---

# atomico/use-state-generator

## useStateGenerator

### Sintaxis

```javascript
let [state, promise] = useStateGenerator(callbackGenerator, initialState, vars);
```

Donde :

* `state` es el estado actual del hook.
* `promise` es una promesa que define si el proceso asíncrono de `useStateGenerator` ha finalizado.
* `callbackGenerator` : Funcion,  generador o generador asíncrono a consumir por `useStateGenerator`.
* `initialState`, estado inicial del hook.
* `vars` es un array de variables a observar entre renders, de ser distinto uno de estos elementos regenera el hook ejecutando nuevamente `callbackGenerator`.

### Ejemplo

```javascript
import { useStateGenerator, delay} from "atomico/use-state-generator";
/** inside web-component */
let length = 10;
let [state] = useStateGenerator(function *(state){
	while(--state){
        yield delay(1000);
        yield state;
    }
    return state;
},0, [length])
```

El ejemplo anterior genera una cuenta regresiva de 10..1, cada paso es de 1000ms.

### Avanzado

 **recursión**, ud puede conocer el estado asociado al generador retornando una función, esta sera analizada para componer un nuevo estado.





