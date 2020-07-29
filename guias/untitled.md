---
description: >-
  Al igual que los componentes de interfaces permiten reutilizar UI los hooks
  permite reutilizar procesos logicos, ejemplo ejecutar actualizaciones
  asíncronas, comunicar efectos y controlar estados solo
---

# Hooks

## Hooks exclusivos para webcomponents

### useProp

Hook que permite reflejar los cambios de estado sobre una propiedad desde el interior del wecomponent.

```text
const [value, setValue] = useProp(propName);
```

Donde :

1. `const [value, setValue]`: Retorno de `useProp`, los argumentos permiten la lectura y actualización del estado asociad a la propiedad `propName` del webcomponent.
2. `propName` :  String que define la propiedad a usar por `useProp` del  webcomponent.

#### Ejemplo

```jsx
const MyComponent = () => {
  const [count, setCount] = useProp("count");
  return (
    <host>
      <button onclick={() => setCount(count + 1)}>+</button>
      <span>{count}</span>
    </host>
  );
};

MyComponent.props = { count: { type: Number, value: 0 } };
```

### useEvent

Hook que permite emitir un evento desde el webcomponent.

```javascript
const dispatchEvent = useEvent(myEvent, optionalEventInit);
```

Donde :

1. `dispatchEvent` : Función que despacha el evento definido por `myEvent`.
2. `myEvent` : String que define el evento a despachar por `useEvent`
3. `optionalEventInit` : Configuración del  evento a despachar, `{bubbles?: boolean, cancelable?: boolean, composed?: boolean, detail?: any}`. [https://developer.mozilla.org/en-US/docs/Web/API/Event/Event](https://developer.mozilla.org/en-US/docs/Web/API/Event/Event)

### useRef

Hook que crea una referencia en la que current es la instancia del webcomponent.

```javascript
const refHost = useHost();
```

 **Este hooks es util para añadir funcionalidades asociadas a la isntancia del webcomponent**

## Hooks homologados de React

### useState

Hook que permite crear un estado sobre el webcomponent.

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

### useEffect

Hook que permite asociar efectos al webcomponent.

```javascript
useEffect(effectCallback, optionalArgumentList);
```

Donde :

1. `effectCallback` : Función que se ejecuta una o mas veces según `optionalArgumentList`, `effectCallback`  puede retornar una función que será ejecutada solo si ```effectCallback`` \` es nuevamente ejecutado o el wecomponents es desmontado.
2. `optionalArgumentList`: Array de argumentos a observar por `useEffect`, si uno de estos argumentos cambia entre renderizaciones `effectCallback` será ejecutado nuevamente. Si `optionalArgumentList` se define como una array vacío\(`[]`\),  useEffect solo ejecutara `effectCallback`  al crear el webcomponent .

#### Ejemplo

```javascript
const listenerClickWindow = () => {
  const handlerClick = () => {
    console.log("Click window!");
  };

  window.addEventListener("click", handlerClick);

  const unlistenerClickWindow = () =>
    window.removeEventListener("click", handlerClick);

  return unlistenerClickWindow;
};
useEffect(listenerClickWindow, []);
```

### useMemo

Hook que permite memorizar el retorno de un callback.

```javascript
const memoValue = useMemo(callback, optionalArgumentList);
```

Donde :

1. `memoValue` : Retorno memorizado por useMemo 
2. `callback`:  Función que se ejecuta una o mas veces según `optionalArgumentList`.
3. `optionalArgumentList`: Array de argumentos a observar por `useEffect`, si uno de estos argumentos cambia entre renderizaciones `useEffect` ejecutara nuevamente el `callback`, memorizando un nuevo retorno.

### useCallback

Hook que permite memorizar un callback para que este conserve su scope.

```javascript
const memoCallback = useCallack(callback, optionalArgumentList);
```

Donde:

1. `memoCallback` : Retorno memorizado por useCallback.

