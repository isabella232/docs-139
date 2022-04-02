---
description: MagicForm api is equivalent in Atomicojs, React and Preact at JSX level
---

# MagicForm in React and Preact

### Installation

```bash
npm i @atomico/magic-form @atomico/react
```

### Usage

{% tabs %}
{% tab title="React" %}
```tsx
import { MagicForm, MagicFormProvider } from "@atomico/magic-form/react";

export function App() {
  return (
    <>
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
    </>
  );
}

```
{% endtab %}

{% tab title="Preact" %}
```tsx
import { MagicForm, MagicFormProvider } from "@atomico/magic-form/preact";

export function App() {
  return (
    <>
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
    </>
  );
}

```
{% endtab %}
{% endtabs %}
