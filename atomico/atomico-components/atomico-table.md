# @atomico/table

**Webcomponent** built with [Atomico JS](https://atomicojs.dev/), Simple to use and customize table. Includes additional support for React and Preact.





### Custom properties

| Global                         | Description                                                 |
| ------------------------------ | ----------------------------------------------------------- |
| --table--radius                | table borde-radius                                          |
| --table--background            | table background                                            |
| --table--border                | table borde                                                 |
| --table--border-split          | border dividing cells                                       |
| --table--row-gap               | row spacing                                                 |
| --table--row-radius            | row border-radius                                           |
| --table--row-shadow            | row box-shadow                                              |
| --table--row-background        | row background                                              |
| --table--row-header-radius     | border-radius of the row declared as slot="header"          |
| --table--row-header-shadow     | box-shadow of the row declared as slot="header"             |
| --table--row-header-background | background of the row declared as slot="header"             |
| --table--row-last-radius       | borde-radius de la ultima fila                              |
| --table--cell-align            | cell alignment, default middle                              |
| --table--cell-padding          | cell padding                                                |
| --table--cell-header-padding   | padding of the cell inside the Tr declared as slot="header" |

### Properties Table

**collapse**: **** `boolean`, **** collapses the rows of the table, if breakpoint is defined the component will automatically define this props when detecting the match with breakpoint.

**breakpoint**: `string`, media query to observe to copal the table.

### Properties Tr

**sticky:** `boolan`**,**The table row will set its position according to the scroll position

{% hint style="info" %}
The following properties are automatically defined by the component to declare state.
{% endhint %}

**td**: `array` ,list of Td nodes associated with the TR component

**collapse**: `boolean`, property defined according to the state of the parent.

**last:** last row of the table

### Properties Td

**width**: string, cell width.

