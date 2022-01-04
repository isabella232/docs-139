---
description: >-
  Atomico inherits part of the React syntax and applies it to webcomponents,
  with a closer to standard approach.
---

# ⚛ From React to Atomico

### If you develop with React, you will know 80% Atomico ... now why use Atomico?:

1. **Atomico will not limit your React learning curve**, what you learned in Atomico is applicable in React, for example hooks and virtualDOM.
2. **Atomico is 3kB** in size which is 7% of React + React-dom.
3. **Better component abstraction**, for example the use of the ShadowDOM will avoid the need to use css-in-js like styles-components or emotion, reducing dependencies.
4. **Agnostic Components**, what you create with React only works within React, what you create with Atomico works on the web, so you can your components within React, Vue, Svelte or Html.
5. **Exclusive component for React**, the CLI @ atomico / exports automatically generates a wrapper component of your webcomponent for React, improving backward compatibility with React.

The following examples show some differences between React and Atomico.

### Counter example

{% tabs %}
{% tab title="React" %}
```jsx
import { useState } from "react";
import ReactDOM from 'react-dom'

function Counter({initialCount}) {
  const [count, setCount] = useState(initialCount);
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(initialCount)}>Reset</button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </>
  );
}


render(
  <Counter initialCount={1}/>, 
  document.querySelector("#counter")
);
```
{% endtab %}

{% tab title="Atomico ✅" %}
```jsx
import { c, useProp } from "atomico";

function counter() {
  const [count, setCount] = useProp("count");
  return (
    <host>
      Count: {count}
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </host>
  );
}

counter.props = { count: { type: Number, value: 0 } }

const Counter = c(counter);

customElements.define(
  "my-counter",
  Counter  
);
```
{% endtab %}
{% endtabs %}

From the example we will highlight the following differences:

1. In Atomico you only use one import.
2. `useProp` is like `useState`, but with the difference that useProp references the state from the webcomponent property defined in `counter.props`.
3. `counter.props` allows us to create the properties of our webcomponent, these are like React's propTypes, but with a big difference they are associated with the instance and can be read and modified by referencing the node, example `document.querySelector("my-counter").count = 10;`
4. `ReactDom.render` needs a reference to mount the component, in Atomico you only need to create the `my-counter` tag to create a new instance of the component.
5. The `<host/>` tag is similar to `<> </>` for React, but  `<host/>` represents the webcomponent instance and **every component created with Atomico must return the host tag**
6. This is only readability, but in Atomico by convention we do not use capital letters when naming our component, these are only used when creating the customElement as in line 16, since `Counter` is instantiable.

### CustomHooks example

{% tabs %}
{% tab title="React" %}
```jsx
import { useEffect, useState } from "react";

function useJsonPlaceholder(path) {
  const [state, setState] = useState();
  useEffect(() => {
    let cancel;
    setState(null);
    fetch(`https://jsonplaceholder.typicode.com/${path}`)
      .then(() => res.json())
      .then((data) => !cancel && setState( data ));
    return () => (cancel = true);
  }, [path]);
}

function Component() {
  const posts = useJsonPlaceholder("posts");
  return (
    <>
      {posts 
        ? posts.map(({ title }) => <h1>{title}</h1>)
        : "Loading..."}
    </>
  );
}
```
{% endtab %}

{% tab title="Atomico ✅" %}
```jsx
import { useEffect, useState } from "atomico";

function useJsonPlaceholder(path) {
  const [state, setState] = useState();
  useEffect(() => {
    let cancel;
    setState(null);
    fetch(`https://jsonplaceholder.typicode.com/${path}`)
      .then(() => res.json())
      .then((data) => !cancel && setState( data ));
    return () => (cancel = true);
  }, [path]);
}

function component() {
  const posts = useJsonPlaceholder("posts");
  return (
    <host>
      {posts 
        ? posts.map(({ title }) => <h1>{title}</h1>)
        : "Loading..."}
    </host>
  );
}
```
{% endtab %}
{% endtabs %}

From the example we will highlight the following differences:

1. The hook api is the same.
2. the component in Atomico returns the \``<host/>` tag.

#### Supported hooks

In Atomico you will have the most useful React hooks such as:

1. useRef
2. useState
3. useReducer
4. useLayoutEffect
5. useEffect
6. useMemo
7. useCallback
8. ~~useContext~~ : **Not supported**, event api is better practice than context when using webcomponents, example [**useChannel**](../../../atomico/atomico-hooks/use-channel.md)****

### CSS-in-JS

It is common to see the use of libraries such as Emotion or styled-components to encapsulate styles in React, but these add an additional cost, be it for performance or bundle, in Atomico there is no such cost.

{% tabs %}
{% tab title="React" %}
```jsx
const Button = styled.a`
  /* This renders the buttons above... Edit me! */
  display: inline-block;
  border-radius: 3px;
  padding: 0.5rem 0;
  margin: 0.5rem 1rem;
  width: 11rem;
  background: transparent;
  color: white;
  border: 2px solid white;

  /* The GitHub button is a primary button
   * edit this to target it specifically! */
  ${props => props.primary && css`
    background: white;
    color: black;
  `}
`

render(
  <div>
    <Button
      href="https://github.com/styled-components/styled-components"
      target="_blank"
      rel="noopener"
      primary
    >
      GitHub
    </Button>

    <Button as={Link} href="/docs">
      Documentation
    </Button>
  </div>
)
```
{% endtab %}

{% tab title="Atomico  ✅" %}
```jsx
import { c, css } from "atomico";

function button() {
  return <host shadowDom><slot/></host>;
}

button.props = { primary: { type: Boolean, relfect: true } };

button.styles = css`
  :host {
    display: inline-block;
    border-radius: 3px;
    padding: 0.5rem 0;
    margin: 0.5rem 1rem;
    width: 11rem;
    background: transparent;
    color: white;
    border: 2px solid white;
  }

  :host([primary]) {
    background: white;
    color: black;
  }
`;

export const Button = c(button);
```
{% endtab %}
{% endtabs %}
