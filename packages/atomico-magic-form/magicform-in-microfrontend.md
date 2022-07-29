# MagicForm in Microfrontend

MagicForm will help you manage your applications with microfrontend architecture, through the concept of isolated providers, for example:

```tsx
<MagicFormProvider actions={{
    async login(){...}
}}>
    <MagicFormProvider actions={actionsClient}>
        <PageClient/>
    </MagicFormProvider>
    <MagicFormProvider actions={actionsAdmin}>
        <PageAdmin/>
    </MagicFormProvider>
</MagicFormProvider>
```

Any action not registered by the provider will continue to bubble until the next provider.
