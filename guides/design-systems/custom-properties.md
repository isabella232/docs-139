---
description: Theory of practical form the definition of variables for design systems
---

# Custom properties

> Personal recommendation as author of [**Atomico\(@uppercod\)**](https://twitter.com/uppercod)\*\*\*\*

### Custom properties of thema

They are the external variables to our design system and belong to the site or application that implements our design system.

```css
:root{
    --theme-primary: black;
    --theme-font-display: "font-title";
    --theme-font-content: "font-content";
}
```

#### Syntax

```css
:root{
    --theme-<utility>: value;
}
```

Where: 

1. `utility`: Any utility associated with the theme, such as font size, margins, spaces, color, background and status.

The prefix is not strict, since these are inherited directly from the site or application.

### Design system custom properties

**Global context**: all variables shared by our design system, these are only imported one for all components.

#### Syntax: 

```css
:root{
    --<prefix>-<utility>: <value>;
}
```

**Example:**

{% tabs %}
{% tab title="css" %}
```css
:root{
    --ds-primary: var(--theme-primary);
}
```
{% endtab %}

{% tab title="import" %}
```markup
<link rel="stylesheet" href="my-ds.css">
```
{% endtab %}
{% endtabs %}

From the `import` example I want you to infer that all the global custom properties of the design system are found only in the `my-ds.css` file, the benefit of this is the import from the main document, allowing us:

1. Avoid blocking typographic import.
2. Styles before loading, we can precede the load definition of our component with base styles to improve the web vitals or simply hide our component to avoid a display before loading, example in tab `"Example of styles before loading"`
3. Global variables can be referenced by the component without an import by the component, example in tab `"example of using global variables"`

{% tabs %}
{% tab title="Example of styles before loading" %}
```css
/**
Our component will only show one
once you have registered.
This is generated automatically 
if you use @atomico/exports
**/
my-component:not(:defined){
    visibility: hidden;
}
```
{% endtab %}

{% tab title="example of using global variables" %}
```javascript
// This does not prevent the component from having
// unique or shared properties between
// a group of components.
button.styles = css`
  :host {
    background: var(--ds-primary);
  }
  :host[warning] {
    background: var(--ds-warning);
  }
  :host[success] {
    background: var(--ds-success);
  }
`;
```
{% endtab %}
{% endtabs %}

#### Local context

```javascript
button.styles = css`
  :host {
    background: var(--ds-button-background);
  }
`;
```

But as a recommendation, avoid atomizing the custom properties, it is more practical to generalize, since it reduces the complexity of editing the design system itself, but this will depend directly on the design of the UI. Suppose we have formalized the action space for every clickable component, example:

```css
:root{
    --ds-action-space: padding: .5rem 1rem;
}
```

The exposed custom property can be inherited between components such as input, button, link, tags and more.

