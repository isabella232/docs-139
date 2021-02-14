---
description: Observe y compruebe los cambios del DOM manualmente.
---

# Test DOM

Para leer el DOM del webcomponent generado con Atomico es necesario conocer el ciclo de renderización a base de promesas.

### HTMLElement.mounted

Esta promesa solo será resuelta una vez que el webcomponent sea montado.

```jsx
const myElement = new MyElement();

await myElement.mounted;

console.log("component mounted!");
```

### HTMLElement.updated

Esta promesa sera 

```jsx
const myElement = new MyElement();

await myElement.unmounted;

myElement.myProp1 = "value 1";
myElement.myProp2 = "value 2";

await myElement.updated;

console.log("webcomponent updated");
```

### 

### HTMLElement.unmounted

```jsx
const myElement = new MyElement();

await myElement.unmounted;

console.log("component unmounted!");
```



