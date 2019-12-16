---
description: Getting started with Atomic is simple and fast
---

# Installation

### Project generator

```text
npm init @atomico
```

Recommended installation, allows you to create a dynamic environment to start with Atomico, supports :

1. Import script from html, similar to Parceljs.
2. Live reload.
3. multiple input files.
4. Dinamic import.
5. Export through expressions, eg `src/components/*-*.js`,
6. Automatic optimization.
7. Javascript and Typescript.

### Custom environments

#### Step 1, Npm

```bash
npm install atomico
```

#### Step 2, Configure babel JSX pragma

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
The use of the JSX is optional you can use [Template string](../guides/virtual-dom.md) and skip the 2 step.
{% endhint %}



