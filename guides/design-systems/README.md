---
description: >-
  I will show you a series of useful techniques to start programming your design
  systems with Atomico, analyzing the recommended structure and its files.
---

# ✨ Design systems

### Recommended structure

```bash
src/
	# Import, export and declare all our components
	components.js 
  # Group all the tokens in our system
	tokens.js
	# Structure example for our component
	/button
		button.{js,jsx,ts,tsx}
		button.md
		button.test.js
```

We will analyze the above.

### **src/components.js**

File that imports, exports and declares all the components of our design system, example:

```javascript
import { Button } from "./button/button";
export { Button } from "./button/button";

customElements.define("my-button", Button);
```

the utilities of this are to centralize everything in components.js are:

1. Clarity of the definition of customElements in a single file for our entire design system
2. Export of all customElements to be extended or redefined.

### src/tokens.js

File that centralizes the custom-properties of our design system, example:

```javascript
import { css } from "atomico";

export const tokensInput = css`
  :host {
    --background: var(--my-ds-input--background, #fff);
    --border-width: var(--my-ds-input--border-width, 1px);
    --border-color: var(--my-ds-input--border-color, black);
    --radius: var(--my-ds-input--radius, 0.5rem);
    --min-height: var(--my-ds-input--min-height, 40px);
  }
  .input-box {
    background: var(--background);
    min-height: var(--min-height);
  }
  .input-box--use-border {
    border: var(--border-width) solid var(--border-color);
  }
`;

export const tokenColors = css`
  :host {
    --primary: var(--my-ds--primary);
    --secondary: var(--my-ds--secondary);
    --success: var(--my-ds--warning);
    --warning: var(--my-ds--warning);
    --danger: var(--my-ds--warning);
    --info: var(--my-ds--warning);
  }
`;
```

From the previous example I highlight

#### 1. Classes of utilities in in tokensInput

#### 2. Declaration pattern of custom properties

```css
:host {
    --background: var(--my-ds-input--background, #fff);
}
```

`--background` will be a token that can be modified at the instance level and this inherits a global token from our system called `--my-ds-input--background`, I want you to notice that the global name of our custom property has a pattern, example:

```css
---my-ds-input--background
---<prefix>-<namespace>--<property>
```

Where:

1. **prefix**: Prefix of our global design system
2. **namespace**: group independent of our design system
3. **property**: property associated with the system, such as color, size, or other value.

**Why use the recommended pattern?** To individualize the configuration at the group level and separate the property definition from it thanks to the use of double hyphens \(**--**\), internally everything is simplified since the tokens only capture the global configuration global to reflect it to a simpler variable accessible only from the component instance level.

#### Instance level

It is the instance of the component either in HTML or JS, example:

{% tabs %}
{% tab title="HTML" %}
```markup
<my-component style="--background: red;"></my-component>;
```
{% endtab %}

{% tab title="JS" %}
```javascript
const component = document.createElement("my-component");

component.style = "--background: red";
```
{% endtab %}
{% endtabs %}

### src/button.js

{% tabs %}
{% tab title="JS" %}
```javascript
import { c, html, css } from "atomico";
import { tokensColor, tokensInput } from "../tokens";

function button(props) {

  return html`<host shadowDom>
    <button ...${props} class="input-box input-box--use-border">
      <slot name="icon"></slot>
      <slot></slot>
    </button>
  </host>`;
}

button.props = {
  name: String,
  value: String,
  disabled: Boolean,
};

button.styles = [
  tokensColor,
  tokensInput,
  css`
    .input-box {
      display: flex;
      gap: 1rem;
    }
  `,
];
```
{% endtab %}

{% tab title="JSX" %}
```jsx
import { c, css } from "atomico";
import { tokensColor, tokensInput } from "../tokens";

function button(props) {
  return (
    <host shadowDom>
      <button {...props} class="input-box input-box--use-border">
        <slot name="icon"></slot>
        <slot></slot>
      </button>
    </host>
  );
}

button.props = {
  name: String,
  value: String,
  disabled: Boolean,
};

button.styles = [
  tokensColor,
  tokensInput,
  css`
    .input-box {
      display: flex;
      gap: 1rem;
    }
  `,
];

export const Button = c(button);

```
{% endtab %}
{% endtabs %}

From the previous code I highlight:

1. **import of `"../tokens"`** and the destructuring of the module that declares the use of `tokensColor` and `tokensInput`.
2. **Utility classes**: Our component makes use of the utility classes of the `tokensColor`.
3. **button.styles**: Atomico allows to associate multiple styles through the use of an array.
4. **Button export.**

