# Input personalizado

Es normal que toda UI usa inputs personalizados en estetica y funcionalidad, en este ejemplo crearemos un input que logre con los siguientes objetivos:

1. Estado visible como propiedad 
2. Sistema de eventos para enterar cambios de estados
3. Valor por defecto 

### paso 1 crear el web-component

Para cumplir con el objetivo Estado visible como propiedad, necesitaremos manipular desde el interior del web-component el estado de nuestra propienda visible, esto se logra mediante el hook [useProp ](../hooks/useprop.md)que permite manipular de forma anónima una propiedad visible del web-component.

```jsx
import { h, customElement, useProp } from "atomico";

function MyInput({ label }) {
  let [value, setValue] = useProp("value");
  return (
    <host>
      {label && label + " :"}
      <input oninput={({ target }) => setValue(target.value)} />
    </host>
  );
}
```

### paso 2 declara propiedad del web-component

La vista y la logica ya están resuelta en en el paso 1 ahora debemos declara la propiedad visible para finalizar los objetivos restantes.

```jsx
MyInput.props = {
  label: String,
  value: {
    type: Number,
    value: 1000,
    event: {
      type: "UpdateInput",
      bubbles: true
    }
  }
};
```

Listo los 3 objetivos resueltos, notara que el código de Atomico es bastante compacto y declarativo.

```jsx
import { h, customElement, useProp } from "atomico";

function MyInput({ label }) {
  let [value, setValue] = useProp("value");
  return (
    <host>
      {label && label + " :"}
      <input oninput={({ target }) => setValue(target.value)} />
    </host>
  );
}

MyInput.props = {
  label: String,
  value: {
    type: Number,
    value: 1000,
    event: {
      type: "UpdateMyInput",
      bubbles: true
    }
  }
};

customElement("my-input", MyInput);

```

Ud puede asociar el evento UpdateInput a windows o el tag my-input, para observar los cambios asociados a la propiedad value, ej:

```javascript
window.addEventListener("UpdateMyInput", (event)=>{
    console.log(event.target.value)
})
```

Atomico resuelve de forma automática el evento ante el cambio de la propiedad.

