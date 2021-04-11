---
description: create connection between components to share internal states
---

# use-channel

## Modulo

```javascript
import { useChannel } from "@atomico/hooks/use-channel";
```

## Syntax

```javascript
const channel = "MyChannel";
const [parentValue, setChildValue] = useChannel(channel);
```

Where :

1. `channel`: `String`, defines the name of the event to be used to generate the channel.
2. `parentValue`: Value inherited by the parent component.
3. `setChildValue`: `Callback`, defines a value for nested components.

## Example

This hook is used by [@atomico/components/router](../atomico-components/router.md)

