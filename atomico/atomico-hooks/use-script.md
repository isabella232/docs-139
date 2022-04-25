---
description: load global scripts when mounting the component
---

# use-script

### Syntax

```typescript
const src = "https://code.jquery.com/jquery-3.6.0.min.js";
const done = ()=> console.log( $ );
const status = useScript(src, done);
```

where:

1. `src`: javascript type resource to inject into document.head
2. `done`: optional , callback when called at the end of the script load
3. `status`: script load status

