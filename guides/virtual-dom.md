---
description: Efficient and extremely small.
---

# Virtual dom



The Atomico virtual-dom is small and is only processed when the object is sent for rendering, you can manifest the virtual-dom using jsx, template-string or a flat object.

### Syntax

```jsx
// JSX
<host>
    <button onclick={handler}>text</button>
</host>

// Template string
html`
    <host>
        <button onclick=${handler}>text</button>
    </host>
`

// Object

{
    nodeType : "host",
    children : [{
        nodeType : "button",
        onclick : handler
    }]
}
```

All the exposed syntaxes are considered valid, the Atomico virtual-dom does not maintain references so you can reuse a node without problems between components, this is highly efficient if you want the render process to ignore static nodes, eg:

```jsx
let static = <h1>node!</h1>

function WebComponent({value}){
    return <host>
        {static}
        <h1>dinamic {value}</h1>
    </host>
}
```

### Lists and Keyes

The render process reuses existing nodes when a new children map is generated, eg:

```jsx
<host>
    <my-tag/>
    <my-tag/>
    <my-tag/>    
</host>
```

This brings problems when each node retains an independent state, since each new list does not reference the node based on its state.

This is solved with the use of the key property, this property allows Atomico to reference the node not by position in the list, but by the referential index, this index must meet the following requirements:

1. Unique among all the brothers
2. All brothers must also have an index

```jsx
<host>
    <my-tag key="1"/>
    <my-tag key="2"/>
    <my-tag key="3"/>   
</host>
```

This optimizes the manipulation of the sun by regenerating and maintaining the states associated with the node correctly.

### shadowDom

Special property of virtual-dom that allows to activate the shadowDom of a node, eg

```jsx
<host shadowDom>
    inside shadowDom!
</host>

<host>
    inside lightDom!
</host>
```

This property can be used on any node that supports attachShadow

### styleSheet

It allows to optimize the use of the css associated to the web-component, allowing to use [**Constructable StyleSheet**](https://developers.google.com/web/updates/2019/02/constructable-stylesheets) only when it is available in the browser, to improve the experience without using Polyfill of Constructable Stylesheets it is advisable to use styleSheet as a String, eg

```jsx
let styleSheet = `
    :host{width:100px;height:100px}
`
<host shadowDom styleSheet={styleSheet}>

</host>
```

Each time Atomico processes the variable as String, cache the StyleSheet instance by building a single instance that can be associated with multiple web-components.

{% hint style="danger" %}
To use **styleSheet** only works together with the **shadowDom** property
{% endhint %}

### is

the web-components allow to extend functionalities on existing tags in the document through the use of **is**, atomico supports this declaration, eg:

```jsx
<button is="my-button"></button>
```

### Events

The association of events in Atomico requires 2 conditions:

1. the name of the event must begin with the prefix **on**.
2. the event name value must be a function.

```jsx
<host onclick={handler} onmyCustomEvent={handler}>
</host>
```

{% hint style="danger" %}
Atomico does not apply additional transformers outside of removing the prefix **on** to subscribe the event.
{% endhint %}



