# useState

### Syntax

```javascript
const [state, setState] = useState(optionalInitialState);
```

Where:

1. `const [state,setState]` : Return of `useState`, the arguments allow reading and updating of the state associated with the hook instance.
   - `state` : Current state.
   - `setState`: Current status updater.
2. `useState( optionalInitialState )`: Function that associates the state to the webcomponent:
   - `optionalInitialState`: Optional parameter that defines the initial state associated to the hook instance, **If `optionalInitialState` is a function it will be executed in order to obtain the initial state only at the moment of the hook instance for the first time**.

#### Example

```jsx
function MyComponent() {
  const [count, setCount] = useState(0);
  return <host onclick={() => setCount(count + 1)}> {count} </host>;
}
```
