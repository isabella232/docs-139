---
description: >-
  Atomico provides coverage to essential aspects for behavior in environments
  based on typescript.
---

# Atomico + Typescript

### Component declaration

```typescript
import { h, customElement, Component } from "atomico";
​
const MyComponent: Component = () => <host />;
​
MyComponent.props = {
  value: { type: String, value: "..." }
};
```

The `Component` type adds the autocomplete rules for its component.

### Declarations for hooks

All hooks have declarations of defined types, then only those of dynamic type are exposed, the unexposed ones have the benefit of autocomplete.

#### useProp

```typescript
let [value, setValue] = useProp<number>("myProp");
```

The statement stated, assigns rule that `value` and `setValue` only accept values type `number`

#### useState

```typescript
// case 1
let [state, setState] = useState(0);
// case 2
let [state, setState] = useState(()=>0);
// case 3
let [state, setState] = useState<number>();
```

The stated statement allows you to assign the rule that `state` and `setState` only accept values type `number`

#### useRef

```typescript
let ref = useRef<HTMLInputElement>();
```

the statement stated defines that ref.current will be or should be an element instantiated from `HTMLInputElement`, by default if the type is not declared it is filled with the `Element` type

#### useMemo

```typescript
// case 1
let value = useMemo(()=>100);
// case 2
let value = useMemo<number>(processComplex);
```

The stated statement assigns the rule that value is of type number

#### useReducer

```typescript
// case 1
let [state, dispatch] = useReducer(reducer,10);
// case 2
let reducer = (state,action)=>10;
let [state, dispatch] = useReducer(reducer);
// case 3
let [state, dispatch] = useReducer<number>(reducer); 
```

The stated statement assigns the rule that value is of type number

