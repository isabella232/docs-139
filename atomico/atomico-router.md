---
description: powerful router for webcomponents
---

# @atomico/router

{% tabs %}
{% tab title="Atomico JSX" %}
```jsx
import { render } from "atomico";
import { RouterSwitch, RouterCase } from "@atomico/router";

render(
    <RouterSwitch>
        <RouterCase path="/" for="home"></RouterCase>
        <RouterCase path="/user/{id}" load={async ({id})=>{
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

### RouterSwitch

Controller component of the routes, with it you can:

1. Observe the status of route transitions.
2. Observe the route in load&#x20;
3. Define the ::part selector to create custom path transitions.

#### Properties

| Props   | Description                                                                                                                          | Type               | Event   |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------ | ------- |
| loading | is defined in case RouterCase defines the load function,  the value of loading will be the route that is being loaded asynchronously | String - read only | loading |
| case    | slot to associate at the time of the match with path                                                                                 | String - read only | match   |

#### Custom properties

| Prop                     | Type                                            |
| ------------------------ | ----------------------------------------------- |
| --router-transition-wait | transition before the entry of the state **in** |
| --router-opacity-wait    | opacity before the entry of the state **in**    |
| --router-transform-wait  | transform before the entry of the state **in**  |
| --router-transition-in   |                                                 |
| --router-opacity-in      |                                                 |
| --router-transform-in    |                                                 |
| --router-transition-out  |                                                 |
| --router-opacity-out     |                                                 |
| --router-transform-out   |                                                 |

#### Transition example

```css
:root{
    --router-transition-wait: 0.5s ease all;
    --router-transition-out: 0.5s ease all;
    --router-transition-in: 0.5s ease all;
    --router-transform-wait: scale(0.5) translateX(50%);
    --router-transform-in: translateY(0%);
    --router-transform-out: scale(0.5) translateX(-50%);
    --router-opacity-wait: 1;
    --router-opacity-out: 1;
}
```

{% embed url="https://stackblitz.com/edit/atomico-router-transition-76khvu?embed=1&hideExplorer=1&view=preview" %}

### RouterCase

Component that declares the behavior of the route, with it you can:

1. Define a slot to show instantly when matching the browser path.
2. Define a load callback to execute when matching the browser route.

#### Properties

| Props | Description                                                          | Type     |
| ----- | -------------------------------------------------------------------- | -------- |
| load  | asynchronous content loader                                          | Function |
| for   | slot to associate at the time of the match with path                 | String   |
| path  | expression for path                                                  | String   |
| memo  | memorize the state resolved by load according to the concurrent path | Boolean  |

### Examples

1. [https://stackblitz.com/edit/atomico-router-for](https://stackblitz.com/edit/atomico-router-for)
2. [https://stackblitz.com/edit/atomico-router-load](https://stackblitz.com/edit/atomico-router-load)
3. [https://stackblitz.com/edit/atomico-router-transition](https://stackblitz.com/edit/atomico-router-transition)
