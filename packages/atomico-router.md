---
description: powerful router for Webcomponents, React and Preact
---

# @atomico/router

@atomico/router aims to facilitate the creation of SPA-type applications through the following strategies:

1. &#x20;**slot**: you can reference a slot within the Router Switch to show on a specific path.
2. **elements**: you will be able to mount CustomElements through Instantable elements.
3. **asynchronous generators**: through asynchronous generators you will be able to show multiple views according to the load state, for example transitions.&#x20;

{% embed url="https://github.com/atomicojs/router" %}

## Syntax

{% tabs %}
{% tab title="Atomico JSX" %}
```jsx
import { render } from "atomico";
import { RouterSwitch, RouterCase } from "@atomico/router";

render(
    <RouterSwitch>
        <RouterCase path="/" for="home"></RouterCase>
        <RouterCase path="/user/{id}" load={async function *()({id}){
            yield <h1>loading...</h1>;
            const data = await getUser(id);
            return <User {...data}/>
        }}></RouterCase>
        <h1 slot="config">home</h1>
    </RouterSwitch>,
    document.body
)jsx
```
{% endtab %}

{% tab title="HTML" %}
```html
<router-switch>
    <router-case path="/" for="home"></router-case>
    <router-case path="/config" for="config"></router-case>
    <section slot="home">...</section>
    <section slot="config">...</section>
</router-switch>
```
{% endtab %}
{% endtabs %}

## Elements

### RouterSwitch

Controller component of the routes, with it you can:

1. Observe the status of route transitions.
2. Observe the route in load&#x20;
3. Define the ::part selector to create custom path transitions.

#### Properties

| Props | Description                                          | Type               | Event |
| ----- | ---------------------------------------------------- | ------------------ | ----- |
| case  | slot to associate at the time of the match with path | String - read only | match |

#### Events

| Event | JSX     |                                                             |
| ----- | ------- | ----------------------------------------------------------- |
| Match | onMatch | It is dispatched every time the router matches a new route. |

### RouterCase

Component that declares the behavior of the route, with it you can:

1. Define a slot to show instantly when matching the browser path.
2. Define a load callback to execute when matching the browser route.

#### Properties

| Props   | Description                                                          | Type     |
| ------- | -------------------------------------------------------------------- | -------- |
| load    | asynchronous content loader                                          | Function |
| for     | slot to associate at the time of the match with path                 | String   |
| path    | expression for path                                                  | String   |
| memo    | memorize the state resolved by load according to the concurrent path | Boolean  |
| destroy | Remove associated view on route change                               | Boolean  |

## Examples

### Pokeapi

{% embed url="https://stackblitz.com/edit/atomico-router?embed=1&file=package.json&view=preview" %}
