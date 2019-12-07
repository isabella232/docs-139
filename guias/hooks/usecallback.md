---
description: >-
  Permite memorizar el callback a base del segundo parametro, posee un efecto
  similar a useMemo
---

# useCallback

### Sintaxis

```javascript
let callback = useCallback(callback,args);
```

Donde:

* `callback`:  Funcion a memorizar cada vez que uno de los elementos de la lista de argumentos cambie en función de su largo o indice
* `args`: lista de argumentos a comparar entre renders por useCallback.
* `memo`: retorno de la ejecución de callback.

