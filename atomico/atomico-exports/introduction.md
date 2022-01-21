# Introduction

`@atomico/exports` is a tool like CLI oriented to have an efficient and aesthetic distribution of packages through NPM or CDN.

#### Efficient?

Yes, thanks to the use of Esbuild and internal processes of @atomico/exports it optimizes your distribution in:

1. Code splitting to subdivide your code efficiently.
2. Preprocess .css files as js modules through postcss.
3. Import of assets separately as URLs relative to the module, this prevents the origin of your assets from being broken when consuming it from a CDN.
4. Component export using expressions, example `src/**/*.js`.
5. Detect external dependencies(they are not part of the bundle)

#### Esthetic?

`@atomico/exports` takes care of the aesthetics of your package, managing everything necessary to achieve the following import format:

```js
// Import 1
import { MyButton, MyInput, MyRadio } from "my-components";
// Import 2
import { MyButton } from "my-components/button";
```

to achieve this `@atomico/exports` manages part of the `exports`, `types` and other properties of your package.json, in order to achieve a perfect aesthetic export.

### Usage

It is recommended to add to the publish queue of the NPM package, since its execution is only necessary when we export our package.

```json
"scripts": {
    "exports": "exports src/*/*.{js,ts,jsx,tsx} --main components --types --exports --minify",
    "prepublishOnly": "npm run exports"
}
```

## Recipes

### Export all the components, define one as main, create the types and minify the code.

```bash
exports src/*/*.{js,ts,jsx,tsx} --main components --types --exports --minify
```

`@atomico/exports` will send all found components to ESbuild to compile and minify, then define the parent of your package and finally create the types.
