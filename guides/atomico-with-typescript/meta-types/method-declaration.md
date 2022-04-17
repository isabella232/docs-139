# Method declaration

Atomico allows the definition of methods from the host tag, this in order to share the scope with the methods (Functions) of the component, but this escapes the definition of types, to patch this we must use the Host type, this will allow us to validate the method from the JSX, TSX and the component instance.

### Host to method declaration

```typescript
import {Host} from "atomico";

type MyMethod = (value: number)=>void;

function component():Host<{myMethod: MyMethod }>{
    const myMethod: MyMethod = ()=>{}
    return <host myMethod={myMethod }/>
}
```

