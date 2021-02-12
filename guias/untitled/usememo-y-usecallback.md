# useMemo y useCallback

### Sintaxis

```javascript
const memoValue = useMemo(callback, optionalArgumentList);
```

Donde :

1. `memoValue` : Retorno memorizado por useMemo 
2. `callback`:  Función que se ejecuta una o mas veces según `optionalArgumentList`.
3. `optionalArgumentList`: Array de argumentos a observar por `useEffect`, si uno de estos argumentos cambia entre renderizaciones `useEffect` ejecutara nuevamente el `callback`, memorizando un nuevo retorno.

### useCallback

Hook que permite memorizar un callback para que este conserve su scope.

```javascript
const memoCallback = useCallack(callback, optionalArgumentList);
```

Donde:

1. `memoCallback` : Retorno memorizado por useCallback.

