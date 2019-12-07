# Props



Atomico improves the experience of defining properties associated with the web-component, by using the props object, you can define attributes and properties, eg:

```javascript
WebComponent.props = {
    simpleProp : String,
    advaceProp : {
        type : String,
        reflect : true,
        value : "default string",
        event : {
            type : "UpdateAdvanceProp",
            bubbles : true,
         }
    }
}
```

### Simple definition

The simple definition accelerates the reading of the property, this will not include associated effects as a default value, reflect as an attribute or issue events before the change, eg:

```javascript
WebComponents.props = {
    propString : String, // attribute, eg: prop-string='hi!'
    propNumber : Number, // attribute, eg: prop-number='10'
    propObject : Object, // attribute, eg: prop-object='{}'
    propArray  : Array,  // attribute eg: prop-array='[]'
    propDate   : Date,   // attribute eg: prop-date='2019-12-05',
    propBool   : Boolean // attribute eg: prop-bool
}
```

### Advanced definition of props

It improves the simple definition by adding utilitarian declarations, allowing to declare in an object associated to the prop, type, reflection as attribute, default value and emission of events before the change.

#### Prop.type

```javascript
// valid declaration
WebComponents.props = { myName : String }
// valid declaration
WebComponents.props = { myName : {type : String} }
```

| Type | `reflect` |
| :--- | :--- |
| String | Si |
| Number | Si |
| Boolean | Si |
| Date | Si |
| Object | Si |
| Array | Si |
| Promise | No |
| Symbol | No |
| RegExp | No |

#### Prop.reflect

If `true`, it will reflect the property as an attribute, this is useful for the declaration of CSS states, eg:

```jsx
let styleSheet = /*css*/`
    :host{
        background:black;
    }
    :host([checked]){
        blackground:white;
    }
`;
WebComponent.props = {
    checked : {
        type : Boolean,
        reflect : true
    }
}
```

#### Prop.event

It allows dispatching an event before the change of value of the prop, if it is defined as true the event to be emitted will take the name of the prop.

```javascript
WebComponent.props = {
    simpleEvent : {
        type : String,
        event : true,
    }
}
// listener example

nodeWebComponent.addEventListener('simpleEvent',handler); 
```

if defined by an `object`, you can configure the type and behavior of the event

```jsx
WebCompoent.props = {
    advanceEvent : {
        type : String, 
        event : {
            type : "myCustomEvent",
            bubbles : true,
            detail : "any message",
            cancelable : true,
            composed: true
        }
    }
}
```

Where: 

* `event.type` : String - optional, name of the event to be emitted before the change of the prop
* `event.bubbles` : Boolean - optional, indicates that the event can be subscribed by the containers.
* `event.detail` : Any - optional, allows you to attach custom event information.
* `event.cancelable` : Boolean - optional, indicates that the event can be canceled by a listener
* `event.composed` :  Boolean - optional, allows the event to exceed the shadow-root limit

The special properties of the event are known as the EventInit standard, you can find out more detail in the[ attached documentation](https://developer.mozilla.org/en-US/docs/Web/API/Event/Event)

#### Prop.value

Atomico allows the definition of default values of the props.

```javascript
WebComponents.props = {
    valueNormal : {
        type : Number,
        value : 100
    },
    valueObject : {
        type : Object,
        get value(){
            return { ...defaultState }
        }
    }  
}
```

{% hint style="warning" %}
Use **getter** if you want the value to be unique between instances, this is required if you use **Array** and **Object** types.
{% endhint %}

### Effects of prop mutation

It is common to see this type of behavior when working with web-components, eg

```javascript
let node = document.querySelector("custom-element");

node.checked = true;

node.checked = !node.checked;
```

they are considered valid, but to create a functional orientation the atomico props can be defined as state reducers, eg:

```javascript
node.checked = (currentState)=>!currentState;
```

Atomico groups the updates coming from the props to generate a single render, if you want to see the side effect of your update on the props you should do the following:

```javascript
node.prop1 = 1;
node.prop2 = 2;
node.prop3 = 3;

await node.rendered;

/** any side effects, eg: analysis of the resulting DOM **/
```

{% hint style="warning" %}
Your WebComponent does not receive references from the props, each render receives an immutable snapshot.
{% endhint %}



