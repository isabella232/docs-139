# use-intersection-observer

Create an **IntersectionObserver** instance to observe the intersection of the webcomponent or a reference.

Remember that to detect any intercept, a minimum height and width of the reference to be observed is required.

### useIntersectionObserver

```javascript
import { useIntersectionObserver } from "@atomico/hooks/use-intersection-observer";

function component(){
    useIntersectionObserver(([entry])=>{
        console.log("",{isIntersecting })
    },{
          threshold: 0.1,
    })
    return <host shadowDom/>
}

component.styles = css`
    :host{
        display: block;
        width: 100%;
        min-height: 1px;
    }
`
```

### useRefIntersectionObserver

```javascript
import { useHost } from "atomico";
import { useRefIntersectionObserver } from "@atomico/hooks/use-intersection-observer";

function component(){
    const host = useHost();
    useRefIntersectionObserver(
        ref,
        ([entry])=>{
            console.log("",{isIntersecting })
        },{
          threshold: 0.1,
        }
    );
    return <host shadowDom/>
}

component.styles = css`
    :host{
        display: block;
        width: 100%;
        min-height: 1px;
    }
`
```



