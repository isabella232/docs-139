---
description: Improve the interaction with the forms and accessibility of your components.
---

# Forms and shadowDOM

It is normal that we use the technique of dispatching events from the component to communicate states and more, but when using forms this changes since the events inside the shadowDOM do not interact with the form outside of it, example:

```markup
<form>
    <my-input>
        #shador-root
            <input/>
    </my-input>
</form>
```

To solve this we will have to nest an input tag in the lightDOM of our component, in order to reflect the logic of this to the form. Atomico facilitates this hybrid interaction between lightDOM and shadowDOM with the [**@atomico/hooks/use-render**](../atomico/atomico-hooks/use-render.md) hook that allows executing a second render that works from the lightDOM, example:

```jsx
import { useRender } from "@atomico/hooks/use-render";

function myInput(){
    // render LightDOM
    useRender(()=><input/>);
    
    // render ShadowDOM
    return <host shadowDom>
        <slot/>
    </host>
}
```

With this you have gained full control over the existing input tag in the lightDOM, allowing you to apply styles using the `::slotted` selector, example:

```javascript
myInput.styles = css`
    :slotted(input){
        border: 1px solid black;
        height: 40px;
    }
`;
```

We have created an input tag that allows you to interact directly with the form, this technique is applicable with all the tags that interact with the form, such as button, input, textarea and others.
