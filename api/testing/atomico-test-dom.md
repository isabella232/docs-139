# atomico/test-dom

### fixture

function that allows to keep the render on a single node for each execution of `it`, the container will be unmounted at the end of each execution of `it`.

```javascript
import { html } from "atomico";
import { expect } from "@esm-bundle/chai";
import { fixture } from "atomico/test-dom";
import { Component } from "./component.js";

describe("my test", () => {
  it("my-component", async () => {
    const component = fixture(html`<${Component}>
        <span>content...</span>
    </${Component}>`);

    await component.updated;

    /** Test logic */
  });
});
```

This allows each fixture execution inside `it` to be related to the container used for the test, allowing you to fily test external DOM changes, example:

```javascript
import { html } from "atomico";
import { expect } from "@esm-bundle/chai";
import { fixture } from "atomico/test-dom";
import { Component } from "./component.js";


describe("my test", () => {
  it("my-component", async () => {
    // first instance of the render, it will return the component
    const component = fixture(html`<${Component}>
        <span>content...</span>
    </${Component}>`);

    await component.updated;
    
    // updates the content of the span tag of the first instance of the render
    fixture(html`<${Component}>
        <span>new content...</span>
    </${Component}>`);
    
    await component.updated;

    expect(
          component.querySelector("span").textContent
    ).to.equal("new content...");
  });
});
```



