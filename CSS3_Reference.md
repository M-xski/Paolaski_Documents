##### *Paula Pérez Tafalla | 2º Desarrollo de Aplicaciones Web | Curso 2016-17*

## CSS3 - Cascade Style Sheets REFERENCE GUIDE
Guía basada en la documentación que ofrece [W3Schools](http://www.w3schools.com/css) sobre las hojas de estilo en cascada.  

## Index
  - [Posicionamiento](#Position)
  - 

### Introducción
Para ubicar los estilos, existen tres formas:  

Forma | Estilo | Ejemplo  
--|---|--  
En línea | En cada elemento html |  ````<p style="color: red"></p>````  
Interno | En las etiquetas ````<style></style>```` del head | ````<head><style> * { color: red; } </style></head>````  
Externo | Link enlazando al documento externo | ````<head><link rel="stylesheet" type="text/css" href="mystyle.css"></head>````  
  
Se suele utilizar la forma externalizada, es la forma de dividir lo máximo posible el código html del css.  
  
#### Sintaxis:
La sintaxis para definir elementos css, es:  
  **nombre_elemento { atributo: propiedades; }**  
Si usaramos los tres estilos, el orden por el que prevalecerían los cambios sería: **en linea, interno, externo, y el explorador**.  
`/* ejemplo de comentarios */` - Definición de comentarios.  

#### Identificadores
Se puede hacer referencia a los elementos html id y class mediante dos elementos: **. para class y # para id**.  
*Ejemplo: .nomclass { color: red }*  

#### Colores:
Existen tres formas de definir los colores en CSS:  

Forma | Ejemplo  
--|---|--  
Nombre válido | `red, black, white, gray`  
valor RGB | `rgb(255, 0, 0)`  
valor Hexadecimal | `#FAFAFA`  

#### Unidades de medida:
##### Unidades Absolutas:
Su valor no depende de otro de referencia.

Unidad | Definición  
--|---|--  
in | pulgadas  
cm | centímetros  
mm | milímetros  
pt | puntos  
pc | picas  
  
##### Unidades relativas:
Su valor depende de otro absoluto.  

Unidad | Definición  
--|---|--  
em | respectiva al tamaño por defecto de las letras  
ex | respectiva a la altura de la letra `x` del tipo y tamaño de la letra  
px | píxeles, relativa respecto a la resolución del monitor  
  
### Background - Fondos de la Página
```` css
  *{
    background-color: /*color válido explicado antes*/;
    background-image: url("ruta/imagen.png");
    background-repeat: [repeat-x | repeat-y | no-repeat];
    background-attachment: scroll | fixed ;
    background-position: left top | left center | left bottom | right top | right center | right bottom |
    center top | center center | center bottom;
  }
````
Además podrán agruparse en una misma propiedad, `background:` en la que asignarle varios atributos.  

`background-color` establece un color de fondo según las formas explicadas antes.  
`background-image` establece como fondo una imagen según la ruta elegida.  
`background-repeat` establece la forma en la que se repetirá el fondo.  
**repeat-x** repite en horizontal la imagen.  
**repeat-y** repite en vertical la imagen.  
 **no-repeat** no repite la imagen.  
 `background-attachment` Define si el fondo será dinámico con la página.  
 **scroll** se moverá al hacer scrolling en la página.  
**fixed** se quedará fijo y solo se moverá el contenido de la página.  

### Border - Bordes del contenido

```` css
  *{
    border-style: dotted | dashed | solid | double | groove | ridge | inset | outset | none | hidden;
    border-width: 5px;
    border-color: red;
    border-right | border-top | border-bottom | border-left: solid red 1px;
    border-radius: 10px;
  }
````
Además se puede agrupar en una misma propiedad, `border:` en la que asignarle varios atributos.  
Si quisiéramos agregar un estilo distinto para cada lado del borde, hay distintas formas:  
Cuatro atributos: **arriba, derecha, izquierda, abajo**. *Ejemplo: border: dotted dashed solid inset red 2px;*  
Tres atributos: **arriba, derecha+izquierda, abajo**. *Ejemplo: border: dotted solid dotted;*  
Dos atributos: **arriba+abajo, izquierda+derecha**. *Ejemplo: border: dotted solid;*  
Un atributo: **todos**. *Ejemplo: border: dotted*.  
  
`border-style` asigna un estilo de borde.  
`border-width` asigna un grosor al borde.  
`border-color` asigna un color al borde.  
`border-radius` establece un borde redondeado para las esquinas del borde, pues por defecto establece un rectángulo perfecto.  
`border-right | border-top | border-bottom | border-left` establece un estilo para el borde derecho, superior, inferior o izquierdo.  

### Margin - Márgenes
```` css
  *{
    margin: 10px 10px | auto;
    margin-left: 10px;
    margin-right: 10px;
    margin-top: 10px;
    margin-bottom: 10px;
  }
````
`margin` asigna un margen externo, podemos asignarlo simplemente con las propiedades añadiendo cuatro, tres, dos o un atributo con la simple etiqueta o definirlos de forma individual.  
Admite valores negativos, porcentajes (medida relativa que escala en relación a la resolución del monitor) e incluso la ausencia de borde.  

### Padding - Margen interno/relleno
```` css
*{
  padding: 10px;
  padding-left:10px;
  padding-top:10px;
  padding-bottom:10px;
  padding-right:10px;
}
````
`padding` corresponde al relleno, al margen interno del elemento, podemos asignarlo al igual que el margen con más de un atributo mediante esta etiqueta o definirlos de forma individual. Admite porcentajes.  

### Height x Width - Altura x Anchura
```` css
  *{
    height: 500px;
    max-height: 500px;
    max-width: 500px;
    min-height: 200px;
    min-width: 500px;
    width: 500px;
   }
````
Tanto `width` como `height` no establecen un margen o un padding, solo establecen un tamaño al contenedor o elemento al que hacen referencia. Admite cualquier unidad de medida y porcentajes.  

Al agregar un `max-width` establece la máxima anchura del elemento o contenedor.  
Esto quiere decir que al redimensionar el explorador, este elemento no variará su tamaño.  
Lo equivalente a la altura sería `max-height` siendo justo lo contrario con `min-width` y `min-width`.  

### Box Model - modelo de cajas
El modelo de cajas es el método por el cual diferenciamos los elementos y los disponemos con css. Se compone de varios niveles:
`outline - margin - border - padding - contenido`.  

### Outline - Contorno
```` css
  *{
    outline: inherit;
    outline-color: blue;
    outline-style:  dotted | dashed | solid | double | groove | ridge |
    inset | outset | none | hidden;
    outline-offset: 10px;
    outline-width: thin |thick | medium;
   }
````
`outline` establece un contorno por fuera del margen del elemento al que hacen referencia. Es una forma de hacer que el elemento al que hacen referencia *destaque* de alguna forma.  
La principal diferencia del outline con border es que el primero no forma parte del elemento en sí, puesto que no afecta a sus dimensiones.
**outline-offset** establece un espacio entre el outline y el borde.  

### Text - Textos
```` css
  *{
      color: /*color válido*/;
      text-align: center | left | right | justify;
      text-decoration: overline | underline | line-through;
      text-transform: capitalize | lowercase | uppercase | full-width;
      text-shadow: 2px 2px 4px black;
      text-indent: 50px;
      letter-spacing: 3px;
      line-height: 10px;
      direction: ltr | rtl;
      white-space: normal | pre-line | pre-wrap | nowrap;
      word-break: normal | break-all | keep-all;
      word-spacing: 10px;
      vertical-align: baseline | length(50px) | sub | super | top | text-top |
      middle | bottom | text-bottom;
   }
````
`text-align` permite alinear el texto según se elija, centrado, justificado a la derecha o izquierda.  
`text-decoration` permite decorar el texto con una linea superior, una linea de subrayado o una linea de tachado.  
`text-transform` permite un cambio en el texto, capitalizado, todo a minúscula, todo a mayúscula o que compartan el mismo tamaño cada letra.  
`text-shadow`: Establece una sombra para el texto, con valores positivos, *el ejemplo correspondería al margen inferior-derecha el difuminado (en píxeles) y el color*.  
`text-indent` Establece la sangría de la primera línea del párrafo.  
`letter-spacing` Establece el espaciado entre letras.  
`line-height` Establece el espacio del interlineado.  
`direction` Establece la dirección del texto para determinados idiomas.  
Sus atributos: **ltr** izq hacia der. **rtl** der hacia izq.  
`white-space` Establece el espacio superior al texto.  
`word-break` Establece si al final del texto en el límite izquierdo se separan las palabras rompiendo la palabra o manteniendo juntas las letras antes del salto de línea.  
**break-all** romper en cualquier momento la palabra.  
**keep-all** mantener las palabras juntas previo al salto de línea.  
`word-spacing` Establece el espacio entre las palabras.  
`vertical-align` Establece un margen vertical al texto.  

----

### Font - Fuentes
```` css
  @font-face {
    font-family: 'name';
    src: url('ruta o enlace');
  }

  *{
    font-family: serif, sans-serif, monospace;
    font-style: italic | normal |  oblique;
    font-size: 2.0em;
    font-weight: bold | bolder | lighter;
    font-variant: normal | small-caps;
 }
````

Podemos encontrar dos tipos de fuentes:  
  - por familia genérica: **serif, sans-serif, monospace**
  - por una fuente concreta: **georgia, arial, courier new**

`font-family` Establece el tipo de familia de fuentes que se usará en el texto, se pueden añadir varias unidas por **,**. Si la fuente tiene espacios, irá entre comillas **"**.  
`font-style` Establece el texto como oblicuo o cursivo.  
`font-size` Establece el tamaño de la fuente, tanto en texto como en fuente se pueden usar la medida relativa **em**.  
`font-weight` Establece el grosor de la tipografía. **bold** sería negrita, y **lighter** mas clara.  
`font-variant` Establece que todo el texto sea en mayúsculas aunque diferenciará en tamaño las letras que correspondan a las mayúsculas.  

`@font-face` establece una ruta para agregar familias de fuentes ajenas a las predefinidas, con **font-family** elegimos el nombre asignado para llamarle después, y con **src: url()** la ruta del archivo que contiene la fuente.  

### Icons - Iconos
```` html
<!DOCTYPE html>
<html>
<head>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.6.3/css/font-awesome.min.css">
</head>
<body>
  <i class="fa fa-cloud"></i> <br/> <i class="fa fa-heart"></i>
</body>
</html>
````
Existe la posibilidad de agregar iconos mediante las etiquetas `<i> o <span>`, con enlaces a librerías de iconos mediante los cuales basta con agregar clases a las etiquetas ya mencionadas. *(Un ejemplo serían los octicons de GitHub o los iconos de bootstrap)*.  

### Links - Enlaces
````css
a:link{ text-decoration: none; }
a:hover{ text-decoration: underline; }
a:active{ text-decoration: underline;}
a:visited{ color: black;}
````

Para agregar estilos a un enlace, se tendrá que hacer referencia a los estados por los que pasa cada uno de estos.  
`:link` es el enlace sin propiciar ningún evento en él.  
`:hover` cuando el cursor está encima.  
`:active` mientras se está pulsando el enlace.  
`:visited` enlace ya visitado previamente.  

### Lists - Listados
````css
  *{
    list-style-type: circle | disc | square | lower-alpha | lower-greek | lower-latin | upper-alpha | none;
    list-style-image: url('image.png');
    list-style-position: inside | outside;
  }
````
`list-style-type` Elige el tipo de indentificación para los elementos de la lista, algunos de los más usados son los que aparecen en el ejemplo.  
`list-style-image` Selecciona una imagen para que haga de identificador de cada elemento de la lista.  
`list-style-position` Establece la sangría del listado. **inside** establecerá mayor sangría que **outside**.  

### Tables - Tablas
```` css
*{
  border: /*propiedades ya vistas sobre los bordes*/
  border-collapse: collapse | separate;
  caption-side: bottom | top;
  empty-cells: hide | show;
  table-layout: auto | fixed;
  text-align: /*visto previamente*/;
  width: auto;
  height: auto;
}
tr:nth-child(even | odd){
  background-color: lightgray;
}
````
Por defecto las tablas tienen dos bordes, uno que contiene la tabla y otro interno para cada celda.  
`border-collapse` Establece la unión de los dos bordes que se agregan por defecto de la tabla.  
`caption-side` Establece la ubicación del `caption` o título de la tabla.  
`empty-cells` Establece la visibilidad de una celda vacía. De dejarlas ocultas, respetaría el hueco de estas.  
`table-layout` Establece que el texto dependerá del tamaño de la celda.  
El atributo **:nth-child(even | odd)** sirve para diferenciar las filas pares o impares, en caso de querer diferenciar unas filas de otras.  
Si quisieramos hacer una tabla responsive tendríamos que agregar a la etiqueta `<table>` o al `<div>` contenedor el estilo **overflow-x: auto**.   Eso agregaría una barra de desplazamiento horizontal bajo la tabla.  

### Display, Visibility & Opacity
````css
*{
  display: block | inline | flex | grid | inline-flex;
  visibility: visible | hidden;

  opacity: 0.5;
  filter: alpha(opacity=50);
}
````
La propiedad `display` cambia la forma en la que se dispone el elemento al que hace referencia, en **block** significa que no admite nada a su izquierda o derecha, **inline** que forma parte de la línea con otros elementos. **flex** permite colocar los elementos de una página para que se comporten de forma predecible cuando el diseño de la página debe acomodarse a diferentes tamaños de pantalla y diferentes dispositivos.  
La propiedad `visibility` establece si un elemento es visible o no.  
La propiedad `opacity` establece la transparencia del elemento al que hacen referencia. El 0% de transparencia sería 1. El 50% sería 0.5. `filter` es el equivalente para algunos exploradores.  

## Position - Posicionamiento
```` css
*{
  position: static | relative | fixed | absolute;
  top: auto;
  left: auto;
  right: auto;
  bottom: auto;
}
````
`position` establece el tipo de posicionamiento que tendrá en relación a la página.  
**static** define que el elemento al que hace referencia está pùesto según el flujo normal de la página.  
**relative** define que el elemento tendrá cierta dependencia de posición en función del contenido de la izquierda y derecha. Se necesita una posición relativa para que funcione el posicionamiento **top, left, bottom, right**.  
