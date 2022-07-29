# Hooks

The useStore hooks for atomico follow an island model where the useStore tries to inherit a parent useStore when synchronizing with the webcomponent, this leaves 2 possibilities:

\
1\. If useStore does not find a superior useStore it will use the assigned one as a parameter.

2\. If useStore finds a superior useStore it will use that store for its synchronization.

this allows your application to respond to an instance-based configuration context.

## useStore

### Provider

Using the second parameter on useStore will generate a copy that defines the context of use and inheritance for the nested webcomponents.

```jsx
const store = useStore(Store, initialState);
```

### Consumer

Consumes the store either by assignment or inheritance

```typescript
const store = useStore(Store);
```

## useActionObserver

In @atomico/store every action is finite, this means that the store knows when the execution of an action is finished, useActionObserver lets you observe that, example:

```typescript
const [ requestData, status ] = useActionObserver(store.actions.requestData);

useEffect(requestData,[]);

console.log(status)// 1. "", 2. "pending", 3. "fulfilled"
```

Where:

1. `requestData`: function that dispatches the action.
2. `status`: `"" | "pending" | "fulfilled" | "rejected"` dispatched action status.

``



## useActionFromForm

It subscribes to the submit of a form in order to dispatch the action, giving the action the instance of the form tag as a parameter.

```tsx
const [status, submit] = useActionFromForm(refForm, store.action.send);
```

Where:

1. `store.action.send`: action to dispatch
2. `status`: `"" | "pending" | "fulfilled" | "rejected"` dispatched action status.
3. `submit`: callback to manually execute the action
