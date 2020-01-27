---
description: >-
  Use prop permite reflejar parte del comportamiento de useState a una propiedad
  del web-component.
---

# useProp

### Sintaxis 

```javascript
let [value, setValue] = useProp(propName);
```

Where:

* `value` : Any, is the current state of the property associated with the web-component
* `setValue` : Function, allows updating the state of the prop.
* `propsName` : String, property name to modify by `useProp`

This hook is useful for creating web-components with Api publica from the web-component, eg:

```jsx
import { h, customElement, useProp } from "atomico";

function WebComponent(){
    let [value,setValue] = useProp("value");
    return <host>
        <button onclick={()=>setValue(value+1)}>
            increment
        </button>
        value : {value}
    </host>    
}

WebComponent.props = {
    value : Number
}
```

using useProp allows you to check the state of the value property easily, eg:

```javascript
document.querySelector("web-component").value
```

