---
description: >-
  Memorize the return of a callback by limiting its execution through an array
  of arguments, the callback is executed at the time of rendering only if the
  arguments change
---

# useMemo

### Syntax

```javascript
let memo = useMemo(callback, args);
```

Where :

* `callback`:  Function, this is called upon initialization or each time one of the items in the argument list changes depending on its length or index
* `args`: list of arguments to compare between renders by useMemo
* `memo`: callback execution return.

### Example

```javascript
let data = useMemo({
    let data = [];
    for(let i = 0;i<length;i++){
        data.push({...randomUser()})
    }
    return data;
},[length]);
```

It is recommended to use it in a high-cost process, as a high-cost iteration in performance that depends on the scope of the render, this allows to avoid second executions conditioned by the arguments of the second parameter of useMemo

