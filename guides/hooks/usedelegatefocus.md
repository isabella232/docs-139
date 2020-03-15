---
description: >-
  It allows delegating the focus action generated on the web-component to a
  reference
---

# useDelegateFocus

### Usage

```jsx
 const ref = useRef();
 useDelegateFocus(ref);
 
 return <host>
   <button>...</button>
   <input ref={ref}/>
 </host>
```

Any focus action on the web-component will redirect the effect on the ref, eg [https://webcomponents.dev/edit/vMBJSomCc0PWfhrpeJ5m](https://webcomponents.dev/edit/vMBJSomCc0PWfhrpeJ5m)

