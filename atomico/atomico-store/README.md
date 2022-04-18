---
description: >-
  @atomico/store a more predictable and natural model for asynchrony when
  controlling states.
---

# @atomico/store

{% embed url="https://github.com/atomicojs/store" %}

### The problem with the traditional approach

Normally the libraries solve the asynchrony through the observable pattern, applying it through a setter or a function that communicates the change to the subscribers, although this is valid, the following question arises, **when does the asynchrony end?**

Let's analyze for example Pinia a store for Vuejs.

```javascript
defineStore("main", {
  state: () => ({
    counter: 0,
  }),
  actions: {
    incrementAsync() {
      setTimeout(() => {jav
        this.counter++;
      }, 100);
    },
  },
});
```

The disadvantages of the above code are:

1. the execution of `incrementAsync` does not have a closure of the execution cycle, since the setTimeout is an unknown execution for the observable and its effect only occurs when setting the `this.counter` property, problem: _"we do not know when that action ends"_.
2. There is no sequence of execution, we could add asynchronous effects inside `myAction` regardless of the order of these. problem: _"a big noodle soup"_.

### A more predictable and natural approach

`@atomico/store` seeks to facilitate async by defining the following goals:

1. [Asynchrony management](./#asynchrony-management).
2. [Finitely predictable asynchrony](./#finitely-predictable-asynchrony.).
3. Modularity and composition.

In this article we will only know how `@atomico/store` solves point 1 and 2.

#### The Store

`@atomico/store` implements 3 classic concepts of a store:

1. `state`: observed and referential state for actions and getters.
2. `actions`: only way to modify the state.
3. `getters`: Virtual values from the state.

### Example

```javascript
import { Store } from "@atomico/store";

export default new Store(
  // initial state
  {
    loading: false,
    products: [],
  },
  {
    actions: {
      async *fetch(state) {
        yield {
          ...state,
          loading: true,
        };

        const products = await getProducts("my-products");

        return {
          ...(yield),
          loading: false,
          products,
        };
      },
    },
  }
);
```

#### Asynchrony management

Let's go back to the previous example and rescue the following block of code:

```javascript
async *fetch(state) {
  yield {
    ...state,
    loading: true,
  };

  const products = await getProducts("my-products");

  return {
    ...(yield),
    loading: false,
    products,
  };
}
```

The execution of the action fetch performs the following steps:

1. `return 1`: defines the loading property..
2. `waiting`: recupera los productos mediante `await getProducts("products")`.
3. `final return`: defines a new state without breaking parallelism thanks to `...(yield)`.

#### Finitely predictable asynchrony.

Each execution of an action returns a promise, thanks to the use of asynchronous generators we can determine when our action ends the cycle, example:

```javascript
import Store from "./my-store";

Store.action.on(({ loading }) => {
  console.log(loading); // 1️⃣ first `true`, 2️⃣ then `false`
});

Store.actions.fetch().then(({ products }) => {
  console.log(products); // DONE!
});
```

### Api

{% content-ref url="hooks.md" %}
[hooks.md](hooks.md)
{% endcontent-ref %}
