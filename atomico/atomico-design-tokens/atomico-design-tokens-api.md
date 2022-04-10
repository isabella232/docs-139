# @atomico/design-tokens api

## compose

create a pipeline of functions that share the same CSSStyleSheet.

### Syntax

```typescript
compose(
    ...middleware: ((sheet: CSSStyleSheet, lastParam:any)=> any)[]
): (firstParam:any)=>sheet: CSSStyleSheet;
```

## tokens

transforma un objeto a custom properties.

### Syntax

```typescript
tokens(theme: Tokens, prefix: string);
```

### Example

{% tabs %}
{% tab title="Input" %}
```typescript
compose(
    tokens(
        {
            size: {
                xl: "32px",
                l: "28px",
                m: "24px",
            }
        },
        "ds"
    )
);
```
{% endtab %}

{% tab title="css mutations" %}
```css
:host{
    --size-xl: var( --ds--size-xl,  32px);
    --size-l: var( --ds--size-xl,  28px);
    --size-m: var( --ds--size-xl,  24px);
}
```
{% endtab %}
{% endtabs %}

