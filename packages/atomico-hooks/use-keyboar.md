---
description: capture key combinations easily
---

# use-keyboar

### Module

```
import { useKeyboard } from "@atomico/hooks/use-keyboard";
```

### Syntax

```
useKeyboard(
    ref: Ref<Element>,
    keysCode: string[],
    callback: (event: KeyboardEvent)=>void
);
```

where:

1. ref, the reference to associate the event keydown and keyup.
2. keysCode:  key combination to capture
3. callback: receives the last event of the key combination

### Example

{% embed url="https://webcomponents.dev/edit/2XCkGDqFKrJwpBpqNCNi" %}

