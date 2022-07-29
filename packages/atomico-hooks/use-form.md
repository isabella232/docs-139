---
description: Communicate the component with external forms.
---

# use-form

### Module

```javascript
import { 
    useForm, 
    useFormListener, 
    useFormInputHidden, 
    useFormInputRadio 
} from "@atomico/hooks/use-form";
```

### useForm syntax

**If the webcomponent is nested within a form** **tag**, this hook will return that form tag as a reference.

```javascript
const ref = useForm()
```

### useFormListener syntax

**If the webcomponent is nested within a form tag**, you will be able to listen to events from that tag through useFormListener.

```javascript
useFormListener("reset",handler);
```

### useFormInputHidden syntax

el hook renderiza un input hidden en el lightDOM cuyo name y value del input seran los parametros que el hook resiva

```javascript
useFormInputHidden("my-field","my-value");
```

### useFormInputRadio

One of the difficult inputs to standardize when working with shadowDOM is the radio input, thanks to this hook you will be able to create and observe a radio input synchronized with the form and its webcomponent.&#x20;

**This hook requires the definition of the properties in its webcomponent:**

```javascript
myComponent.props = { name: String, checked: Boolean }
```

You can work with the input from the component logic, example:

```jsx
const refInput = useFormInputRadio(<input slot="input" value="my-value"/>);

return <host>
    <slot name="input"/>
</host>;
```

Your component will automatically be reactive to the change of the states of the radio input

### Example&#x20;

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/NuVzTC7iXlKSxhl112pJ/src/index.jsx" %}

