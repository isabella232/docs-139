---
description: >-
  Memorize the return of a callback by limiting its execution through an array
  of arguments, the callback is executed at the time of rendering only if the
  arguments change
---

# useMemo

### Sintaxis

```javascript
let memo = useMemo(callback, args);
```

Donde:

* `callback`:  Funcion que sera llamada al inicializar o cada vez que uno de los elementos de la lista de argumentos cambie en función de su largo o indice 
* `args`: lista de argumentos a comparar entre renders por useMemo
* `memo`: retorno de la ejecución de callback.

### Ejemplo

```javascript
let data = useMemo({
    let data = [];
    for(let i = 0;i<length;i++){
        data.push({...randomUser()})
    }
    return data;
},[length]);
```

callbackHighCostProcess, puede ser una iteración de alto costo en rendimiento que dependa del scope del render, esto permite evitar segundas ejecuciones condicionadas por los argumentos del segundo parámetro de useMemo

