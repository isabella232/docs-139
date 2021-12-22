---
description: >-
  Improves the form development experience thanks to the use of webcomponents to
  centralize submission
---

# @atomico/magic-form

## Installation and import

{% tabs %}
{% tab title="Instalation" %}
```
npm install @atomico/magic-form
```
{% endtab %}

{% tab title="Module webcomponents" %}
```javascript
import { 
    MagicForm,
    MagicFormProvider 
} from "@atomico/magic-form";
```
{% endtab %}

{% tab title="Module hooks" %}
```javascript
import { 
    useMagicForm, 
    useMagicFormProvider 
} from "@atomico/magic-form/hooks";
```
{% endtab %}
{% endtabs %}

## Webcomponent

{% tabs %}
{% tab title="HTML" %}
```html
<magic-form-provider>
  <magic-form>
    <form action="user">
      <input type="text" name="name" />
      <input type="text" name="email" />
      <button>Create user</button>
    </form>
  </magic-form>
</magic-form-provider>
<script>
  document.querySelector("magic-form-provider").actions = {
    async add(form) {
      return fetch("./my-api", {
        method: "post",
        body: new FormData(form),
      }).then((res) => res.json());
    },
  };
</script>
```
{% endtab %}

{% tab title="JSX Atomico" %}
```jsx
import { MagicForm, MagicFormProvider } from "@atomico/magic-form";

function component() {
  return (
    <host>
      <MagicFormProvider 
        actions={{
          async add(form) {
            return fetch("./my-api", {
              method: "post",
              body: new FormData(form),
            }).then((res) => res.json());
          },
        }}
      >
        <MagicForm>
          <form action="user">
            <input type="text" name="name" />
            <input type="text" name="email" />
            <button>Create user</button>
          </form>
        </MagicForm>
      </MagicFormProvider>
    </host>
  );
}x
```
{% endtab %}
{% endtabs %}

`magic-form-provider` captures all the forms nested in `magic-form` when executing the submit event by the form and distributes them according to the definition of the action attribute to each method of the actions object

### \<magic-form> | MagicForm

captures the submit event of the nested form and sends it to `MagicFormProvider`

```html
<magic-form>
  <form action="user">
    <input type="text" name="name" />
    <input type="text" name="email" />
    <button>Create user</button>
  </form>
</magic-form>
```

**Events**

| Type            | Description                                  | Config                              |
| --------------- | -------------------------------------------- | ----------------------------------- |
| `"ChangeState"` | Dispatched when status changes from provider | `{bubbles: false, composed: false}` |

**Properties**

| Property | Description                                                                                  |
| -------- | -------------------------------------------------------------------------------------------- |
| `state`  | Read only, Current status submission of the form                                             |
| `action` | <p>Defines the action to dispatch, if not defined it can be inherited from the</p><p>tag</p> |



## Hooks for Atomico

### useMagicForm

catch the submit event and send it to the `useMagicFormProvider`

```jsx
import { useRef } from "atomico";
import { useMagicForm } from "@atomico/magic-form/hooks";

function component() {
  const ref = useRef();
  const [state, submit] = useMagicForm(ref);
  return (
    <host>
      <form ref={ref} action="addUser">
        <input type="text" name="name" />
        <input type="email" name="email" />
        <button>Add user</button>
      </form>
    </host>
  );
}
```

### useMagicFormProvider

receives the submits from `useMagicForm`

```jsx
import { useHost } from "atomico";
import { useMagicFormProvider } from "@atomico/magic-form/hooks";

function component() {
  const ref = useHost();
  const forms = useMagicFormProvider(ref, {
    addUser(form) {
      const body = new FormData(form);
      return fetch(formData, { method: "POST", body }).res((res) => res.json());
    },
  });
  return <host></host>;
}
```
