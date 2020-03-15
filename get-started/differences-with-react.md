---
description: >-
  Atomico has a style inherited from React, but with some differences in favor
  of using web-components
---

# Differences with React

### Event handling

```jsx
// React
<button onClick={handler}>...</button> 

// Atomico
<button onclick={handler}>...</button>
```

Atomico detects events based on 2 conditions that the prop begins with the prefix `on` and that the value is a function, **the only transformation when associating the event is the elimination of the prefix `on`, this in favor of the use of custom events**, eg:

```jsx
<button onMyEvent={handler}>...</button> // addEventListener("MyEvent",handler)
```

### Composition

Atomico uses customElements as a component system, this forces the host to exist to associate a life cycle and use hooks, eg:

```jsx
function WebComponent(){
    return <host>
        web-component
        <Button onclick={handler}>...</Button>
    </host>
}

function Button({onclick, children}){
    return <button onclick={onclick}>{children}</button>
}
```

The previous example shows a valid composition syntax for Atomico, but **you will not be able to use Hooks inside components that are not a customElement**, in the previous case  you will not be able to use hooks. if you want button to contain hooks declare it as customElement, eg

{% embed url="https://webcomponents.dev/edit/zaXQCViR8OuiPMeHLK1R" %}

#### Slots y Children 

You can use Slots if you declare the shadowDom property on the host tag, the advantage of slots is that the nodes are natively reflected within the associated slot, but they behave differently than using children:

1. the slot can exist before the web-component that uses it
2. If invoked from HTML, its representation cannot be avoided, therefore its execution cannot be conditioned.
3. You cannot iterate over slots like you do with children.

**The use of Slot vs Children is recommended since the slot is agnostic to libraries.**

Can children be used between custom elements? Yes, but only between customElements declared with Atomico, for example:

```jsx
function WebComponent1(){
    return <host>
        <web-component-2>
            <span>child 1</span>
            <span>child 2</span>
            <span>child 3</span>
        </web-component-2>
    </host>
}

function WebComponent2({children}){
    return <host shadowDom>
        <ul>
            {children.map(({child})=><li>{child}</li>)}
        </ul>
    </host>
}

WebComponent2.props = {
    children : Array
}

customElement("web-component-1",WebComponent1);
customElement("web-component-2",WebComponent2);
```



