# Advanced

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

Advantage : 

1. Remove leverage from tag-name 
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

### Static nodes

Atomico allows you to reuse static nodes, improving performance, example:

```jsx
const header = <header></header>;

function component(){
    return <host>
        {header}
    </host>
}
```

Consider using static nodes as a contextual technique, it is not a rule.

