---
description: Create reactive templates that interact with the state of your webcomponent
---

# use-dollars

The purpose of this hook is to allow communication between the webcomponent and the lightDOM without knowing the DOM, achieving with this hook:

1. expose the webcomponent's api to the lightDOM and react to it.
2. data binding between the state of the webcomponent and the lightDOM.

### module

```
import { useDollars } from "@atomico/hooks/use-dollars";
```

### Syntax

```
useDollars(ref: Ref<HTMLSlotElement>);
```

### Example

{% embed url="https://webcomponents.dev/edit/CAIDkPAI9Stp5APyS87n/src/index.jsx" %}
