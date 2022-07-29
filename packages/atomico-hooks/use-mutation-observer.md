---
description: Observe the changes of a reference using MutationObserver
---

# use-mutation-observer

### Module <a id="modulo"></a>

```javascript
import { 
    useMutationObserver, 
    useMutationObserverState 
} from "@atomico/hooks/use-mutation-observer";
```

### useMutationObserver syntax <a id="sintaxis-usemutationobserver"></a>

Observe mutations using a callback

```typescript
useMutationObserver(    
    ref: Ref<Element>,    
    observe: MutationCallback,    
    config?: MutationObserverInit
);
```

### useMutationObserver syntax <a id="sintaxis-usemutationobserver-1"></a>

Reflects mutations in a state

```typescript
const mutations:MutationRecord[] = useMutationObserverState(    
    ref: Ref<Element>,    
    config?: MutationObserverInit
);
```

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/DuOt53NoiMeLZfQKfVuf/src/index.jsx" %}



### [ ](https://atomico.gitbook.io/doc/v/es/atomico/atomico-hooks/use-async-effect)

