---
description: Eficiente y extremadamente pequeño.
---

# Virtual dom

El virtual-dom de Atomico es ligero y solo se procesa cuando el objeto es enviado a renderización, ud puede manifestar el virtual-dom de diversas formas en atomico, sea mediante jsx, template-string o un objeto plano.

### Sintaxis

```jsx
// JSX
<host>
    <button onclick={handler}>text</button>
</host>

// Template string
html`
    <host>
        <button onclick=${handler}>text</button>
    </host>
`

// Object

{
    nodeType : "host",
    children : [{
        nodeType : "button",
        onclick : handler
    }]
}
```

Todas las sintaxis expuestas se consideran validas, el virtual-dom de Atomico no mantiene referencias por lo que ud puede reutilizar un nodo sin problemas entre componentes, esto es altamente eficiente si desea que el proceso de render ignore nodos estáticos

```jsx
let static = <h1>node!</h1>

function WebComponent({value}){
    return <host>
        {static}
        <h1>dinamic {value}</h1>
    </host>
}
```

### Listas y Keyes

El proceso de render reutliza los nodos existentes cuando se genera un nuevo mapa de children, ej:

```jsx
<host>
    <my-tag/>
    <my-tag/>
    <my-tag/>    
</host>
```

Esto trae problemas cuando cada nodo conserva un estado independiente, ya que cada nueva lista no referencia el nodo en función de su estado.

Esto se soluciona con el uso de la propiedad **key**, esta propiedad permite que Atomico referencie el nodo no por posición en la lista sino por el indice referencial, este indice debe cumplir con los siguientes requisitos : 

1. Ser unico entre todos los children del padre.
2. Todos los children del padre deben poseer keys

Para mejorar el uso de key, atomico no limita su tipo, ud pude usar cualquier variable que permite referencia, ej Symbol.

```jsx
<host>
    <my-tag key="1"/>
    <my-tag key="2"/>
    <my-tag key="3"/>   
</host>
```

Esto optimiza la manipulación del dom regenerando y manteniendo los estados asociados al nodo de forma correcta.

### shadowDom

Propiedad especial del virtual-dom que permite activar el shadowDom de un nodo, eg

```jsx
<host shadowDom>
    inside shadowDom!
</host>

<host>
    inside lightDom!
</host>
```

La propiedad puede ser usada sobre cualquier nodo que soporte attachShadow

### styleSheet

Permite optimar la utilización del css asociado al web-component, permitiendo usar [**Constructable StyleSheet**](https://developers.google.com/web/updates/2019/02/constructable-stylesheets) solo cuando este disponible en el navegador, para mejorar la experiencia de uso sin Polyfill de Constructable Stylesheets, es recomendable usar styleSheet como un String, ej

```jsx
let styleSheet = `
    :host{width:100px;height:100px}
`
<host shadowDom styleSheet={styleSheet}>

</host>
```

Cada vez que Atomico procesa la variable como String, cache la instancia de StyleSheet construyendo una sola instancia que se puede asociar a múltiples web-components.

{% hint style="danger" %}
Para usar **styleSheet** solo funciona junto con la propiedad **shadowDom**
{% endhint %}

### is

los web-components permiten extender funcionalidades sobre tag ya existentes el el documento mediante el uso de **is**,  atomico soporta esta declaracon, ej:

```jsx
<button is="my-button"></button>
```

### Eventos

La asociación de eventos en Atomico requiere 2 condiciones :

1. el nombre del evento debe comenzar con el prefijo **on.**
2. el valor del nombre del evento debe ser del tipo funcion.

```jsx
<host onclick={handler} onmyCustomEvent={handler}>
</host>
```

{% hint style="danger" %}
Atomico no aplica transformadores adicionales fuera de quitar el prefijo **on** para suscribir el evento.  
{% endhint %}



