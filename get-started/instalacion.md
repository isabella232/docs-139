---
description: Comenzar con Atomico es simple y rapido
---

# Instalación

## Manual

### Paso 1, Npm

```bash
npm install atomico
```

### Paso 2, Configurar  pragma de babel JSX

Atomico usa la letra `h` para la declaración del JSX, la siguiente configuración es la recomendada para babel.

```javascript
{
  "plugins": [
    ["@babel/plugin-transform-react-jsx", {
      "pragma": "h", // default pragma is React.createElement
     }]
  ]
}
```

{% hint style="info" %}
EL uso del **JSX** es opcional ud puede usar **Template string**
{% endhint %}

## Atomico base

Permite la creación de web-components y/o aplicaciones con Atomico, el siguiente repositorio pre-configurado con bundle-cli permite:

1. Livereload para sus documentos HTML.
2. Dinamic import.
3. Agrupación de dependencias.
4. Individualización de dependencias.
5. Recomendación de proyecto.

{% embed url="https://github.com/atomicojs/base" %}

```bash
git clone https://github.com/atomicojs/base
```







