# Type

Although the props today offer strict rules, Type allows them to be complemented with a direct definition of the types to accept, example:

```typescript
import { Props } from "atomico";

function component(){
    return <host/>
}

component.props = {
    value: String as Type<"A"|"B"|"C">
}
```

The above is equivalent to using value as a function, example:

```typescript
import { Props } from "atomico";

function component(){
    return <host/>
}

component.props = {
    value: {
        type: String,
        value: ():"A"|"B"|"C"=>"A"
    }
}
```

This is also valid for the null type that in Atomic translates as Any, example:

```typescript
component.props = {
    src: null as Type<string | Promise<any>>
}
```

