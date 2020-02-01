---
description: >-
  Atomico entrega cobertura a aspectos esenciales para un comportamiento en
  entornos basado en typescript.
---

# Atomico + Typescript

### Declaración de componente

Mediante la importación `Component` desde el modulo Atomico ud podrá obtener las funciones de autocompletado de esta interfaz.

```typescript
import { h, customElement, Component } from "atomico";
​
const MyComponent: Component = () => <host />;
​
MyComponent.props = {
  value: { type: String, value: "..." }
};
```

### Declaraciones para hooks

Todos los hooks posen declaraciones de tipos definidas, a continuación solo se exponen las de tipo dinámico, las no expuestas poseen el beneficio de auto-completado.

#### useProp

```typescript
let [value, setValue] = useProp<number>("myProp");
```

La declaración expuesta, dar como regla que value y setValue solo acepte valores tipo `number`

#### useState

```typescript
// caso 1
let [state, setState] = useState(0);
// caso 2
let [state, setState] = useState(()=>0);
// caso 3
let [state, setState] = useState<number>();
```

La declaración expuestas, permite dar como regla que state y setState solo acepte valores tipos `number`

#### useRef

```typescript
let ref = useRef<HTMLInputElement>();
```

la declaración expuesta, define que `ref.current` sera o debe ser un elemento instanciado desde `HTMLInputElement`, por default si no se declara el tipo se rellena con el tipo `Element`

#### useMemo

```typescript
// caso 1
let value = useMemo(()=>100);
// caso 2
let value = useMemo<number>(processComplex);
```

La declaración expuesta, dar como regla que `value` sea del tipo `number`

#### useReducer

```typescript
// caso 1
let [state, dispatch] = useReducer(reducer,10);
// caso 2
let reducer = (state,action)=>10;
let [state, dispatch] = useReducer(reducer);
// caso 3
let [state, dispatch] = useReducer<number>(reducer); 
```

La declaración expuesta, dar como regla que `value` sea del tipo `number`

