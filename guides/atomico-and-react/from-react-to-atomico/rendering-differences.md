# Rendering Differences

Atomico escapa de la lógica de inmutabilidad de DOM React y se acerca mas al APi nativa del DOM.

esto quiere decir que Atomico a nivel de scope solo es responsable de recibir las props y renderizar el DOM, pero no observa las mutaciones internas del DOM de forma automática, esto es por que las mutaciones a nivel nativo pueden provenir de cualquier lugar, ahora para asegurar una sincronización del estado es conveniente que todo webcomponent que desea ser observado emite un evento evento que defina una modificación interna.

Ud puede hacer esto facilmente mediante el uso de [useevent.md](../../../api/hooks/useevent.md "mention")
