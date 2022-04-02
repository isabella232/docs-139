---
description: receives the submits from MagicForm
---

# MagicFormProvider | \<magic-form-provider>

### **Example**

```tsx
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

### **Events**

| Type            | Description                                 | Config                              |
| --------------- | ------------------------------------------- | ----------------------------------- |
| `"ChangeForms"` | Dispatched when forms changes from provider | `{bubbles: false, composed: false}` |

### **Properties**

| Property | Description                                                               |
| -------- | ------------------------------------------------------------------------- |
| `forms`  | Read only, current state of the captured forms                            |
| actions  | object that defines the actions to be captured by the `MagicFormProvider` |

##
