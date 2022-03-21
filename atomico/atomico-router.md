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

1. Define a slot to show instantly when matching the browser path.
2. Define a load callback to execute when matching the browser route.

| Prop | Description                                          | Type     |
| ---- | ---------------------------------------------------- | -------- |
| load | asynchronous content loader                          | Function |
| for  | slot to associate at the time of the match with path | String   |
| path | expression for path                                  | String   |
