---
description: captures the submit event of the nested form and sends it to MagicFormProvider
---

# MagicForm | \<magic-form>

### E**xamples**

{% tabs %}
{% tab title="Default" %}
```tsx
<MagicForm>
  <form action="user">
    <input type="text" name="name" />
    <input type="text" name="email" />
    <button>Create user</button>
  </form>
</MagicForm>
```
{% endtab %}

{% tab title="onChangeState" %}
```tsx
<MagicForm onChangeState={event=>{
  console.log(event.currentTarget.state);
}}>
  <form action="user">
    <input type="text" name="name" />
    <input type="text" name="email" />
    <button>Create user</button>
  </form>
</MagicForm>
```
{% endtab %}
{% endtabs %}

### **Events**

| Type            | Description                                  | Config                              |
| --------------- | -------------------------------------------- | ----------------------------------- |
| `"ChangeState"` | Dispatched when status changes from provider | `{bubbles: false, composed: false}` |

### **Properties**

| Property | Description                                                                                  | Type   |
| -------- | -------------------------------------------------------------------------------------------- | ------ |
| `state`  | Read only, Current status submission of the form                                             | Object |
| `action` | <p>Defines the action to dispatch, if not defined it can be inherited from the</p><p>tag</p> | String |

#### Property.state

```tsx
interface MagicFormActionStatus{
    result?:any,
    timestamp?: number,
    status: "pending" | "fulfilled" | "rejected"
}
```
