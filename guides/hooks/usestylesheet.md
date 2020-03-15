---
description: >-
  It allows to use adoptedStyleSheets, this optimizes the load of the css
  associated to the web-component when using shadowDom
---

# useStyleSheet

AdoptedStyleSheet? [https://developers.google.com/web/updates/2019/02/constructable-stylesheets](https://developers.google.com/web/updates/2019/02/constructable-stylesheets).

### Usage

```jsx
const style1 = `:host{ background : black; display: block; }`;
const style2 = `:host{ padding : 2rem; color : black; }`;

function WebComponent(){
    useStyleSheet(style1,style2);
    return <host shadowDom/>
}
```

