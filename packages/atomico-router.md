---
description: powerful router for Webcomponents, React and Preact
---

# @atomico/router

@atomico/router tiene como objetivo facilitar la creacion de aplicaciones tipo SPA a travez de las siguientes estrategias:

1. &#x20;slot: usted podra referenciar un slot dentro  de RouterSwitch a mostrar en un path especifico.&#x20;
2. elementos: usted podra montar CustomElements a travez de elementos Instanciables.
3. generadores asincronos: a través de generadores asíncronos usted lograra mostrar múltiples vistas según el estado de carga, por ejemplo transiciones.&#x20;

{% embed url="https://github.com/atomicojs/router" %}

## Sintaxis

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

## Elementos

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
