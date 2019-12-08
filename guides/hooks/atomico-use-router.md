---
description: "Small and simple router to manage web-components, based on popstate and\_\_ hooks"
---

# atomico/use-router



Before starting to read the hooks, I recommend understanding the expression pattern created for use-route

| Patrón | Descripción |
| :--- | :--- |
| `/folder` | Required and exact match |
| `/:id` | Required parameter, capture the folder and associate the capture with the id property |
| `/:id?` | Optional parameter, capture the folder and associate the capture with the id property |
| `/:id...` | Optional spread parameter, capture everything the folder follows and associate the capture with the id property |
| /\* | Required, allows not to define in writing the name of the folder |

### useRoute

```javascript
let [inRoute, params] = useRoute("/my-route");
```

It allows to observe the state of a route, where:

* `"/my-route"` : String, route pattern to subscribe to the router.
* `inRoute` : Boolean, define if the route matches
* `params`: Object that stores the parameters captured by the router.

### useRouter

```javascript
let paths = {
    "/": ()=>"in root",
    "/:id": ({id})=><User id={id}/>,
    "default": ()=>"404"
};
let View = useRouter(paths);
```

It allows to observe the state of one or more routes through an object, where:

* `paths` : Routes to be observed by a Router, if it coincides with an index of the object, the value of the index will be executed or used
* `View` : return of paths depending on the route.

### useRedirect

```javascript
let redirect = useRedirect(optionalPath)
```

It allows to redirect the route, where:

* `optionalPath` : Optional String, if defined redirect points only to the optionalPath path.
* `redirect` : Optional String, if defined, will only be redirected to the optional Path

