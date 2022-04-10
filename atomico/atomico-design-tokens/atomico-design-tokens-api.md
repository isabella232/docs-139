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

transform an object to custom properties.

### Syntax

```typescript
tokens(theme: Tokens, prefix: string);
```

### Example 1

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

### Example 2, variations

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
            },
            variation: {
                small: {
                    size: {
                        xl: "28px",
                        l: "24px",
                        m: "20px",
                    },                
                }
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
:host([small]){
    --size-xl: var( --ds-small--size-xl,  28px);
    --size-l: var( --ds-small--size-xl,  24px);
    --size-m: var( --ds-small--size-xl,  20px);
}
```
{% endtab %}
{% endtabs %}

###

