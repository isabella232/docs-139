# Rendering Differences

Atomico escapes React DOM immutability logic and moves closer to the native DOM API, this means that Atomico at the scope level is only responsible for receiving the props and rendering the DOM, but it does not observe the internal mutations of the DOM automatically, this is because the native level mutations can come from anywhere, for example other libraries. Now for ensure state synchronization it is convenient that every webcomponent that wants to be observed has the obligation to dispatch a change event

You can easily achieve this by using [useevent.md](../../../api/hooks/useevent.md "mention") or [#prop.event](../../../api/props/#prop.event "mention"), applying that you can:

**capture change as event**

```jsx
const [ value, setValue ] = useState("init"); // you can also use useProp

<host>
    <my-component 
        value={value} 
        onchange={({target})=>setValue(target.value)}
    ></my-component>
</host>
```

**Force a fixed value**

```jsx
const update = useUpdate();

<host>
    <my-component 
        value={value} 
        onchange={update}></my-component>
</host>
```

the `update` function forces an update on the component, in order to redefine value according to the scope
