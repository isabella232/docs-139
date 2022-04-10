# @atomico/design-tokens api

### compose

create a pipeline of functions that share the same CSSStyleSheet.

```typescript
compose(
    ...middleware: ((sheet: CSSStyleSheet, lastParam:any)=> any)[]
): (firstParam:any)=>sheet: CSSStyleSheet;
```
