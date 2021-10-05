---
description: >-
  The usePromise hook consumes an asynchronous function is ideal for using fetch
  or other asynchronous tasks.
---

# use-promise

### Module

```javascript
import { usePromise } from "@atomico/hooks/use-promise";
```

### Syntax

```jsx
const [result, status] = usePromise(
  asyncFunction,
  runFunction,
  optionalArguments
);
```

Where :

* `result`: Retorno de la promesa
* `status`: Estado de la promesa:
  * `""`: Without executing.
  * `"pending"`: In action.
  * `"fulfilled"`: Successfully executed.
  * `"rejected"`: Executed with error.
* `asyncFunction`: asynchronous function.
* `runFunction`: `Booleano`, if `true` it will execute the promise and define the status.
* `optionalArguments`: Optional `any[]`, allows to regenerate the promise through arguments.

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/PWFshi0MYl0CTbwlXIN6/src/index.jsx" %}



