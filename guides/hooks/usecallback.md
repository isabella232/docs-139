---
description: >-
  Allows memorizing the callback based on the second parameter, has an effect
  similar to useMemo
---

# useCallback

### Syntax

```javascript
let callback = useCallback(callback,args);
```

Where:

* `callback`:  Function, this is executed at the beginning or every time one of the elements of the argument list changes depending on its length or index
* `args`:Array, are the arguments to compare between renders by useCallback.
* `memo`: callback execution return.

