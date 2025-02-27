# Table of contents

* [👋 Atomico](README.md)
* [🚀 Getting started with Atomico](getting-started-with-atomico.md)

## Api

* [🧬 Props(Properties)](api/props/README.md)
  * [Value cycle as prop](api/props/value-cycle-as-prop.md)
* [🧩 VirtualDOM](api/virtualdom/README.md)
  * [Advanced](api/virtualdom/advanced.md)
* [🎣 Hooks](api/hooks/README.md)
  * [useProp](api/hooks/useprop.md)
  * [useEvent](api/hooks/useevent.md)
  * [useRef](api/hooks/useref.md)
  * [useHost](api/hooks/usehost.md)
  * [useState](api/hooks/usestate.md)
  * [useReducer](api/hooks/usereducer.md)
  * [useEffect and useLayoutEffect](api/hooks/useeffect-y-uselayouteffect.md)
  * [useMemo and useCallback](api/hooks/usememo-y-usecallback.md)
  * [useUpdate](api/hooks/useupdate.md)
  * [useContext](api/hooks/usecontext.md)
* [🔬 Testing](api/testing/README.md)
  * [Render cycle](api/testing/test-dom.md)
  * [atomico/test-hooks](api/testing/test-hooks.md)
  * [atomico/test-dom](api/testing/atomico-test-dom.md)

## Guides

* [🧠 Atomico design patterns](guides/atomico-design-patterns/README.md)
  * [♻ Webcomponents with hybrid rendering](guides/atomico-design-patterns/webcomponents-with-hybrid-rendering.md)
  * [🔗 Slot as templates](guides/atomico-design-patterns/slot-as-templates.md)
* [🗺 Atomico style guide](guides/atomico-style-guide.md)
  * [Component](guides/atomico-style-guide/component.md)
  * [File structure](guides/atomico-style-guide/file-structure/README.md)
    * [Monorepo](guides/atomico-style-guide/file-structure/monorepo.md)
    * [Design systems](guides/atomico-style-guide/file-structure/design-systems.md)
* [🛡 Atomico with Typescript](guides/atomico-with-typescript/README.md)
  * [Props](guides/atomico-with-typescript/props.md)
  * [Component](guides/typescript.md)
  * [Meta-types](guides/atomico-with-typescript/meta-types/README.md)
    * [Type](guides/atomico-with-typescript/meta-types/type.md)
    * [Event declaration](guides/atomico-with-typescript/declare-meta-types-to-the-component.md)
    * [Method declaration](guides/atomico-with-typescript/meta-types/method-declaration.md)
  * [Check the correct use of hooks](guides/atomico-with-typescript/check-the-correct-use-of-hooks.md)
* [🤝 Atomico and React](guides/atomico-and-react/README.md)
  * [⚛ From React to Atomico](guides/atomico-and-react/from-react-to-atomico/README.md)
    * [Rendering Differences](guides/atomico-and-react/from-react-to-atomico/rendering-differences.md)
    * [VirtualDOM api differences](guides/atomico-and-react/from-react-to-atomico/virtualdom-api-differences.md)
* [💧 SSR / SSG](guides/ssr-ssg.md)
* [🔀 Slot](guides/slot.md)
* [🗃 Archives](guides/archives/README.md)
  * [Class inheritance](guides/class-inheritance.md)
  * [Forms and shadowDOM](guides/forms-and-shadowdom.md)
  * [Tips](guides/tips.md)
  * [Design systems](guides/archives/design-systems.md)

## packages

* [@atomico/exports](packages/introduction/README.md)
  * [CLI and Flags](packages/introduction/atomico-exports.md)
  * [Wrapper for React](packages/introduction/wrapper-for-react.md)
* [@atomico/hooks](packages/atomico-hooks/README.md)
  * [use-intersection-observer](packages/atomico-hooks/use-intersection-observer.md)
  * [use-ref-values](packages/atomico-hooks/use-ref-values.md)
  * [use-script](packages/atomico-hooks/use-script.md)
  * [use-attributes](packages/atomico-hooks/use-attributes.md)
  * [use-prop-proxy](packages/atomico-hooks/use-prop-proxy.md)
  * [use-click-press](packages/atomico-hooks/use-click-press.md)
  * [use-dollars](packages/atomico-hooks/use-dollars.md)
  * [use-reflect-event](packages/atomico-hooks/use-reflect-event.md)
  * [use-keyboar](packages/atomico-hooks/use-keyboar.md)
  * [use-click-coordinates](packages/atomico-hooks/use-click-coordinates.md)
  * [use-copy](packages/atomico-hooks/use-copy.md)
  * [use-debounce-state](packages/atomico-hooks/use-debounce-state.md)
  * [use-form](packages/atomico-hooks/use-form.md)
  * [use-listener](packages/atomico-hooks/use-listener.md)
  * [use-disabled](packages/atomico-hooks/use-disabled.md)
  * [use-css](packages/atomico-hooks/use-css.md)
  * [use-channel](packages/atomico-hooks/use-channel.md)
  * [use-promise](packages/atomico-hooks/use-promise.md)
  * [use-responsive-state](packages/atomico-hooks/use-responsive-state.md)
  * [use-parent](packages/atomico-hooks/use-parent.md)
  * [use-resize-observer](packages/atomico-hooks/use-resize-observer.md)
  * [use-slot](packages/atomico-hooks/use-slot/README.md)
    * [useSlot](packages/atomico-hooks/use-slot/useslot.md)
    * [useProxySlot](packages/atomico-hooks/use-slot/useproxyslot.md)
  * [use-render](packages/atomico-hooks/use-render.md)
  * [use-mutation-observer](packages/atomico-hooks/use-mutation-observer.md)
  * [use-css-light-dom](packages/atomico-hooks/use-css-light-dom.md)
  * [use-controller](packages/atomico-hooks/use-controller.md)
  * [use-router](packages/atomico-hooks/use-router.md)
  * [use-async-effect](packages/atomico-hooks/use-async-effect.md)
  * [use-child-nodes](packages/atomico-hooks/use-child-nodes.md)
  * [use-force-render](packages/atomico-hooks/use-force-render.md)
* [@atomico/components](packages/atomico-components/README.md)
  * [@atomico/keen-slider](packages/atomico-components/keen-slider.md)
  * [@atomico/modal](packages/atomico-components/modal.md)
  * [@atomico/lottie](packages/atomico-components/lottie.md)
  * [@atomico/table](packages/atomico-components/table.md)
* [@atomico/react](packages/atomico-react.md)
* [@atomico/store](packages/atomico-store/README.md)
  * [Store](packages/atomico-store/store.md)
  * [Hooks](packages/atomico-store/hooks.md)
  * [Examples](packages/atomico-store/examples/README.md)
    * [Cart](packages/atomico-store/examples/cart.md)
* [@atomico/router](packages/atomico-router.md)
* [@atomico/magic-form](packages/atomico-magic-form/README.md)
  * [MagicFormProvider | \<magic-form-provider>](packages/atomico-magic-form/magicformprovider-or-less-than-magic-form-provider-greater-than.md)
  * [MagicForm | \<magic-form>](packages/atomico-magic-form/magicform-or-less-than-magic-form-greater-than.md)
  * [MagicForm Hooks](packages/atomico-magic-form/magicform-hooks.md)
  * [MagicForm in React and Preact](packages/atomico-magic-form/magicform-in-react-and-preact.md)
  * [MagicForm in Microfrontend](packages/atomico-magic-form/magicform-in-microfrontend.md)
  * [MagicForm Patterns](packages/atomico-magic-form/magicform-patterns.md)
* [🚫 Deprecated](packages/deprecated/README.md)
  * [@atomico/design-tokens](packages/deprecated/atomico-design-tokens/README.md)
    * [@atomico/design-tokens api](packages/deprecated/atomico-design-tokens/atomico-design-tokens-api.md)

## Support

* [Discord](https://discord.gg/7z3rNhmkNE)
* [Github](https://github.com/atomicojs/atomico)
* [Twitter](https://twitter.com/atomicojs)
