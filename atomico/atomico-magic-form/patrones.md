---
description: >-
  MagicForm makes it easy to send data to the server, here are some useful
  patterns
---

# Patrones

### Login

```tsx
async login(form: HTMLFormElement){
  const user = Object.fromEntries(new FormData(form) as any);
  
  return myApi.login(user);
}
```

### Create data

```tsx
async create(form: HTMLFormElement){
  const result = await fetch("/my-api",{method: "post",body: new FormData(form)});
  return result.json();
}
```

### Search

The following action allows us to generate searches from a form tag that has an input search, the objective is to consume the search value recursively only if there has been a change in the input search during the fetch performed.

```tsx
async search(form: HTMLFormElement) {
  const beforeFetch = Object.fromEntries(new FormData(form) as any);
  
  await new Promise((resolve) => setTimeout(resolve, 1000)); // debounce
  
  const result = await fetch(beforeFetch.search);
  
  const afterFetch = Object.fromEntries(new FormData(form) as any);
  
  if (afterFetch.search === beforeFetch.search) {
    return result;
  } else {
    return login(form);
  }
}
```
