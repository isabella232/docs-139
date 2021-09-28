# Untitled

Atomico's virtualDOM is: 

1. Close to standard DOM .
2. Additional coverage to webcomponents.

### Components as constructors

Atomico does not support the use of functions to instantiate the component as we traditionally do in React, so that the component can be instantiated as a constructor it must be a webcomponent or a real Node.

{% tabs %}
{% tab title="❌ Not supported" %}
```jsx
function Component(){
    return <host></host>
}

function App(){
    return <host>
        <Component/>
    </host>
}
```
{% endtab %}

{% tab title="✔️ Spported" %}
```jsx
function component(){
    return <host></host>
}

const Component = c(component);
customElements.define("my-component",Component)

function app(){
    return <host>
        <Component/>
    </host>
}
```
{% endtab %}

{% tab title="✔️ Supported" %}
```jsx

function app(){
    const Div = document.createElement("div");
    return <host>
        <Image/>
        <Div/>
    </host>
}
```
{% endtab %}
{% endtabs %}

### Event Association

Like React in Atomico you need to use the prefix on to announce an event, but there is a difference **Atomico does not manipulate the name of the event so `onClick` is different from `onclick`**, the purpose of this difference is to support custom events.

```jsx
<div>
    <button onclick={console.log}>click</button>
    <button onMyCustomEvent={console.log}>click</button>
    <button onmy-event={console.log}>click</button>
    <button onmouseover={console.log}>click</button>
</div>
```

### Keyes

the `key` property in Atomicoo can be of type String, Number, Symbol or other immutable reference.

```jsx
<div>
    <div key={1}>1</div>
    <div key={symbol}>1</div>
    <div key={immutable}>1</div>
</div>
```

### dangerouslySetInnerHTML

```jsx
<div innerHTML={`<h1>html!</h1>`}/>
```



