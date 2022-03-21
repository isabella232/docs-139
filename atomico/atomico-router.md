---
description: powerful router for webcomponents
---

# @atomico/router

![](../.gitbook/assets/atomico-router.svg)

```tsx
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
)
```

### RouterSwitch

Controller component of the routes, with it you can:

1. Observe the status of route transitions.
2. Observe the route in load&#x20;
3. Define the ::part selector to create custom path transitions.



### RouterCase

Component that declares the behavior of the route, with it you can:

1. definir un slot al momento al hacer match con la ruta del browser.
2. definir un callback load para cargar el contenido de la ruta al hacer match con la ruta del browser

| Prop | Description                                   | Type     |
| ---- | --------------------------------------------- | -------- |
| load | cargador asíncrono del contenido              | Function |
| for  | slot a asociar al momento  del match con path | String   |
| path | expresión para la ruta                        | String   |
