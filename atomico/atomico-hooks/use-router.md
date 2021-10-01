---
description: Hooks to work with routes in the browser
---

# use-router

Hook to handle routes based on expressions according to the [**https://github.com/uppercod/exp-route**](https://github.com/uppercod/exp-route)  library, this hook is used by [**@atomico/components/router**](https://app.gitbook.com/@atomico/s/doc/~/drafts/-MkwI-GZFi_DQoa0Epyp/atomico/atomico-components/router)\*\*\*\*

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
const view = useRouter({
    "/":()=><h1>home</h1>,
    "user/{id}":({ id })=><my-user id={id}/>,
})
```

### useRoute syntax

```jsx
const view = useRoute("/",()=><h1>home</h1>);
```

### useRouteMatch syntax

```jsx
const match = useRouteMatch();

const isHome = match("/home");
```

