---
description: Getting started with Atomic is simple and fast
---

# Installation

### Step 1, Npm

```bash
npm install atomico
```

### Step 2, Configure babel JSX pragma

Atomico uses the letter `h` for the JSX declaration, the following configuration is recommended for babel.

```javascript
{
  "plugins": [
    ["@babel/plugin-transform-react-jsx", {
      "pragma": "h", // default pragma is React.createElement
     }]
  ]
}
```

{% hint style="info" %}
The use of the JSX is optional you can use Template string and skip the 2 step.
{% endhint %}

## Atomico base

It allows the creation of web-components and applications with Atomico, the following pre-configured repository with bundle-cli allows:

1. Livereload for your HTML documents.
2. Dinamic Import.
3. Group of dependencies.
4. Individualization of dependencies.
5. Structure recommendation for your project.

{% embed url="https://github.com/atomicojs/base" %}

```bash
# first
git clone https://github.com/atomicojs/base
# open your folder
npm install
# wait and run
npm run dev
# check localhost: 8080
```



