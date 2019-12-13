---
description: >-
  use recursive and asynchronous generators to compose stream logic, in short
  one monad.
---

# atomico/use-state-generator

### useStateGenerator

#### Syntax

```javascript
let [state, promise] = useStateGenerator(callbackGenerator, initialState, vars);
```

Where:

* `state` : It is the current state of the hook.
* `promise` : It is a promise that defines whether the asynchronous process of `useStateGenerator` : has ended.
* `callbackGenerator` : Function, generator or asynchronous generator to be consumed by `useStateGenerator`
* `initialState`: initial state of the hook.
* `vars`: it is an array of variables to observe between renders, if one of these elements is differentregenera el hook ejecutando nuevamente `callbackGenerator`.

#### Example

```javascript
import { useStateGenerator, delay} from "atomico/use-state-generator";
/** inside web-component */
let length = 10;
let [state] = useStateGenerator((state)=>{
    while(--state){
        yield delay(1000);
        yield state;
    }
    return state;
},0, [length])
```

The previous example generates a countdown of 10..1, each step is 1000ms.

