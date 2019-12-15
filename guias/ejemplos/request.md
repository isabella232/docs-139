# Request

Listar informacion proveniente de un servidor puede ser un atarea recurrente, atomico hace esto sumamente simple, para este ejemplo definiremos los siguientes objetivos : 

1. comunicar el web-component con un Api
2. listar la data en función de su estado, sea cargando, error o lista.

### paso 1 crear el web-component

Ud puede cumplir los objetivos de diversas formas, pero Atomico posee un customHook pensado para efectos asíncronos, este es [useLazy ](../hooks/atomico-use-lazy.md#uselazy)y se  encuentra en el modulo atomico/use-lazy, permite hacer request o dinamic import de forma simple, ej:

```jsx
import { h, customElement } from "atomico";
import { useLazy } from "atomico/use-lazy";

function ListItem({ label }) {
  let StateComponent = useLazy(async () => {
    let request = await fetch("https://jsonplaceholder.typicode.com/photos");
    let data = await request.json();

    return data.map(props => <Item {...props}></Item>);
  });
  return (
    <host>
      <StateComponent loading="loading..." error="Ups!"></StateComponent>
    </host>
  );
}

function Item({ title, url, thumbnailUrl }) {
  return (
    <div>
      <img src={thumbnailUrl} />
      title : {title}
      <a href={url}>view</a>
    </div>
  );
}

customElement("list-item", ListItem);

```



