# useMemo and useCallback

### Syntax

```javascript
const memoValue = useMemo(callback, optionalArgumentList);
```

Where :

1. `memoValue` : Return memorized by useMemo.
2. `callback`: Function that is executed one or more times according to `optionalArgumentList`.
3. `optionalArgumentList`: Array of arguments that controls the execution of `callback`, if an argument of `optionalArgumentList` changes it will trigger that `callback` is executed again.

### useCallback

Hook that allows you to memorize a callback so that it keeps its scope

```javascript
const memoCallback = useCallack(callback, optionalArgumentList);
```

Where:

1. `memoCallback` : Return memorized by useCallback.
