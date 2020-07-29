---
description: >-
  Ud puede comenzar rapidamente a prototipar con Atomico desde cualquier
  navegador
---

# Inicio rapido

**Paso 1** : Cree un fichero HTML.

**Paso 2**: Copie el siguiente script

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <my-component></my-component>
    <script>
        import { c } from "http://unpkg.com/atomico";
        import html from "http://unpkg.com/atomico/html";

        const MyWebComponent = () =>
        html`<host>mi primer webcomponent con atomico</host>`;

        const HTMLMyWebComponent = c(MyWebComponent);

        customElements.define("my-component", HTMLMyWebComponent);
    </script>    
</body>
</html>
```

**Del ejemplo podemos destacar :**

1. `c`: Función que transforma `MyWebComponent`en un elemento HTML valido para customElements.define.
2. `html` : Función que crea el virtual-dom usando template-string. 
3. `MyWebComponent`: Función que reprecenta el  webcomponent.
   * `host`: etiqueta especial que representa la instancia del webcomponent, **todo webcomponent creado con Atomico siempre deberá retornar la etiqueta `<host/>.`**
4. `customElements.define`: Función que registra el `HTMLMyWebComponent` como parte del documento HTML.
   * `"my-component"` : Declara que el webcomponent será instanciado cada vez que se invoque la etiqueta`my-component`

