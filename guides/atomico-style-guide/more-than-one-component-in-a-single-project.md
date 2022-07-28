---
description: >-
  Sometimes we centralize the generation of more than one component in a
  repository without being a monorepo, Atomico allows us to maintain this
  pattern, since it is ideal for design systems
---

# More than one component in a single project

### Recommended file structure for webcomponents

you always prefer to keep each component isolated in a directory with names associative to the same component, example:

```
├── my-button
│   ├── my-button.{js,jsx,ts,tsx}
│   ├── my-button.test.{js,jsx,ts,tsx}
│   ├── my-button.stories.js
│   └── my-button.md
└── my-input
    ├── my-input.{js,jsx,ts,tsx}
    ├── my-input.test.{js,jsx,ts,tsx}
    ├── my-input.stories.js
    └── my-input.md
```

**why?** The NPM-oriented [`@atomico/exports`](../../atomico/atomico-exports.md) packaging tool allows automatic export from the recommended structure,`@atomico/exports` will generate a modern package.json to current standards, automatically generating all (main, types, exports and more) what is necessary for your package to be distributed correctly.
