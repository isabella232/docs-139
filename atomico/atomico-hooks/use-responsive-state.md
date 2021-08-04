---
description: >-
  Declare a state based on a responsive expression similar to using the tag
  img[srcset].
---

# use-responsive-state

## Modulo

```javascript
import { useResponsiveState } from "@atomico/hooks/use-responsive-state";
```

## Syntax

```jsx
const expression = "phone, tablet 720px, destop 1080px";
const state = useResponsiveState(expression);
```

Where:

* `state`: `String`, Current state according to the comparison between experiment and matchMedia.
* `expression`: `String`, An expression that declares the serialized states.

## Expressions

```text
"<defaultState>, <caseState> <size>"
```

Where:

* `defaultState`: Default state this cannot contain the use of commas `", "`.
* `caseState`: Status to show if matchMedia match.
  * size: size expression to observe, example:
    * "1080px": `(min-width: 1080px)`
    * "1080x720px": `(min-width: 1080px) and (min-height: 720px)`
    * "50rem": `(min-width: 50rem)`
    * "50em": `(min-width: 50em)`

### Example

The following example shows the use of useResponsiveState, to display a message based on the mediaquery. [**Livepreview**](https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/collection/n2tZyzx4LMKqk1jNE0e9/gGV9X6OW5gINqRBFp8mK)**.**

```jsx
import { c } from "atomico";
import { useResponsiveState } from "@atomico/hooks/use-responsive-state";

function myComponent() {
  const state = useResponsiveState("phone, tablet 720px, desktop 1080px");
  return (
    <host>
      <center>
        <h1>{state}</h1>
        <p>
          👋 To see the effect it is necessary to resize the preview, more info

        </p>
      </center>
    </host>
  );
}
```



