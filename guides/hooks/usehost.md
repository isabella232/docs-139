---
description: >-
  It allows obtaining a reference to the host without the need to associate with
  reference
---

# useHost

### Syntax

```jsx
const host = useHost();

console.log(host.current) // <web-component/>
```

### Usage

Improve the custom-hooks experience for web-components, since it allows direct access to the host, eg:

```jsx
 function useProp(name) {
    let ref = useHost();
    if (name in ref.current) {
        if (!ref[name]) {
            ref[name] = [null, nextValue => (ref.current[name] = nextValue)];
        }
        ref[name][0] = ref.current[name];
        return ref[name];
    }
}
```

