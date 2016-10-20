###### *Paula Pérez Tafalla - 2º Desarrollo de Aplicaciones Web - Diseño de Interfaces Web - Curso 2016/17*

## Guía HTML5: HyperText Markup Language
Guía de referencia de HTML5 basada en la documentación de [W3Schools](http://www.w3schools.com/html/default.asp)

## Herramientas online
- [HTML5 Cheatsheet - By EMEZETA](http://i.emezeta.com/weblog/html5-cheatsheet/html5-cheatsheet-emezeta.pdf)

## Index
- [Head](#head)
- [Body](#body)
- [Identificadores](#identificadores)
- [Elementos del texto](#elementos-del-texto)
- [Tablas](#tablas)
- [Listas](#listas)
- [iFrames](#iframes)
- [Secciones](#seciones-html5)
- [Formularios](#formularios)
- [Contenido multimedia](#contenido-multimedia)

----

``` html
<!DOCTYPE html>
  <html lang="es-ES">
    <head>
      <!-- Comentarios -->
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta name="author" content="Paula Perez Tafalla">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <base href="ruta" target="blank_ parent_ self_ top_">
      <title>Título del Documento</title>
      <link hreflang="en" rel="stylesheet" type="text/css" href="theme.css">
      <script></script>
      <style></style>
      <noscript></noscript>
    </head>
    <body>
    </body>
  </html>
```

**`<!doctype html>`** Define el documento HTML, solo se abre esta etiqueta.  
**`<html>`** Abre el documento de html, dentro de estas etiquetas irá todo el documento, además con el atributo *lang* defines el idioma en el que se escribe.

### Head
La etiqueta `<head>` contendrá información de la página.
**`<meta>`** Define metadatos para la página.  
Los atributos que puede tener son:  
  **charset**: Define el tipo de codificación, por ejemplo: UTF-8.  
  **name**: Define un título, un nombre, para el contenido de los metadatos.  
  **content**: Define el contenido de los metadatos.  

**`<base>`** Establece la ruta de todos los enlaces de la página.  
Los atributos que puede tener son:    
  **target** dirá si se abre en una pestaña nueva, en la misma, en el padre, etc.  
  **href** Indicará la ruta.  
  **http-equiv** Se utiliza para darle información al http, entre sus *content* más frecuentes está *refresh* y el content tendrá el      intervalo de tiempo.

**`<link>`**  Establece enlaces para relacionar el documento con otros archivos, por ejemplo el documento *externo* de css.  
Los atributos que puede tener son:  
 **rel** Relación que tiene con el documento.  
 **type** Tipo de documento.  
 **hreflang** Idioma del archivo con el que se está enlazando.

**`<title>`** Establece el título de la página (será visible en las pestañas del navegador).  

**`<script>`** Define un script de JavaScript.  
**`<style>`** Define el estilo de la página.  
**`<noscript>`** Mensaje por defecto si no funciona el javascript en el explorador.

### Body  
La etiqueta `<body>` define todo el contenido de la página y que además será visible por el usuario desde el explorador.  

### Identificadores
Los identificadores son atributos que permiten identificar los elementos para posteriormente ser utilizados por el servidor, por css, por javascript, etc.  
 El atributo **id**, asigna un identificador.  
 El atributo **class**, asigna una clase.  

Estos identificadores pueden asignarse en cualquier elemento, pero además existen etiquetas que contienen elementos, una forma de agruparlos, que no es visualmente perceptible por el explorador.  
 `<div></div>` Establece una agrupación de contenido, no es visible por el explorador.  
 `<span></span>` Sirve para lo mismo que la etiqueta anterior, con la diferencia de que al cerrar su etiqueta no agregará un salto de línea después.  

### Elementos del texto
`<h1></h1>` hasta `<h6></h6>` Define el encabezado de la página de mayor a menor tamaño.  
`<p></p>` Define un párrafo.  
`<br/>` Define un salto de línea.
`<hr/>` Define un salto de línea con una línea horizontal divisoria.  
`<pre></pre>` Respeta los saltos de línea que sean aplicados dentro del párrafo.

`<strong></strong>` Texto importante - negrita.  
`<em></em>` Texto enfatizado - cursiva.  
`<mark></mark>` Texto marcado - subrayado con color.  
`<small></small>` Texto pequeño - Estilo copyright.  
`<del></del>` Texto eliminado - tachado.  
`<ins></ins>` Texto insertado - subrayado.  
`<sub></sub>` Texto subscript  
`<sup></sup>` Texto superscript  

`<q></q>` Define una cita para el texto, normalmente de una frase o dos, es decir poco texto.  
`<blockquote cite=""></blockquote>` Cita para un texto, el atributo cite debe tener la url de donde obtienes el texto.  
`<abbr title="World Health Organization">WHO</abbr>`  Define abreviación, el atributo title tendrá el significado de las siglas.  
`<adress></adress>` Define una dirección de correo postal.  
`<cite></cite>` Define el nombre de algún trabajo profesional (obra de arte, por ejemplo).

`<code></code>` Define código de programación, respetando el texto con una fuente y tamaño determinados.  
`<kbd></kbd>` Define textos que significan entradas del teclado.  
`<samp></samp>` Define las salidas de algun programa.  
`<var></var>` Define variables, como por ejemplo e = mc2.  
### Enlaces
`<a href="url" target="_blank _top _ self _parent">click aquí</a>` Define un enlace, el atributo **href** para señalar la ruta a la que irá o el URL y dentro de las etiquetas irá el texto que se mostrará por el explorador.  
`<img src="pic_mountain.jpg" alt="Mountain View">` Define una imagen, el **src** señala el nombre del archivo, ruta, o url de donde procede. **Alt** significa alternativo, y es un texto de accesibilidad para aplicaciones que leen el contenido de la web.  

### Tablas  
``` html
  <table>
     <caption>Establece un título para la tabla</caption>
      <tr>
        <th>  </th>
        <td>  </td colspan="1">
        <td>  </td rowspan="2">
      </tr>
 </table>
```
`<table></table>` Define la tabla.  
`<caption></caption>` Define un título para la tabla.  
`<tr></tr>` Define la fila de la tabla.  
`<th></th>` Define el encabezado de la tabla.  
`<td></td>` Define la celda de cada columna de la tabla.  
 El atributo **colspan** unirá las celdas hacia la derecha, es decir, las columnas.  
 El atributo **rowspan** unirá las celdas hacia abajo, es decir, las filas.  

### Listas  
Las listas son elementos anidables, es decir, se pueden crear listados dentro de otros. Encontramos tres tipos de listados:  

- Listas ordenadas:
``` html
  <ol type="I">
    <li>  </li>
    <li>
      <ol>
        <li>  </li>
        <li>  </li>
      </ol>
    </li>
    <li>  </li>
  </ol>
```
*En el ejemplo, listado anidado de dos listas ordenadas (ol).*  

`<ol></ol>` Define la lista ordenada.  
  El atributo **type** define el tipo de numeración que llevará, se podrá elegir entre **A, a, 1, I, i**.  
`<li></li>` Define cada elemento del listado.  

- Listas desordenadas:
``` html
    <ul>
      <li>  </li>
      <li>  </li>
    </ul>
```
`<ul></ul>` Define el listado desordenado.  

- Listado de definición:
``` html
  <dl>
      <dt>Coffee</dt>
      <dd>- black hot drink</dd>
  </dl>
```

`<dl></dl>` Define la lista de definición.  
`<dt></dt>` Define el elemento que se desrcibirá en la etiqueta `<dd></dd>`.  
`<dd></dd>` Etiqueta que establece la definición del `<dt></dt>` superior.

### iFrames  
Los iframes son como *"ventanas"* que se abren dentro de una pestaña, sirven para enlazar con otros documentos y mostrar su contenido, u contenidos de otras web.  

``` html
  <iframe src="demo_iframe.htm" name="iframe_a" height="200" width="300">
    Tu explorador no soporta iFrames.
  </iframe>
  <a href="http://www.w3schools.com" target="iframe_a">W3Schools.com</a>
```  
El atributo **src** sirve para poner el nombre de la web o documento que mostrará, el **name** será un identificador, **height** anchura y **width** altura en píxeles.  

El enlace que se quiera a enlazar con el iframe para abrirlo en este, tendrá que tener un **target**, con el mismo contenido que el identificador-nombre del iframe.  

### Secciones HTML5
``` html
  <header>  </header>
  <nav>     </nav>
  <section> </section>
  <article> </article>
  <aside>   </aside>
  <footer>  </footer>
  <details> </details>
  <summary> </summary>
```  
Las secciones son etiquetas introducidas en HTML5, las cuales definen elementos de la página pero no son perceptibles por el explorador.   
`<header>`Define la cabecera de la página.  
`<nav>`  Define el menú navegable por la página.  
`<section>` Define una sección (izq).  
`<article>` Define una sección independiente (izq-abajo de section).  
`<aside>` Contenido lateral de la página.  
`<details>` Define detalles adicionales.  
`<summary>` Define el encabezado para la etiqueta details.  

### Formularios
``` html
  <form action="GET o POST">
    <fieldset>
      <legend>Título del fieldset</legend>
        <label for="name"></label>
        <input type="text">
        <input type="radio" name="gender" value="male" checked>
        <input type="submit" formmethod="post" formaction="demo_post.asp" formtarget="_blank">
        <input type="file">
        <input type="number" name="quantity" min="1" max="5">
    </fieldset>
  </form>
```
*Todos los elementos de los formularios son elementos en línea.*  
`<form action="GET o POST"></form>` Define el formulario, el atributo **action** determinará si se muestran datos sobre el servidor o no en la URL, POST siempre que comprometa datos privados debe usarse.  
`<fieldset></fieldset>` Es una agrupación de una parte del formulario, será rodeado por un margen sólido y simple.  
`<legend></legend>` Define un título para el formulario que irá ubicado en el margen del fieldset.  
`<label for="name"></label>` Es el texto que complementa al formulario, por ejemplo nombre seguido de su input-text para saber que se refiere al nombre en ese input.  

`<input type="text">` Entrada de teclado de texto.  
`<input type="radio" name="gender" value="male" checked>` Botón de selección, si hay varios para elegir uno, deberán tener el mismo nombre con distinto valor, se usa checked para elegir el que será seleccionado por defecto.  
`<input type="submit" formmethod="post" formaction="demo_post.asp" formtarget="_blank">` Botón de subida/finalizado.  
`<input type="file">` Botón de selección de archivo.  
`<input type="number" name="quantity" min="1" max="5">` Introduce un numero **min**, el minimo valor posible y **max** el máximo.

```html
<select name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select>

<textarea name="message" rows="10" cols="30"> The cat was playing in the garden.
</textarea>

<button type="button">Click Me!</button>
```

`<select></select>` Cuadro de selección, debe ponerse con el atributo **name**, para posteriormente dar los datos al servidor.  
`<option value=""></option>` Dentro del cuadro de selección se abrirá un desplegable con las opciones que se utilicen con option y su atributo **value**, se pueden añadir tantos como sea necesario.  

`<textarea name="message" rows="10" cols="30"></textarea>` Cuadro de texto de comentarios, rows y cols establece su tamaño en px.  
`<button type="button"></button>` Establece un botón.  

``` html
<input list="browsers" name="browser">
<datalist id="browsers">
  <option value="Internet Explorer">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>

<keygen name="security">

<input type="range"  id="a" name="a" value="50">100 +
<input type="number" id="b" name="b" value="50">  =
<output name="x" for="a b"></output>
</form>
```

`<input list="browsers" name="browser">` Establece un **datalist**, deberá ser introducido por el imput el tipo de listado que se va a dar, son elementos prefijados.  
`<datalist id="browsers">` Define el listado de valores.  
`<option value="Internet Explorer">` Define las opciones para elegir.  

`<keygen name="security">` Define la seguridad para el usuario, normalmente existen dos contraseñas, la del usuario y otra para el servidor, la pública, puede ser usada para validar el user.
`<output name="x" for="a b"></output>` Establece la salida de una operación matemática.

### Atributos para el formulario
*Para input:*  
  **password:** contraseña, se muestra con `*****`  
  **checkbox:** cuadrado de selección con un tick  
  **color:** menú para elegir un color  
  **email:** correo  
  **range:** rueda para elegir un rango
  **search:** búsqueda  
  **tel:** teléfono  
  **time:** hora hh:mm  
  **url:** link  
  **readonly:** valor de solo lectura.  
  **disabled**: desactivado  
  **size:** tamaño de los input  
  **maxlength:** maximo tamaño de carácteres  
  **autocomplete:** autocompletado  
  **novalidate:** no será enviado al procesarlo con el submit  
  **placeholder:** referencia visual para dentro de los input-text, desaparece al escribir.  
  **required:** requerido, obliga a rellenar el campo antes de enviar

*Para submit:*  
  **formaction:** establece el url del archivo que procesará el formulario  
  **formenctype:** - solo para POST- especifica el tipo de procesamiento  
  **formmethod:** GET O POST  
  **formtarget:** establece que se mostrará al finalizar el submit

**multiple:** para file,permite elegir varios archivos.  
**step:** para number, establece un valor para ir de x valor en x valor ej: de 3 en 3.  

### Contenido Multimedia
```html
  <audio src="" controls></audio>
```
Creará un reproductor por defecto con el audio que se elija por **src**, puede ser un url o la ruta del archivo.  Si se añade el atributo controls, añaderá un panel de pause-retroceder, etc. En caso de querer añadir varias pistas se usaria dentro de audio la etiqueta **`<source>`** como en el siguiente caso.

```html
<audio controls autoplay>
    <source src="horse.ogg" type="audio/ogg">
    <source src="horse2.ogg" type="audio/ogg">
    Tu explorador no soporta audio.
</audio>
```
El atributo **autoplay** dará comienzo a la canción según se abra la página.  

En el caso de video se define de la misma forma que audio:

```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English">
  Tu explorador no soporta video.
</video>
```
la etiqueta `<track>` significa añadir subtítulos al vídeo, se definen con **src** indicando la ruta o un url.  

```html
<object width="400" height="50" data="bookmark.swf"></object>
<embed width="400" height="50" src="bookmark.swf" type="">
```
El elemento **`<object>`** es soportado por todos los exploradores, y es utilizado para importar otros plugins ajenos, como un pdf o elemento flash.  
**`<embed>`** sirve para lo mismo, pero está dejando de usarse.  
