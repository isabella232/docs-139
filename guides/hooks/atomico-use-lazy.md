---
description: >-
  It facilitates the execution of asynchronous processes, for example request or
  dinamic import
---

# atomico/use-lazy

### useLazy

```jsx
let Component = useLazy(asyncCallback,args);
```

Where:

* `asyncCallback` : Asynchronous callback, useLazy will show the state of the process depending on the load, which may be these loading, success or error.
* `args` :  Array of arguments to compare between renders by useLazy for hook regeneration, an effect similar to useEffect.
* `Component`: Component that represents the state of the process.

#### Example

{% embed url="https://codepen.io/uppercod/pen/BaaMORB?editors=1010" caption="" %}

The request in the example will only be regenerated if the id variable changes, useLazy will always remain with the return of the last callback regneration ignoring pending tasks

### useLazyNode

```javascript
let Component = useLazyNod(()=>import("./pages/any-page/any-page.js"))

return <host>
    <Component loading="...loading" error="...error"/>
</host>
```

It allows to apply dynamic import only if the node is represented in the DOM, where:

* `loading`: Any, allows you to show this property while waiting for the import.
* `error` : Any, allows you to show this property if an error is generated.

