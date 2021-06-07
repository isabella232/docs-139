---
description: >-
  Build test to custom hooks created with Atomico with an isolated instance and
  predictable
---

# atomico/test-hooks

The "atomico/test-hooks" submodule is a direct part of Atomico's core and will allow you to run the customHook in a controlled way without the need for webcomponents.

```javascript
import { createHooks } from "atomico/test-hooks";
```

## createHooks

function that creates an isolated context that is shared globally with Atomico hooks when executing the load method

### Instance

```javascript
const hooks = createHooks(opcionalRender, opcionalHost);
```

Where:

* **optionalRender**: Callback that allows restarting the hook's life cycle, this callback will be executed every time a hook like [useState](../hooks/usestate.md) or [useReducer](../hooks/usereducer.md) requests the scope update, Atomico uses it to render the webcomponent again.
* **opcionalHost**: allows to share an object for the hook [useHost](../hooks/usehost.md), Atomico uses it to share the instance of the webcomponent.

### Return of the instance

```typescript
interface Hooks {
  load<T>(callback: () => T): T;
  clearEffect(unmounted?: boolean): () => void;
}
```

Where:

* **load**: Function that allows to load the hooks to the temporary global context of Atomico.
* **clearEffect:** Function that activates the collector of useLayoutEffect, when executing clear Effect a callback will be returned that allows ending the collector for useEffect, closing the cycle of secondary effects.

  If clear Effect receives true as parameter, it communicates the unmounted.

## Example:

**./use-counter.js:** customHook to test.

```typescript
import { useState } from "atomico";

export function useCounter(initialValue) {
  const [value, setValue] = useState<number>(initialValue);
  return {
    value,
    increment: () => setValue((value) => value + 1),
    decrement: () => setValue((value) => value - 1),
  };
}
```

**./use-counter.test.js:** The example is based on the test environment from [@web/test-runner](https://modern-web.dev/docs/test-runner/overview/).

```javascript
import { expect } from "@esm-bundle/chai";
import { createHooks } from "atomico/test-hooks";
import { useCounter } from "./use-counter.js";

it("Check return", () => {
  const hooks = createHooks();

  const counter = hooks.load(() => useCounter(10));

  expect(counter.value).to.equal(10);
  expect(counter.increment).to.be.an.instanceOf(Function);
  expect(counter.decrement).to.be.an.instanceOf(Function);
});
```

