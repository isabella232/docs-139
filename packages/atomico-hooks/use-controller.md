---
description: Use a ReactiveController.
---

# use-controller

### Modulo

```javascript
import { useController } from "@atomico/hooks/use-controller";
```

### Syntax

```jsx
class AController {/*...*/}

const useA = x => useController(host => new AController(host, x));
const { a } = useA('a');
```

Where:

* `AController`: `ReactiveController`, A [ReactiveController](https://lit.dev/docs/composition/controllers/) with property `a`.

