---
description: Allows to run side effects after rendering
---

# useEffect and useLayoutEffect

## Syntax

```javascript
useEffect(effectCallback, optionalArgumentList);
```

Where :

1. `effectCallback` : Function that is executed one or more times according to `optionalArgumentList`,`effectCallback` can return a function that will be executed only if `effectCallback` is executed again or the webcomponent is unmounted.
2. `optionalArgumentList`: Array of arguments that controls the execution of `effectCallback`, if an argument of`optionalArgumentList` changes it will trigger that `effectCallback` is executed again without first cleaning the effects subscribed by the previous execution.

## Example

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

## useLayoutEffect

useLayoutEffect replicates the logic of useEffect but with synchronous execution to the render.

