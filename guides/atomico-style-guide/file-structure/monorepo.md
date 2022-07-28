# Monorepo

The following format is friendly when sharing a webcomponent to NPM using @atomico/exports

```
├── src
│   ├── define.{js,ts,jsx,tsx}
│   ├── elements.{js,ts,jsx,tsx}
│   ├── define.test.{js,ts,jsx,tsx}
│   └── slots
│       ├── my-sub-element-1.{js,jsx,ts,tsx}
│       └── my-sub-element-2.{js,jsx,ts,tsx}
├── README.md
├── index.html
├── .npmignore
├── package.json
└── tsconfig.json
    
```

From the previous structure we highlight:

1. `src/define`: import the components from `src/elements` and declare them as customElements
2. `src/elements`: groups and export components as CustomElements

### Why separate the export of the element from the declaration?

since it improves the customElements definition experience, example:

```jsx
import "my-component"; // internalmente define el customTag
import { MyElement } from "my-component/elements"; // no define el customTag
```

Thanks to @atomico/exports this is really easy, example:

```bash
exports src/{define,elements}.{ts,tsx} --exports --types
```

You can see a use case of this structure in @atomico/components

{% embed url="https://github.com/atomicojs/components/tree/master/src/components/table" %}
