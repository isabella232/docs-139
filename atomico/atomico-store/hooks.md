# Hooks

### useStore

You subscribe to a store directly.

```jsx
useStore(store);
```

### useStoreProvider

Define a Store to share with nested useStoreConsumers.

```jsx
useStoreProvider(store, id?: string | symbol);
```

Where:

1. `store`: Store instance.
2. `id`: Optional parameter, defines an ID for the Store, this allows that in the ascending search of `useStoreConsumer` the store is defined according to the equality of the ID

### useStoreConsumer

Find and consume a store.

```ts
const store = useStoreConsumer(id?: string | symbol);
```

Where:

1. `id`: Optional parameter, identifier of the store defined by `useStoreProvider`

### useActionObserver

When every action is executed, it creates a promise. This hook allows you to observe the state of the promise when it is dispatched.

```ts
const [myAction, status, result] = useActionObserver(store.actions.myAction);
```

Where:

1. `myAction`: function that dispatches the action.
2. `status`: `"" | "pending" | "fulfilled" | "rejected"` dispatched action status.
3. `result`: return of dispatched action

