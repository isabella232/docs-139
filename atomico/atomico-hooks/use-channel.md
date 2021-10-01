---
description: create connection between components to share internal states
---

# use-channel

Este hook implementa [**@atomico/channel**](https://github.com/atomicojs/channel) una alternativa a React.Context, pero basada en eventos y agnóstica. 

### Modulo

```javascript
import { useChannel } from "@atomico/hooks/use-channel";
```

### Syntax

```javascript
const channel = "MyChannel";
const [parentValue, setChildValue] = useChannel(channel);
```

Where :

1. `channel`: `String`, defines the name of the event to be used to generate the channel.
2. `parentValue`: Value inherited by the parent component.
3. `setChildValue`: `Callback`, defines a value for nested components.

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/34DlYUfeqmk0sO3BUa31/src/index.jsx" %}

This hook is used by [@atomico/components/router](../atomico-components/router.md)

