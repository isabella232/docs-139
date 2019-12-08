---
description: >-
  Atomico allows an uncomplicated migration with React, for this you must follow
  the following steps based on the following example.
---

# From React to Atomico

### Code to migrate

```jsx
import React, { useEffect, useState} from "react";

export default function Counter() {
  let [count, setCount] = useState(0);

  useEffect(() => {
    let interval = setInterval(() => setCount(state => state + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <h1 class="title">React counter : {count}</h1>;
}

```

 a counter based on hooks, this by means of an interval updates its state every 1000ms.

### Step 1

 Define the local pragma `/*@jsx h*/`, this will internally replace `React.createElement`, this change does not modify the configuration of your environment and allows you to keep React and Atomico working in parallel together, if you want to completely eliminate React you can modify the pragma from babel and avoid using this step.

```jsx
/*@jsx h*/
```

### Step 2

Modify import, Atomico groups everything you need to replace React in the `"atomico"` main module.

```jsx
/*@jsx h*/
import { h, customElement, useEffect, useState } from "atomico";

function Counter() {
  let [count, setCount] = useState(0);

  useEffect(() => {
    let interval = setInterval(() => setCount(state => state + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <h1 class="title">Atomico counter : {count}</h1>;
}

customElement("atomico-counter", Counter);

```

Where: 

* `h`: pragma function used to generate the Atomico JSX.
* `customElement`: function that registers the web-component to be used as a global HTML tag.

**Atomico will work without problem in conjunction with React for a progressive migration, you can see this example that shows how Atomico works in an environment managed by React.**

{% embed url="https://codesandbox.io/s/react-example-xyhf9" %}

### Improving the code

The example shown presents you with 2 problems that we can fix with Atomico:

1. The CSS of the component is global, this prevents sharing our component effectively.
2. We cannot know the internal state of the component as we would do with the input tag, eg `document.querySelector("input").value`**.**

```jsx
let styleSheet = /*css*/`
  .title{ font-family : monospace }
`;

function Counter() {
  let [count, setCount] = useProp("count");

  useEffect(() => {
    let interval = setInterval(() => setCount(state => state + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <host shadowDom styleSheet={styleSheet}>
    <h1 class="title">Atomico counter : {count}</h1>
  </host>;
}

Counter.props = {
  value  : Number
}

```

 Where: 

* `styleSheet` : Css associated only to the web-component.
* `useProp`: Hook that allows to use a property of the web-component as a state, this allows an external reading.
* `host` : tag pointing to the same web-component
* `host[shadowDom]`: Property of the virtual-dom to activate the use of shadow Dom
* `host[styleSheet]` : Pproperty that allows you to associate the use of CSS with the web-component, the use of this property optimizes the use of css according to the browser
* `Counter.props`: Object that declares the properties of the web-component



