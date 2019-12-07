# De React a Atomico

Atómico permite una migración sin complicaciones con React, para ello ud deberá seguir los siguientes pasos a base del siguiente ejemplo:

```jsx
import React, { useEffect, useState} from "react";

export default function Counter() {
  let [count, setCount] = useState(0);

  useEffect(() => {
    let interval = setInterval(() => setCount(state => state + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <h1 class="title">React counter : {count}</h1>;
}

```

 un contador basado en hooks, este mediante un intervalo actualiza su estado cada 1000ms.

### Paso 1

 Definir el pragma local `/*@jsx h*/`, esto internamente remplazara `React.createElement`, Este cambio no modifica la configuración de su entorno y permite mantener React y Atómico funcionando en paralelo, si busca eliminar por completo a React puede modificar el pragma desde babel y evitar usar este paso

```jsx
/*@jsx h*/
```

### Paso 2

Modificar importación, Atómico agrupa todo lo que necesita para remplazar a React en el modulo principal `"atomico"`

```jsx
/*@jsx h*/
import { h, customElement, useEffect, useState } from "atomico";

function Counter() {
  let [count, setCount] = useState(0);

  useEffect(() => {
    let interval = setInterval(() => setCount(state => state + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <h1 class="title">Atomico counter : {count}</h1>;
}

customElement("atomico-counter", Counter);

```

Donde : 

* h: función pragma usada para generar el JSX de Atomico
* customElement: función que registra el WebComponent para ser usado como tag HTML global.

**Atomico funcionara sin problema de forma conjunta con React para una migración progresiva, puede ver este ejemplo que muestra como Atomico funciona en un entorno gestionado por React.**  [**https://codesandbox.io/s/react-example-xyhf9**](https://codesandbox.io/s/react-example-xyhf9)\*\*\*\*

### Mejorando el codigo de React

El ejemplo enseñado previamente presenta 2 problemas:

1. El estilo del componente es globa, esto impide compartir nuestro componente de forma efectiva.
2. No podemos conocer el estado interno del componente, de forma externa como lo haríamos con el tag input, eg `document.querySelector("input").value`

```jsx
let styleSheet = /*css*/`
  .title{ font-family : monospace }
`;

function Counter() {
  let [count, setCount] = useProp("count");

  useEffect(() => {
    let interval = setInterval(() => setCount(state => state + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <host shadowDom styleSheet={styleSheet}>
    <h1 class="title">Atomico counter : {count}</h1>
  </host>;
}

Counter.props = {
  value  : Number
}

```

 Donde : 

* `styleSheet` : Css asociado solo al webComponent.
* `useProp` : Remplaza a useEffect para usar una propiedad del webComponent como estado, esto permite una lectura externa.
* `host` : tag que apunta al mismo web-component 
* `host[shadowDom]`: Propiedad del webComponent para activar el  uso del shadowDom
* `host[styleSheet]` : propiedad que permite asociar el uso de CSS al webComponent, el uso de esta propiedad optimiza la utilización del css en función del navegador
* `Counter.props`: Objeto que declara las propiedades del webComponent



