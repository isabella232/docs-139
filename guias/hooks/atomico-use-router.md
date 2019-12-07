---
description: >-
  Pequeño y simple router para gestionar web-components, a base de popstate y
  hooks
---

# atomico/use-router

Antes de comenzar con la lectura de los hooks, recomiendo comprender el patrón de expresiones creado para use-route

| Patrón | Descripción  |
| :--- | :--- |
| `/folder` | Requerido y de coincidencia exacta |
| `/:id` | Parámetro requerido, captura el folder y asocia la captura a la propiedad id |
| `/:id?` | Parámetro opcional, captura el folder y asocia la captura a la propiedad id  |
| `/:id...` | Parámetro opcional spread, captura todo lo que siga el folder y asocia la captura a la propiedad id  |
| /\* | Requerido, permite no definir de forma escrita el nombre del folder  |

## useRoute

```javascript
let [inRoute, params] = useRoute("/my-route");
```

Permite observar el estado de una ruta, donde:

* `"/my-route"` : String, patron de ruta a suscribirse al router.
* `inRoute` : Boolean, define si la ruta posee conciencia.
* `params`: Objeto que almacena los parámetros capturados por el router.

## useRouter

```javascript
let paths = {
    "/": ()=>"in root",
    "/:id": ({id})=><User id={id}/>,
    "default": ()=>"404"
};
let View = useRouter(paths);
```

Permite observar el estado de una o más rutas a través de un objeto, donde:

* `paths` : rutas a observar por useRouter, de concidir con un indice del objeto se ejecutara o retornara el valor del indice.
* `View` : retorno de paths en funcion de la ruta.

## useRedirect

```javascript
let redirect = useRedirect(optionalPath)
```

Permite redirecionar la ruta, donde : 

* `optionalPath` : String opcional, de ser definido redirect apuntara solo al path optionalPath.
* `redirect` : Callback que redirecciona el navegador.





