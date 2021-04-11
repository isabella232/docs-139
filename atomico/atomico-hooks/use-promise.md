---
description: Consumes a promise reflecting the return and status of this.
---

# use-promise

### Modulo

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

- `result`: Retorno de la promesa
- `status`: Estado de la promesa:
  - `""`: Without executing.
  - `"pending"`: In action.
  - `"fulfilled"`: Successfully executed.
  - `"rejected"`: Executed with error.
- `asyncFunction`: asynchronous function.
- `runFunction`: `Booleano`, if `true` it will execute the promise and define the status.
- `optionalArguments`: Optional `any[]`, allows to regenerate the promise through arguments.
