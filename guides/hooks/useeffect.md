---
description: "allows you to create side effects, useful for controlling effects that\_\_ interactive with the DOM or asynchrony"
---

# useEffect

### Syntax

```javascript
function afterRender() {
  console.log("after render");
  return function beforeNewRender() {
    console.log("new render");
  }
}

useEffect(afterRender, optionalArgument);
```

Where:

* `afterRender` : Function, runs after the render associated with the hook.
* `beforeNewRender` : Funcion optional,   is the return of the afterRender function and this will be executed only if a new render is generated or the hook is unmounted.

### Example

```javascript
let [route, setRoute] = useState(location.pathname);

useEffect(() => {
  function handler() {
    setRoute(location.pathname);
  }
  window.addEventListener("popstate", handler);
  return () => window.removeEventListener("popstate", handler);
}, [
```

