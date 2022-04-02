# MagicForm Hooks

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

