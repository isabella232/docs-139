# @atomico/design-tokens api

## module

```javascript
import {
    compose,
    tokens,
    classes
} from "@atomico/design-tokens";
```

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

## classes

It facilitates the reuse of tokens, through the generation of dynamic classes.

### Syntax

```typescript
classes(tokens:Tokens);
```

### Example

{% tabs %}
{% tab title="Input" %}
```javascript
import {css} from "atomico";
import { compose, classes } from "@atomico/design-tokens";

const designTokens = compose(
    classes(
        {
            size: {
                xl: "32px",
                l: "28px",
                m: "24px",
            }
        }
    )
);

export const classUtils = designTokens(
    css`
        .gap.--size{
            gap: var(--size);
        }
    `
);
```
{% endtab %}

{% tab title="CSS mutations" %}
```css
.gap\.xl{    
    gap: var(--size-xl);
}
.gap\.l{    
    gap: var(--size-l);
}
.gap\.m{    
    gap: var(--size-m);
}
```
{% endtab %}
{% endtabs %}
