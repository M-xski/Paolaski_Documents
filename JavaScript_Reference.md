###### *Kurumi · Studio (cc) 2016*

# JavaScript: Reference Guide
Guía basada en el contenido ofrecido por [W3Schools](http://www.w3schools.com/js/default.asp) sobre JavaScript.

### Herramientas Online
- [JavaScript CheatSheet - By EMEZETA](http://www.emezeta.com/doc/javascript-cheatsheet/?amount=0&cmd=_donations&hosted_button_id=6XU7D2MX6ZJCA&business=joseromanhernandez%40gmail.com&return=http%3A%2F%2Fwww.emezeta.com%2Fdoc%2Fjavascript-cheatsheet%2Findex.php&item_name=Javascript+Cheatsheet+%28Donation%29&currency_code=EUR)
- [JSBin - A collaborative JS debugging](https://jsbin.com/?html,js,output)

## Index
- [Introducción](#introducción)
- [Ubicación](#ubicación)
- [Tipos de salida](#tipos-de-salida)
- [Sintaxis](#sintaxis)
- [Operadores](#operadores)
- [Variables](#variables)
- [Tipos de datos](#tipos-de-datos)
- [Funciones](#funciones)
- [Eventos](#eventos)
- [Objetos](#objetos)
- [Strings](#strings)  
 - [Métodos de los strings](#métodos-de-los-strings)
- [Number](#number)  
 - [Métodos de number](#métodos-de-number)  

## Introducción
JavaScript puede cambiar el contenido de los documentos HTML, encontramos los siguientes métodos:

``` html
<p id="demo">JavaScript can change HTML content.</p>
<button type="button" onclick="document.getElementById('demo').innerHTML='Hello!'">Click Me!</button>
```
*En el ejemplo, al seleccionar el botón cambiará un texto por el introducido con innerHTML.*

Con el método `.getElementById()` busca cualquier id que coincida con el id introducido en el método, y con el método `.getElementById().innerHTML` cambiará el contenido del elemento a buscar por id.

``` html
<button onclick="document.getElementById('mimg').src='pic1.gif'">Turn on the light</button>
  <img id="myImage" src="pic_bulboff.gif" style="width:100px">
<button onclick="document.getElementById('mimg').src='pic2.gif'">Turn off the light</button>
```
*En el ejemplo: segun seleccionemos un botón u otro cambiará una imagen por otra.*

Si quisiéramos cambiar los atributos de algun elemento de HTML, tendríamos que poner `document.getElementById('id').atributo="cambios"`.

``` html
<p id="demo">JavaScript can change the style of an HTML element.</p>
<button type="button" onclick="document.getElementById('demo').style.color='red'">Click Me!</button>
```
*En el ejemplo: al seleccionar el botón cambiará el texto de color.*

Si quisiéramos cambiar algo del estilo (CSS) sería con el método `document.getElementById('id').style.css_elementos='cambios'`.

``` html
<p id="demo">JavaScript can hide HTML elements.</p>
<button type="button" onclick="document.getElementById('demo').style.display='none'">Click Me!</button>
<button type="button" onclick="document.getElementById('demo').style.display='block'">Click Me!</button>
```
*En el ejemplo: el primer botón hará "desaparecer" el texto, y el segundo lo mostrará.*

Con el atributo de CSS display, podríamos hacer desaparecer elementos o hacerlos aparecer.

## Ubicación
Al igual que CSS, JavaScript tiene tres formas de ubicar su código:

- **En el body**:
``` html
<body>
  <script>
      document.getElementById("demo").innerHTML = "My First JavaScript";
  </script>
</body>
```

- **En el head**:
``` html
<head>
  <script type="text/javascript">
    function myFunction(){
      window.alert("hello world!");
    }
  </script>
</head>
<body>
  <button type="button" onclick="myFunction()">Try it</button>
</body>
```
*Al seleccionar el botón, este mostrará una ventana emergente con un mensaje.*

- **En un documento externo**:
``` html
  <body>
    <script src="myScript.js"></script>
  </body>
```

## Tipos de salida
Si quisiéramos mostrar datos, tenemos cuatro formas distintas:

Forma | Descripción  
------|--------------  
`window.alert()` | Creará una ventana emergente mostrando lo que se introduzca dentro del paréntesis.  
`document.write()` | Creará un texto en el que mostrará el contenido del paréntesis.  
`document.getElementById("id_elemento").innerHTML = resultado` | Cambiará el elemento que tenga el mismo id por el *resultado*.  
`console.log()` | En este caso el resultado del paréntesis no se mostrará en la vista de usuario si no que será mostrado en la consola del explorador **`(F12)`**.  

## Sintaxis
`//Los comentarios unilínea se escriben con // al principio de la frase.`
`/* Los comentarios
  multiínea se escriben con /* y */. */`

JavaScript es *case-sensitive* es decir, diferencia mayúsculas de minúsculas.
JavaScript ignora los múltiples espacios.
No se declara el tipo de variable pero sí se identifican. *Ejemplo:* `var x = 5;`.
Los string pueden definirse con `"comillas dobles"` o `'comillas'`.

### Operadores
Los operadores existentes: `+ - / * ++ --`.

### Variables
Para dar un nombre a las variables se recomida el método **under_score** o el método **camelCase**.

### Tipos de datos
Número: `var length = 16;`
String: `var lastName = "Johnson";`
Array: `var cars = ["Saab", "Volvo", "BMW"];`
Objetos: `var x = {firstName:"John", lastName:"Doe"};`

## Funciones
Las funciones son bloques de código que devuelven un resultado. Se utilizan cuando ocurre un evento (click de un botón, por ejemplo), se invoca algo, o se autoinvoca. Si al final de la función está el **return**, la función dará su final ahí.
``` javascript
function name(parameter1, parameter2, parameter3) {
    code to be executed;
    [return] something;
}
```

## Objetos
``` javascript
  var person = {
    firstName:"John",
    lastName:"Doe",
    age:50,
    eyeColor:"blue"};
```

## Eventos
Son reacciones que ocurren en el documento HTML al hacer alguna acción. Encontramos distintos eventos:

Evento | Descripcion  
-------|------------  
`onchange` | Cuando un elemento HTML ha sido cambiado  
`onclick` | Cuando el usuario selecciona algún elemento *(pulsar un botón, por ejemplo)*  
`onmouseover` | Cuando el cursor pasa por encima del elemento  
`onmouseout` | Cuando el cursor deja de estar encima del elemento  
`onkeydown` | Cuando el usuario pulsa una tecla del teclado  
`onload` | Cuando carga una página  

```html
<button onclick='document.getElementById("demo").innerHTML=Date()'>The time is?</button>
```
*Ejemplo: al hacer click en el botón mostrará la fecha*.

## Strings
Los strings son cadenas de carácteres, se definen entre dobles comillas o comillas como ya se ha mencionado.
``` javascript
var ejemplo = 'cadena';
var cita = "Le dijo que se llamaba: 'John'";
var txt = "ABCDEFGHIKLMNOPQRSTUVWXYZ";
var sln = txt.length;
```
Además se puede entrecomillar dentro de un string situando comillas simples dentro del string, será detectado como carácter.
Para acceder a toda la cadena de texto de un elemento se utiliza `.length`.

Existe el carácter de escape `\` en los string que sirven para determinados objetivos:

Código | Definición  
-------|-----------  
`\'` | comilla simple  
`\"` | doble comillas  
`\\` | barra invertida  
`\n` | nueva línea  
`\r` | retorno de carro  
`\t` | tabulador  
`\b` | espacio  
`\f` | salto de línea  

### Métodos de los Strings
método | descripción  
-------|------------  
`indexOf()`            |    Devuelve la primera posición del primer carácter del texto pasado por parámetro.  
`lastIndexOf()`        |    Devuelve la última posicón del primer carácter del texto pasado por parámetro.  
`search()`             |    Busca una cadena que coincida con el string pasado por parámetro, devuelve su posición.  
`slice(start, end)`    |    Extrae la cadena comprendida entre las posiciones que se le pasan por parámetro. Si se le pasan valores negativos, este comienza por el final.  
`split("-")`           |    Devuelve la cadena dividida cada carácter por el elemento pasado por parámetros.  
`substr(start, end)`   |    Es similar a `slice()`, pero no admite valores negativos, y el segundo valor establece el final del string extraído.  
`replace("valueA", "valueB")` | Sustituye algún elemento del string que coincida con el primer valor por el segundo valor pasado por parámetro.  
`toUpperCase()`       |    Convierte la cadena de texto en mayúsculas.  
`toLowerCase()`       |    Convierte la cadena de texto en minúsculas.  
`concat()`            |    Une dos cadenas, equivalente a "+" de los strings.  
`charAt(position)`    |    Devuelve el carácter de la posición pasada por parámetro.
`charCodeAt(position)`|    Devuelve el carácter unicode del carácter al que hace referencia.  
`link()`              |    Devuelve una cadena como link.  
 
## Number 
La declaración de los number puede ser entero, decimal, alguna operación matemática, hexadecimal, etc...  
*Si un resultado devuelve NaN, significa not a number, es decir, da un resultado con un valor no numérico.*  

Existe la función `isNaN("valor")` devolverá el valor pasado por parámetro en caso de darse como resultado NaN.  
Existe la posibilidad de definir number como objeto. Ejemplo: `var y = new Number(500);`  

### Métodos de Number
  método             |  descripción   
---------------------|-----------------------------------------------  
`toString()`         |  Convierte un number en una cadena de texto - string  
`toExponential(num)` |  Devuelve una cadena, con un número redondeado y escribir usando la notación exponencial.  
`toFixed()`



