---
description: >-
  Improves the form development experience thanks to the use of webcomponents to
  centralize submission
---

# @atomico/magic-form

{% embed url="https://github.com/atomicojs/magic-form" %}

A powerful form submission manager created with Atomicojs webcomponents, with MagicForm you can:

1. Simplify the sending of forms by centralizing the sending actions through a provider.
2. Know at all times the forms that are being provided and show their status.
3. Isolate a group of actions according to provider, this means that if a provider does not register the action it will bubble to the parent provider.

### Installation and import

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

### Usage

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
}
```
{% endtab %}
{% endtabs %}

`magic-form-provider` captures all the forms nested in `magic-form` when executing the submit event by the form and distributes them according to the definition of the action attribute to each method of the actions object

### \<magic-form> | MagicForm

captures the submit event of the nested form and sends it to `MagicFormProvider`

**Events**

| Type            | Description                                  | Config                              |
| --------------- | -------------------------------------------- | ----------------------------------- |
| `"ChangeState"` | Dispatched when status changes from provider | `{bubbles: false, composed: false}` |

**Properties**

| Property | Description                                                                                  |
| -------- | -------------------------------------------------------------------------------------------- |
| `state`  | Read only, Current status submission of the form                                             |
| `action` | <p>Defines the action to dispatch, if not defined it can be inherited from the</p><p>tag</p> |

### \<magic-form-provider> | MagicFormProvider

receives the submits from `MagicForm`

**Events**

| Type            | Description                                 | Config                              |
| --------------- | ------------------------------------------- | ----------------------------------- |
| `"ChangeForms"` | Dispatched when forms changes from provider | `{bubbles: false, composed: false}` |

**Properties**

| Property | Description                                                               |
| -------- | ------------------------------------------------------------------------- |
| `forms`  | Read only, current state of the captured forms                            |
| actions  | object that defines the actions to be captured by the `MagicFormProvider` |

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
