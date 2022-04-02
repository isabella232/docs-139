---
description: receives the submits from MagicForm
---

# MagicFormProvider | \<magic-form-provider>

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
