---
description: Check DOM changes manually.
---

# Test DOM

## Render cycle

To read the DOM of the webcomponent generated with Atomico it is necessary to know the rendering cycle based on promises.

### HTMLElement.mounted

Promise that will only be resolved once the webcomponent is mounted.

```jsx
const myElement = new MyElement();

await myElement.mounted;

console.log("mounted!");
```

### HTMLElement.updated

Promise that will only be resolved after mounted and will be created each time there is a rendering task.

```jsx
const myElement = new MyElement();

myElement.myProp1 = "value 1";
myElement.myProp2 = "value 2";

await myElement.updated;

console.log("updated");
```

### HTMLElement.unmounted

Promise that will be resolved once the webcomponent has been removed from the Document.

```jsx
const myElement = new MyElement();

await myElement.unmounted;

console.log("unmounted!");
```
