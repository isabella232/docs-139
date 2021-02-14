---
description: Observe y compruebe los cambios del DOM manualmente.
---

# Test DOM

## Ciclo de renderización

Para leer el DOM del webcomponent generado con Atomico es necesario conocer el ciclo de renderización a base de promesas.

### HTMLElement.mounted

Esta promesa solo será resuelta una vez que el webcomponent sea montado.

```jsx
const myElement = new MyElement();

await myElement.mounted;

console.log("mounted!");
```

### HTMLElement.updated

Esta promesa será resuelta luego de mounted y se creara cada vez que exista una tarea de renderización, las tareas son acumulable por lo que ud puede modificar múltiples actualizaciones y estas se resolverán en un solo render.

```jsx
const myElement = new MyElement();

myElement.myProp1 = "value 1";
myElement.myProp2 = "value 2";

await myElement.updated;

console.log("updated");
```

### HTMLElement.unmounted

Esta promesa será resuelta una vez que el webcomponent haya sido desmontado del Documento.

```jsx
const myElement = new MyElement();

await myElement.unmounted;

console.log("unmounted!");
```





