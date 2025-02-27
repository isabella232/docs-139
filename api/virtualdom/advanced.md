# Advanced

### Special properties

| Property   | Type    | Effect                                                                                               |
| ---------- | ------- | ---------------------------------------------------------------------------------------------------- |
| shadowDom  | Boolean | Enables the use of the shadowDOM on the node.                                                        |
| staticNode | Boolean | Render the node only once, this optimizes the update process as the node is ignored between updates. |
| cloneNode  | Boolean | clone a node of type Element                                                                         |
| $\<name>   | any     | the $ prefix allows defining  as an attribute in all cases.                                          |

### render

By default, the render is configured to be used within the webcomponent by reading the return of the function, but it can be used outside of Atomico, example:

{% tabs %}
{% tab title="function h" %}
```javascript
import { h, render } from "atomico";


render(
    h("host",{ style: {background:"red"} }
        h("h1",null,"Text content...")
    ),
    document.querySelector("#app")
);
```
{% endtab %}

{% tab title="JSX" %}
```jsx
import { h, render } from "atomico";


render(
    <host style={{background:"red"}}>
        <h1>Text content...</h1>
    </host>,
    document.querySelector("#app")
);
```
{% endtab %}

{% tab title="Template string(html)" %}
```javascript
import { html, render } from "atomico";


render(
    html`<host style=${background:"red"}>
        <h1>Text content...</h1>
    </host>`,
    document.querySelector("#app")
);
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Render rule "The first node of the render must always be the host tag".
{% endhint %}

### Constructor with custom element

This technique allows you to use any registered custom element without the need to know its `tag-name` for its use, example:

```jsx
function component(){
    return <host/>
}
// 1️⃣ We create the custom element
const Component = c(component);

// 2️⃣ We register the custom element
customElements.define("my-component", Component);

function App(){
    return <host>
        <Component/>
    </host>
}
```

Advantage :&#x20;

1. Remove leverage from tag-name&#x20;
2. Infer the types of the props and autocomplete only if you use JSX and Atomico.

### Constructor with DOM

Atomico allows the use of the DOM, for this it establishes its created or recovered node as a constructor, example:

```jsx
function component(){

    const Div = useMemo(()=>document.createElement("div"));
    
    return <host>
        <Div style="color: black">content...</Div>
    </host>
}
```

### Dynamic constructor

Atomico associates the variable associated with the instance as a constructor, example:

```jsx
function component({ subComponent }){
    const TagName = `my-${subComponent}`;
    
    return <host>
        <TagName/>
    </host>
}
```

### staticNode

allows to declare a node within the scope of the function as static, this will optimize the diff process between render, achieving better performance in cases of high stress of the UI, example:

```jsx
function component() {
  return (
    <host>
      <h1 staticNode onclick={console.log}>
        i am static node!
      </h1>
    </host>
  );
}
```

the biggest advantage of this is that the node accesses the scope of the webcomponent

### cloneNode

Allows to clone a node from the virtualDOM, example:

```jsx
const Div = document.createElement("div");

Div.innerHTML = `<h1>Div!</h1>`;

function component() {
  return (
    <host>
      <Div cloneNode onclick={console.log} />
      <Div cloneNode onclick={console.log} />
      <Div cloneNode onclick={console.log} />
      <Div cloneNode onclick={console.log} />
      <Div cloneNode onclick={console.log} />
    </host>
  );
}
```

The objective of this feature is to retrieve slot and use it as a template from the webcomponent.

### Hidratación desde SSR

Atomico permite la reutilización del DOM ya existente en el documento, esto se realiza al momento de la instancia del webcomponent definiendo una propiedad especial sobre la etiqueta a hidratar

```markup
<my-webcomponent data-hydrate>
    <h1>I will be the title of the component</h1>
</my-webcomponent>
```

El shadowDOM también puede ser hidratado ejemplo:

```markup
<my-webcomponent data-hydrate>
    <template shadowroot="open">
        <h2>Shadow Content</h2>
        <slot></slot>
        <style>shadow styles</style>
    </template>
    <h2>Light content</h2>
</my-webcomponent>
```

{% hint style="info" %}
El código expuesto aun no es parte del estándar, es una propuesta impulsada por el **Google Chrome** [https://web.dev/declarative-shadow-dom/](https://web.dev/declarative-shadow-dom/), para ser usada en todos los browser debe hacer uso de polyfills.&#x20;
{% endhint %}
