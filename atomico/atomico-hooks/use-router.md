---
description: Hooks to work with routes in the browser
---

# use-router

Hook to handle routes based on expressions according to the [**https://github.com/uppercod/exp-route**](https://github.com/uppercod/exp-route) library, this hook is used by [**@atomico/components/router**](../atomico-components/router.md)\*\*\*\*

### Module

```javascript
import { 
    useRouter, 
    useRoute, 
    useRouteMatch, 
    useRedirect, 
    redirect, 
    getPath 
} from "@atomico/hooks/use-router";
```

### useRouter syntax

```jsx
const [ view, path, params, search ] = useRouter({
    "/":()=><h1>home</h1>,
    "user/{id}":({ id })=><my-user id={id}/>,
})
```

Where:

1. `view`: return of the last function executed according to the route match.
2. `path`: string, represents the prop of the last path that consists of the path match.
3. `params`: parameters captured according to the path
4. `search`: parameters captured from the path

### useRoute syntax

```jsx
const [ view, path, params, search ] = useRoute("/",()=><h1>home</h1>);
```

Share the return from useRouter

### useRouteMatch syntax

```jsx
const match = useRouteMatch();

const isHome = match("/home");
```
