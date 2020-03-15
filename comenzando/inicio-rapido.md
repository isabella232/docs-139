---
description: Inicie con Atomico en menos de 5 minutos
---

# Inicio rapido

### Creación de proyecto

El siguiente comando permite dar una estructura base para iniciar con Atomico, **complete las instrucciones de la terminal**

```bash
npm init @atomico
# after
cd ${folder}
npm install
```

Una vez finalizada la instalación de las dependencias arranque el siguiente comando.

```bash
npm run dev:doc
```

Este abrirá un servidor que permite visualizar su componente, la dirección del servidor se imprimirá en la terminal, por defecto es [http://localhost:8000/](http://localhost:8000/)

### Mi primer componente

al interior del directorio \`src/components\`, cree una carpeta que se asocie al nombre de su componente, para este ejemplo llamaremos a nuestro componente  `my-button` , a base del nombre definido crearemos los los archivos asociados a nuestro componente, eg:

```bash
src
└───components
    └───my-button
            my-button.js ## componente
            my-button.css ## css del componente
            my-button.md ## documentacion de componente
```

### Archivo my-button.js

Primero deberá importar el package atomico para crear su componente, eg:

```jsx
import { h, customElement } from "atomico";
```

Donde:

* `h` : funcion pragma que usa las declaraciones JSX
* `customElement`: funcion que permite registrar nuestro componente

Luego de la importación creemos nuestro componente solo usando una función

```jsx
import { h, customElement } from "atomico";
import style from "./my-button.css";

const MyButton = ({ label }) => (
  <host shadowDom>
    <style>{style}</style>
    {label}
  </host>
);

MyButton.props = {
  type: {
    type: String, // obliga aque la propiedad type sea solo del tipo string
    reflect: true,// permite que el estado se refleje como attributo
    value: "normal" // valor por defecto al iniciar el componente
  },
  label: {
    type: String, // obliga aque la propiedad label sea solo del tipo string
    value: "my default label"  // valor por defecto al iniciar el componente
  }
};
```

Donde:

* MyButton: Funcion que posee la vista y logica de nuestro componente
* MyButton.props : Objeto que define las propiedades/attributos a usa por nuestro webcomponent.

### Archivo my-button.md

Este archivo permite añadir y pre-visualizar su componente en el servidor.



