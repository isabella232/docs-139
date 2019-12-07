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

Donde :

* `value` es el estado actual de la propiedad asociada al web-component
* `setValue` es una función encargada de actualizar el estado
* `propsName` es el nombre de la propiedad a modificar por `useProp`

Este hooks es util para crear web-components con Api acesible desde el web-component, eg

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

Gracias al uso de useProp vs useState ud podrá consultar el estado de la propiedad value fácilmente, eg

```javascript
document.querySelector("web-component").value
```



