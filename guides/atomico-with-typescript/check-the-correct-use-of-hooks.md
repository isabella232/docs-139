---
description: >-
  By default most hooks infer types automatically, however here are some typing
  tips:
---

# Check the correct use of hooks

## useState

useState infers the type according to its initial state, if you don't define that state you can define the type manually, example:

```ts
const [message, setMessage] = useProp<string>();
```

The above statement will define that:

1. `message` is of type `string`.
2. `setMessage` only accepts values of type `string` or functions that return a `string`.

## useProp

useProp will not infer the type from the prop, you must define it, example:

```ts
const [message, setMessage] = useProp<string>("message");
```

Let's remember that useProp has a return api similar to useState, so the previous declaration will define that:

1. `message` is of type `string`.
2. `setMessage` only accepts values of type `string` or functions that return a `string`.

## useMemo and useCallback

both useMemo vs useCallback infer its type based on the callback that builds the memo state, but for certain conditions you may need to force the type return, example:

```ts
const message = useMemo<string>(() => "i'am atomico!");
```

Although useMemo infers that its type is string, you can change the return rules via the first type parameter.

The above statement will define that:

1. `message` is of type `string`.

> This applies equally to useCallback.

## useEvent

useEvent allows defining the detail structure through the type parameter, example:

```ts
const dispatch = useEvent<{ id: string }>("MyCustomEvent", { bubbles: true });

dispatch({ id: string });
```

The above statement will define that:

1. The dispatch callback expects an object of type `{id: string}` as a parameter.

## useRef

useRef allows to define through the type parameter the expected value of current in the reference.

```ts
const refForm = useRef<HTMLFormElement>();
```

The above statement defines:

1. `refForm?.current` is of the type `HTMLFormElement`.

## useHost

useHost defines that current always exists, so the optional selector is not necessary, the type parameter of useHost allows to define the source Element, example:

```ts
const host = useHost<HTMLElement>();
```

All hooks in Atomico have Type declarations, explore them when importing each hook as a documentation source.
