# Flexbox

**El modelo de caja flexible** fue diseñado como un modelo unidimensional de layout, y como un metodo que puede ayudar a distribuir el espacio entre los ítems de una interfaz y mejorar las capacidades de alineación.

 Flexbos maneja el layout como una sola dimension a la vez, ya sea columna o fila.

Dado que flexbox es un módulo completo y no una sola propiedad, implica un montón de cosas, incluyendo todo su conjunto de propiedades. Algunas de ellas están destinadas a ser establecidas en el contenedor (elemento padre, conocido como "**flex container**") mientras que las otras están destinadas a ser establecidas en los hijos (llamados **flex items**).

Si la maquetación "normal" se basa en las direcciones de flujo en bloque y en línea, la maquetación flexible se basa en las "direcciones de flujo flexibles".

 <!-- imagen -->
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/11/00-basic-terminology.svg "Idea principal")

Los elementos se dispondrán siguiendo el eje principal (desde el inicio hasta el final) o el eje transversal (desde el inicio hasta el final).

* **main axis** - El eje principal de un contenedor flex es el eje principal a lo largo del cual se disponen los elementos flex. Cuidado, no es necesariamente horizontal; depende de la propiedad flex-direction  
* **main-star/main-end** - Los elementos flex se colocan dentro del contenedor empezando por el inicio principal y llegando hasta el final principal.  
* **Main size** - La anchura o la altura de un elemento flex, cualquiera que sea la dimensión principal, es el tamaño principal del elemento. La propiedad de tamaño principal del elemento flexible es la propiedad "anchura" o "altura", la que se encuentre en la dimensión principal.  
* **Cross axis** - El eje perpendicular al eje principal se llama eje transversal. Su dirección depende de la dirección del eje principal.  
* **Cross-star / Cross-end** - Las líneas flex se llenan de artículos y se colocan en el contenedor comenzando por el lado de inicio transversal del contenedor flex y avanzando hacia el lado de finalización transversal.  
* **Cross size** - La anchura o la altura de un elemento flex, cualquiera que esté en la dimensión transversal, es el tamaño transversal del elemento. La propiedad de tamaño transversal es la que esté en la dimensión transversal de 'anchura' o 'altura'.

---
---

># Propiedades del Flexbox

---
---
>## Propiedades del contenedor
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/01-container.svg "Idea principal")

**Display** Define un contenedor flex; inline o block dependiendo del valor dado. Habilita un contexto flex para todos sus hijos directos.
```css
.container {
  display: flex; /* o inline-flex */
}
```
___
**Flex-direction** Esto establece el eje principal, definiendo así la dirección en la que se colocan los elementos flex en el contenedor flex. Flexbox es un concepto de diseño en una sola dirección. Piensa que los elementos flex se colocan principalmente en filas horizontales o en columnas verticales.
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg "Idea principal")
```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
* row (default): de izquierda a derecha en ltr; de derecha a izquierda en rtl 
* row-reverse: de derecha a izquierda en ltr; de izquierda a derecha en rtl 
* column: igual que la fila pero de arriba a abajo
* column-reverse: igual que fila-inversa pero de abajo a arriba
___
**Flex-wrap** Por defecto, los elementos de flexión tratarán de encajar en una línea. Puedes cambiar esto y permitir que los elementos se envuelvan como sea necesario con esta propiedad.
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/flex-wrap.svg "Idea principal")
```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```
* nowrap (default): todos los elementos flex estarán en una línea
* wrap: los elementos flex se envolverán en varias líneas, de arriba a abajo.
* wrap-reverse: los elementos flex se envolverán en varias líneas, de abajo a arriba.

Aquí se puede ver un [ejemplo visual.](https://css-tricks.com/almanac/properties/f/flex-wrap/)
___
**Flex-flow** Se trata de una abreviatura de las propiedades flex-dirección y flex-wrap, que juntas definen los ejes principal y transversal del contenedor flexible. El valor por defecto es row nowrap.

```css
.container {
  flex-flow: column wrap;
}
```
___
**justify-content** Define la alineación a lo largo del eje principal. Ayuda a distribuir el espacio libre sobrante cuando todos los elementos flexibles de una línea son inflexibles, o son flexibles pero han alcanzado su tamaño máximo. También ejerce cierto control sobre la alineación de los elementos cuando desbordan la línea.
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg "Idea principal")
```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```
* **flex-start** (por defecto): los elementos se empaquetan hacia el inicio de la dirección flex.  
* **flex-end**: los elementos se empaquetan hacia el final de la dirección de flexión.  
* **start**: los elementos se empaquetan hacia el inicio de la dirección del modo de escritura.  
* **end**: los elementos se empaquetan hacia el final de la dirección del modo de escritura.  
* **left**: los elementos se empaquetan hacia el borde izquierdo del contenedor, a menos que no tenga sentido con la dirección de flexión, entonces se comporta como start.  
* **right**: los elementos se empaquetan hacia el borde derecho del contenedor, a menos que no tenga sentido con la dirección de flexión, entonces se comporta como end.  
* **center**: los elementos se centran a lo largo de la línea.  
* **space-between**: los ítems se distribuyen uniformemente en la línea; el primer ítem está en la línea inicial, el último en la línea final.  
* **space-around**: los elementos se distribuyen uniformemente en la línea con el mismo espacio alrededor de ellos. Ten en cuenta que visualmente los espacios no son iguales, ya que todos los elementos tienen el mismo espacio a ambos lados. El primer elemento tendrá una unidad de espacio contra el borde del contenedor, pero dos unidades de espacio entre el siguiente elemento porque ese siguiente elemento tiene su propio espacio que se aplica.  
* **space-evenly**: los elementos se distribuyen de manera que el espacio entre dos elementos cualesquiera (y el espacio hacia los bordes) es igual.  

Ten en cuenta que el soporte de los navegadores para estos valores es matizado. Por ejemplo, el **space-between** nunca obtuvo soporte de algunas versiones de Edge, y start/end/left/right no están en Chrome todavía. MDN [tiene gráficos detallados](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content). Los valores más seguros son flex-start, flex-end y center.

También hay dos palabras clave adicionales que puedes emparejar con estos valores: safe y unsafe. El uso de safe asegura que, independientemente de cómo se haga este tipo de posicionamiento, no se puede empujar un elemento de tal manera que se renderice fuera de la pantalla (por ejemplo, fuera de la parte superior) de tal manera que el contenido no se pueda desplazar también (lo que se llama "pérdida de datos").

___
**Align-content** Esto alinea las líneas de un contenedor flexible cuando hay espacio extra en el eje transversal, de forma similar a como justify-content alinea los elementos individuales dentro del eje principal.
>Nota: Esta propiedad sólo tiene efecto en los contenedores flexibles de varias líneas, donde flex-wrap está establecido como wrap o wrap-reverse). Un contenedor flexible de una sola línea (es decir, donde flex-wrap está establecido en su valor por defecto, no-wrap) no reflejará align-content.  

![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg "Idea principal")
```css
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}
```

* **Normal (por defecto)**: los elementos se empaquetan en su posición por defecto como si no se hubiera establecido ningún valor.  
* **Flex-start / start**: los elementos se empaquetan al principio del contenedor. El (más soportado) flex-start honra la dirección de flexión mientras que start honra la dirección del modo de escritura.  
* **Flex-end / end**: elementos empaquetados hasta el final del contenedor. El (más soportado) flex-end honra la dirección flex mientras que end honra la dirección del modo de escritura.  
* **Center**: elementos centrados en el contenedor.  
* **Space-between**: elementos distribuidos uniformemente; la primera línea está al principio del contenedor mientras que la última está al final.  
* **Space-around**: los elementos se distribuyen uniformemente con el mismo espacio alrededor de cada línea.  
* **Space-evenly**: los elementos se distribuyen uniformemente con el mismo espacio alrededor de ellos.  
* **Stretch**: las líneas se estiran para ocupar el espacio restante.

Las palabras clave modificadoras safe y unsafe pueden utilizarse junto con el resto de estas palabras clave (aunque hay que tener en cuenta la compatibilidad con los navegadores), y se encargan de ayudarle a evitar la alineación de elementos de forma que el contenido sea inaccesible.

___
**gap, row-gap, column-gap** La propiedad gap controla explícitamente el espacio entre los elementos flex. Aplica ese espacio sólo entre los elementos, no en los bordes exteriores.
 

![**idea principal**](https://css-tricks.com/wp-content/uploads/2021/09/gap-1.svg "Idea principal")
```css
.container {
  display: flex;
  ...
  gap: 10px;
  gap: 10px 20px;
  row-gap: 10px;
  column-gap: 20px;
}
```

> El comportamiento podría ser pensado como un canal mínimo, ya que si el canal es más grande de alguna manera (debido a algo como justify-content: space-between;) entonces el gap sólo tendrá efecto si ese espacio terminara siendo más pequeño.

No es exclusivamente para flexbox, el gap funciona también en grid y en multi column layout.  

---
---
>## Propiedades del Hijo (items)
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/02-items.svg "Idea principal")

**Order** Por defecto, los elementos de flexión se presentan en el orden de origen. Sin embargo, la propiedad order controla el orden en que aparecen en el contenedor de flex.  
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/order.svg "Idea principal")
```css
.item {
  order: 5; /* default is 0 */
}
```
___  

**Flex-grow** Define la capacidad de un elemento flexible para crecer si es necesario. Acepta un valor sin unidades que sirve como proporción. Determina la cantidad de espacio disponible dentro del contenedor flexible que debe ocupar el elemento.

Si todos los elementos tienen flex-grow establecido en 1, el espacio restante en el contenedor se distribuirá por igual entre todos los hijos. Si uno de los hijos tiene un valor de 2, ese hijo ocupará el doble de espacio que cualquiera de los otros (o lo intentará, al menos). 
![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/flex-grow.svg "Idea principal")
```css
.item {
  flex-grow: 4;
}
```
>Números negativos son invalidos
___

**Flex-shrink** Define la capacidad de un elemento flexible para encogerse si es necesario. 

```css
.item {
  flex-shrink: 3;
}
```
>Números negativos son invalidos
___

**Flex-basis** Define el tamaño por defecto de un elemento antes de distribuir el espacio restante. Puede ser una longitud (por ejemplo, 20%, 5rem, etc.) o una palabra clave.  
La palabra clave auto significa "look at my width or height property / *mira mi propiedad de anchura o altura*" (lo que hacía temporalmente la palabra clave main-size hasta que fue desaprobada).  
La palabra clave content significa "dimensionar en base al contenido del elemento" - esta palabra clave no está bien soportada todavía, por lo que es difícil de probar y más difícil de saber lo que hacen sus hermanos max-content, min-content, y fit-content.

```css
.item {
  flex-basis:  | auto;
}
```
>Si se establece en 0, el espacio extra alrededor del contenido no se tiene en cuenta. Si se establece en auto, el espacio extra se distribuye en base a su valor flex-grow. [Ejemplo](https://www.w3.org/TR/css-flexbox-1/images/rel-vs-abs-flex.svg).
___

**Flex** Es la abreviatura de flex-grow, flex-shrink y flex-basis combinados.  
El segundo y tercer parámetro (flex-shrink y flex-basis) son opcionales. El valor por defecto es 0 1 auto, pero si lo establece con un solo valor numérico, como flex: 5;, eso cambia la flex-basis a 0%, así que es como establecer flex-grow: 5; flex-shrink: 1; flex-basis: 0%;.

```css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```
>Se recomienda utilizar esta propiedad abreviada en lugar de establecer las propiedades individuales. La abreviatura establece los otros valores de forma inteligente.
___
**align-self** Esto permite anular la alineación por defecto (o la especificada por align-items) para elementos flexibles individuales.

![**idea principal**](https://css-tricks.com/wp-content/uploads/2018/10/align-self.svg "Idea principal")
```css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```
>Tenga en cuenta que float, clear y vertical-align no tienen efecto en un elemento flex.
___

> # Cosas a tener en cuenta
___

 ## Prefijos
 Flexbox requiere un prefijo de proveedor para soportar la mayor cantidad de navegadores posibles. No sólo incluye anteponer a las propiedades el prefijo del proveedor, sino que hay nombres de propiedades y valores completamente diferentes. Esto se debe a que la especificación de Flexbox ha cambiado con el tiempo, creando una versión "antigua", "joven" y "nueva".  
Tal vez la mejor manera de manejar esto es escribir en la nueva sintaxis y ejecutar su CSS a través de Autoprefixer, que maneja los fallbacks muy bien.

 ## Navegadores que lo soportan

Los principales como Chrome, firefox, egde y safari soportan Flexbox. Puede ver una lista completa de los navegadores (y la versión) que soportan Flexbox [aquí](https://caniuse.com/flexbox).

 ## Algunos Bugs

Si bien no existen muchos bugs en Flexbox, Philip Walton y Greg Whitworth tienen un [repositorio en github](https://github.com/philipwalton/flexbugs) con todos los posibles errores que puede encontrar.  

## Flex Responsivo

Otra forma de hacer un diseño responsivo es cambiar el porcentaje de la propiedad flex de los elementos flex para crear diferentes diseños para diferentes tamaños de pantalla. También tenemos que incluir flex-wrap: wrap; en el contenedor flex para que este ejemplo funcione:

```css
.flex-container {
  display: flex;
  flex-wrap: wrap;
}

.flex-item-left {
  flex: 50%;
}

.flex-item-right {
  flex: 50%;
}

/* Diseño responsivo - hace un diseño de una columna en lugar de un diseño de dos columnas */
@media (max-width: 800px) {
  .flex-item-right, .flex-item-left {
    flex: 100%;
  }
}
```

[Se puede ver de forma visual aquí](https://www.w3schools.com/css/tryit.asp?filename=trycss3_flexbox_responsive2)

## Aprende Flex con... una rana

Quise agregar esto ya que, buscando información de este control encontre este curioso sitio web para aprender Flex de forma visual con ayuda de una rana (Froggy). [Aquí esta la página](https://flexboxfroggy.com/#es)