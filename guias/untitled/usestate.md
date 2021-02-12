# useState

### Sintaxis

```javascript
const [state, setState] = useState(optionalInitialState);
```

Donde:

1. `const [state,setState]` : Retorno de `useState`, los argumentos permiten lectura y actualización del estado asociado a la instancia del hook.
   * `state` :  estado actual
   * `setState`: actualizador del estado.
2. `useState( optionalInitialState )`: Función que asocia el estado al webcomponent:
   * `optionalInitialState`: Parámetro opcional que define el estado inicia asociado a la instancia del hook, **Si `optionalInitialState` es una función se ejecutara para así obtener el estado inicial solo al momento de instancia el hook por primera vez**

#### Ejemplo

```jsx
function MyComponent() {
  const [count, setCount] = useState(0);
  return <host onclick={() => setCount(count + 1)}> {count} </host>;
}
```

