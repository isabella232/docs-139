# Recipes

### Export all the components, define one as main, create the types and minify the code.

```bash
exports src/*/*.{js,ts,jsx,tsx} --main components --types --exports --minify
```

`@atomico/exports` will send all found components to ESbuild to compile and minify, then define the parent of your package and finally create the types.
