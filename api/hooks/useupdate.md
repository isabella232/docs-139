---
description: 'Force an update, ideal for working with references'
---

# useUpdate

It is normal that the state of your component depends on the references of a slot, this hook facilitates the process of observing these references without the need to associate the changes to a state.

### Syntax

```javascript
const update = useUpdate();
```

Where:

1. `update`: Callback, force component update.

