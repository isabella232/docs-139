# Store

## Constructor

```typescript
new Store(
    initialState,
    {
        actions,
        getters
    }
);
```

#### Where:

1. `initialState`: Object or function that defines the initial state
2. actions : Object that groups the actions of the state
3. getters : Object that creates virtual values of the state.

### actions

```tsx
async function *myAction(state, optionalParam){
    const stateUpdates = await logicAsync(optionalParam);
    return {
        ...(yield),
        ...stateUpdates
    }
}
```

### getters

getters are just functions that compute state.

```typescript
const total = (state)=>state.a + state.b;
```

## Store.on((state)=>void)

Subscribes to state changes, example:

```typescript
const off = store.on((state)=>{
    console.log(state.loading);
});

off(); // remove the subscription
```

## Store.clone( optionalNewState )

Clone the state and define a new state for it.
