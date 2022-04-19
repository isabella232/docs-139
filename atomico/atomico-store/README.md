---
description: >-
  @atomico/store a more predictable and natural model for asynchrony when
  controlling states.
---

# @atomico/store

{% embed url="https://github.com/atomicojs/store" %}

```typescript
interface State {
  api: string;
  loading: boolean;
  products: { id: number; title: string; price: number };
}

const initialState = (state: State) => ({
  api: "",
  loading: false,
  products: [],
});

async function* getProducts(state: State) {
  yield { ...state, loading: true };
  return {
    ...(yield),
    loading: false,
    products: await (await fetch(state.api)).json(),
  };
}

const store = new Store(initialState, {
  actions: { getProducts },
});
```

### Objectives

1. Asynchrony management.
2. Finitely predictable asynchrony.
3. Modularity and composition.

#### Asynchrony management

Application events and service calls are naturally asynchronous, with @atomico/store you can use asynchronous functions or asynchronous generators to define the update cycle.

**update cycle?** By this I mean the states that occur sequentially when dispatching the action, example:

```typescript
async function* getProducts(state: State) {
  yield { ...state, loading: true };
  return {
    ...(yield),
    loading: false,
    products: await (await fetch(state.api)).json(),
  };
}
```

The previous action will generate 2 states when dispatched:

1. state 1:`{loading: true, products:[]}`
2. state 2: `{loading: false, products:[...product]}`

The advantage of this is that the process is clearly observable by the store and by whoever dispatches the action.

#### Finitely predictable asynchrony

Every action in @atomico/store is wrapped in a promise that defines when it ends its cycle, this will let you execute actions sequentially, example:

```typescript
await store.actions.orderyBy();
await store.actions.insert({ id: 1000 });
await store.actions.updateAll();
```

#### Modularity and composition

@atomico/store allows to decouple the actions and the state of the store, for a better modularization , example:



{% tabs %}
{% tab title="actions.js" %}
```typescript
export interface State {
  api: string;
  loading: boolean;
  products: { id: number; title: string; price: number };
}

export const initialState = (state: State) => ({
  api: "",
  loading: false,
  products: [],
});

export async function* getProducts(state: State) {
  yield { ...state, loading: true };
  return {
    ...(yield),
    loading: false,
    products: await (await fetch(state.api)).json(),
  };
}
```
{% endtab %}

{% tab title="store.js" %}
```typescript
import * as Actions from "./actions";

export default new Store(Actions.initialStore, { actions: { Actions } });
```
{% endtab %}
{% endtabs %}

### Api

{% content-ref url="hooks.md" %}
[hooks.md](hooks.md)
{% endcontent-ref %}
