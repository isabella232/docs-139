---
description: >-
  Atomico esta pensado para una mantencion simple de llevar,  a continuación
  algunos tips utils para proyectos con Atomico.
---

# Recomendaciones

### Instalación

prefiera la instalación mediante el  comando \`npm init @atomico\`, este descargara una configuración  para iniciar su proyecto desde [github.com/atomicojs/base](https://github.com/atomicojs/base), **esta configuración posee la estructura recomendada para su proyecto**

Atomico agiliza la creación y documentación de componentes mediante bundle-cli, este permite empaquetar tanto su componente, hooks y documentación, siga estas recomendaciones para facilitar el proceso de empaquetado.

### Directorio

El directorio recomendado para la exportación se basa en la declaración de componentes  en carpetas únicas que agrupen estilo y documentación, prefiera el uso de  Kebab Case para definir el formato de nombre  de directorio  y fichero, ej:

```bash
src/
    components/
        my-component/
            my-component.js
            my-component.css
            my-component.md
    custom-hooks/
        my-hook
            my-hook.js
            my-hook.md
```

#### \#\#\# Scripts

Los scripts 

#### Observaciones de sintaxis 

#### Fichero tipo js,  para componente.



```jsx
import {h, customElement} from "atomico";

const MyComponent = ()=>{
    return <host></host>
};

MyComponent.props = {
    myProp : {
        type : String
    }
}
```

