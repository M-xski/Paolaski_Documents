## S*tandard* Q*uery* L*anguage* :floppy_disk: `MySQL` 

> Notas de clase y basado en el tutorial de [W3Schools](https://www.w3schools.com/sql/) :heavy_minus_sign: Paula Pérez Tafalla | 2018 

SQL es el lenguaje estandar de almacenamiento, manipulación y recuperación de datos.

> La mayoría de programas de bases de datos SQL tienen sus propias extensiones además del estándar SQL. Para probar las consultas: [TryIt W3Schools](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all)



#### :black_circle: SYNTAX

La mayoría de acciones que necesitas hacer en una base de datos se realizan con declaraciones SQL.

```mysql
SELECT * FROM NombreTabla; /* Selecciona todos los campos de la tabla */ 
```

Las palabras clave **no son case sensitive** (es decir,`select` es lo mismo que `SELECT`). Para diferenciar las palabras clave, estas se escribirán en mayúsculas.  

Para realizar comentarios (anotaciones que no se ejecutarán cuando se compilen las búsquedas):

```mysql
 /* Comentario multilínea */		 -- Comentario unilínea
```

Estos se pueden combinar de forma que en mitad de una instrucción se puede comentar parte de la misma, o incluso continuar el comentario en la siguiente línea.  

Por otra parte algunos de los comandos más importantes de SQL son: 

| Comando           | Descripción                              |
| ----------------- | ---------------------------------------- |
| `SELECT`          | Extrae datos de una base de datos.       |
| `UPDATE`          | Actualiza datos de una base de datos.    |
| `DELETE`          | Elimina datos de una base de datos.      |
| `INSERT INTO`     | Inserta datos nuevos en una base de datos. |
| `CREATE DATABASE` | Crea una nueva base de datos.            |
| `ALTER DATABASE`  | Modifica la base de datos.               |
| `CREATE TABLE`    | Crea una nueva tabla.                    |
| `ALTER TABLE`     | Modifica una tabla.                      |
| `DROP TABLE`      | Elimina una tabla.                       |
| `CREATE INDEX`    | Crea un índice (búsqueda de clave)       |
| `DROP INDEX`      | Elimina un índice                        |



### ⚫️ Tipos de Datos

Se clasifican en tres grupos de tipo de datos: **texto, numérico y fecha**. En **negrita** se marcarán los más frecuentes. 



Tipos de datos de cadenas de **texto**:

| Tipo de dato                        | Descripción                              |
| ----------------------------------- | ---------------------------------------- |
| `CHAR(size)`, **` VARCHAR(size)`**  | Almacena una cadena de texto determinada, su máximo es de 255. VARCHAR se diferencia de CHAR en que si se exceden su máximo se convierte en TEXT. |
| `TINYTEXT`, **`TEXT`**,  `LONGTEXT` | Almacena un string cuyo máximo en el caso de TINYTEXT es de 255 carácteres. El máximo de TEXT es de 65,535 carácteres, y en el caso de LONGTEXT es de  4,294,967,295 carácteres. |
| `BLOB`,`MEDIUMBLOB`, `LONGBLOB`     | Almacena un BLOBs (Binary Large OBjects). Su máximo es de 65,535 bytes de datos. El MEDIUMBLOB almacena como máximo 16,777,215 bytes y LONGBLOB  4,294,967,295 bytes |
| ` ENUM(x,y,z,etc.)`, `SET`          | Un ENUM(), es una enumeración de posibles valores. Almacena un máximo de  65535 valores. SET() almacena un máximo de 64. |



**(*)** Tipo de datos de valores **numéricos**:

| Tipo de dato                             | Descripción                              |
| ---------------------------------------- | ---------------------------------------- |
| ` TINYINT(size)`, ` SMALLINT(size)`, `MEDIUMINT(size)`, **`INT(size)`**, `BIGINT()` | TINYINT:  -128 a 127 (normal), SMALLINT:  -32768 to 32767, MEDIUMINT:  -8388608 to 8388607, INT:  -2147483648 to 2147483647, BIGINT:  -9223372036854775808 to 9223372036854775807 |
| `FLOAT(size,d)`                          | Número pequeño con decimales. El máximo de decimales se especifica por parámetro. |
| **` DOUBLE(size,d)`**                    | Número grande con decimales. El máximo de decimales se especifica por parámetro. |
| **`DECIMAL(size,d)`**                    | Double almacenado como String            |

> **(*)** Hace referencia a su forma normal , si los valores numéricos están sin signo, tienen mayor valor máximo.



Tipo de datos relacionados con **fechas**:

| Tipo de dato   | Descripción                              |
| -------------- | ---------------------------------------- |
| ` DATE()`      | Fecha con formato  YYYY-MM-DD            |
| ` DATETIME()`  | Fecha con formato  YYYY-MM-DD HH:MI:SS   |
| ` TIMESTAMP()` | Fecha que se almacena como el número de segundos desde la época de Unix. El rango que soporta es de  '1970-01-01 00:00:01' UTC a '2038-01-09 03:14:07' UTC |
| `TIME()`       | Hora con formato  HH:MI:SS               |



### :black_circle: SELECT

La declaración `SELECT` se utiliza para extraer datos de una base de datos. Los datos se devuelven en una tabla de resultados. Su sintaxis es la siguiente:

```mysql
SELECT * FROM NombreTabla; 
SELECT CustomerName, City FROM Customers; /* Extraerá las dos columnas de la tabla Customers */
```

El `*` significa todas las columnas. La `,` adjunta columnas a mostrar.

La declaración `SELECT DISTINCT` se utiliza para devolver sólo los valores distintos. Dentro de una tabla, una columna puede contener valores duplicados y a veces sólo queremos listar los valores diferentes.

```mysql
SELECT Country FROM Customers; /*Listará todos los países de la tabla Customers*/
SELECT DISTINCT Country FROM Customers; /* Listará cada elemento una vez, omitiendo duplicados*/
SELECT COUNT(DISTINCT Country) FROM Customers; /* Sacará el número de países, sin repetición */
```

> La función`COUNT()` obtiene el número de registros que se le indique.



### :black_circle: LIMIT (SELECT TOP)

La cláusula `SELECT TOP` se utiliza para especificar un número de registros limitado a devolver. En MySQL se utiliza la cláusula `LIMIT`. Su sintaxis es la siguiente:

```mysql
SELECT nombreColumna1,nombreColumna2 FROM nombreTabla WHERE condicion1 LIMIT number;
```

Un ejemplo sería: 

```mysql
SELECT * FROM Customers LIMIT 3; /* Sacaría los 3 primeros registros de la búsqueda */
```





### :black_circle: SELECT INTO

La declaración `SELECT INTO` copia los datos de una tabla en una tabla nueva. Su sintaxis es la siguiente:

```mysql
SELECT * INTO nuevaTabla [IN otraBBDD] FROM tablaVieja WHERE condicion;
```

Además podemos copiar algunas columnas en una nueva tabla:

```
SELECT columna1, columna2, columna3 , ... INTO nuevaTabla 
[IN otraBBDD] FROM tablaVieja WHERE condicion;
```

> La tabla nueva se creará con los mismos nombres y tipos definidos en la tabla vieja. Puedes crear nuevas columnas usando la cláusula `AS`.

Algunos ejemplos serían:

```MYSQL
SELECT * INTO CustomersBackup2017 FROM Customers; -- Crea una copia backup de Clientes.
```

```mysql
SELECT CustomerName, ContactName INTO CustomersBackup2017 FROM Customers;
-- Copia solo las columnas seleccionadas dentro de una tabla nueva.
```

```mysql
SELECT * INTO CustomersGermany FROM Customers WHERE Country = 'Germany';
-- Copia solo los clientes alemanes en una tabla nueva.
```



### :black_circle: INSERT INTO SELECT

La declaración `INSERT INTO SELECT ` copia los datos de una tabla y los inserta en otra tabla. Requiere que los tipo de datos en la fuente y el objetivo coincidan. Los registros existentes en la tabla objetivo no son afectados. Su sintaxis es la siguiente:

```mysql
INSERT INTO tabla2 SELECT * FROM tabla1 WHERE condition;
-- Copia todas las columnas de una tabla en otra.
INSERT INTO tabla2 (columna1, columna2, columna3, ...) SELECT columna1, columna2, columna3, ...
FROM table1 WHERE condition;
-- Copia sólo algunas columnas de una tabla en otra.
```

Algunos ejemplos serían:

```mysql
INSERT INTO Customers (CustomerName, City, Country) SELECT SupplierName, City, Country FROM Suppliers;
-- Copia Vendedores en Clientes ( las columnas que no contienen datos, serán NULL).
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
SELECT SupplierName, ContactName, Address, City, PostalCode, Country FROM Suppliers;
-- Copia Vendedores en Clientes (con todas las columnas).
```





### :black_circle: WHERE

La cláusula `WHERE` se utiliza para filtrar resultados. Extraerá únicamente aquellos resultados que cumplan una condición específica. Su sintaxis: 

```mysql
SELECT Columna1, Columna2 FROM NombreTabla WHERE condicion; 
```

> La claúsula `WHERE` no se utiliza solo en `SELECT`, se puede utilizar en `UPDATE`, `DELETE`, etc...

Algunos ejemplos de la cláusula `WHERE`: 

```mysql
SELECT * FROM Customers WHERE Country='Mexico'; 
/* Mostará todas las columnas que cumplan con la condición de que el país sea 'Mexico' */ 
SELECT * FROM Customers WHERE CustomerID = 1;
```

> Los valores numéricos no se deben cerrar entre comillas.



### :black_circle: ALIAS

Los alias asignan a una tabla, columna o tabla un nombre temporal. Se utilizan para que los nombres de los resultados sean más indentificables. Estos nombres solo existen en la duración de la búsqueda. Para ello se utiliza `AS`. La sintaxis es la siguiente:

```mysql
SELECT nombreColumna AS aliasColumna FROM nombreTabla; /* Alias para Columna */
SELECT nombreColumna FROM nombreTabla AS aliasTabla; /* Alias para Tabla */
```



### :black_circle: Operadores

Los distintos operadores que encontramos en MySQL son `=` :heavy_minus_sign: `<>` :heavy_minus_sign: `>`  :heavy_minus_sign: `<` :heavy_minus_sign:  `>=`  :heavy_minus_sign: `<=` 

`BETWEEN`: Extraerá los registros determinados en un rango inclusivo, eso quiere decir que el valor de comienzo y final están incluídos en la búsqueda. Su sintaxis es la siguiente:

```mysql
SELECT nombreTabla FROM nombreTabla WHERE nombreColumna BETWEEN valor1 AND valor2;
```

Un ejemplo sería: 

```mysql
SELECT * FROM Products WHERE Price BETWEEN 10 AND 20;
/* Mostrará los productos cuyo precio esté entre 10 y 20 */ 
```

`LIKE`: Busca por un patrón, **siempre con cadenas de texto**. Existen dos comodines para representar unos patrones de búsqueda, que se pueden combinar, además puedes combinar varias condiciones usando `AND` u `OR`.

- `%` significa cero, uno o múltiples carácteres.
- `_` significa un único carácter.

Su sintaxis es la siguiente:

```mysql
SELECT columna1, columna2 ... FROM nombreTabla WHERE columnaN LIKE patronBusqueda;
```

Unos ejemplos serían:

```MYSQL
[...] WHERE CustomerName LIKE 'a%' /*Encontrará todos los valores que empiecen por 'a'*/
[...] WHERE CustomerName LIKE '%a' /* Encontrará todos los valores que terminen en 'a'*/
[...] WHERE CustomerName LIKE '_r%' 
/* Encontrará todos los valores que contengan una 'r' en segunda posición */
```

`IN`: Para especificar múltiples posible valores de una columna. Es una abreviatura de múltiples condiciones `OR`. Su sintaxis es la siguiente:

```mysql
SELECT nombreColumna FROM nombreTabla WHERE nombreColumna IN (valor1, valor2, ...); /* o */ 
SELECT nombreColumna FROM nombreTabla WHERE nombreColumna IN (SELECT [consulta2]);
```

Unos ejemplos serían: 

```mysql
SELECT * FROM Customers WHERE Country IN ('Germany', 'France', 'UK'); 
/* Mostrará todos los clientes cuyo país sea Alemania, Francia o UK */
SELECT * FROM Customers WHERE Country IN (SELECT Country FROM Suppliers);
/* Mostrará todos los clientes cuyo país sea el mismo que el de sus vendedores */
```



:black_circle: **Operadores AND, OR y NOT**

En la cláusula `WHERE` se pueden combinar los operadores `AND`, `OR`, o `NOT`. Los operadores`AND` y `OR` filtran los resultados basándose en más de una condición. Su sintaxis es la siguiente:

```mysql
SELECT * FROM NombreTabla WHERE Condicion1 AND Condicion2;
SELECT * FROM NombreTabla WHERE Condicion1 OR Condicion2;
SELECT * FROM NombreTabla WHERE NOT Condicion1;
```

El operador `AND` mostrará los resultados si **todas las condiciones** separadas por `AND` son **TRUE**. 

El operador `OR` mostrará los resultados si **algunas de las condiciones** separadas por `OR` son **TRUE**.

El operador `NOT` mostrará un resultado si la condición es **NOT TRUE**.

Algunos ejemplos combinando estos operadores: 

```mysql
SELECT * FROM Customers WHERE Country='Germany' AND (City='Berlin' OR City='München');
/* Mostará los clientes donde el país sea Alemania y además la ciudad sea Berlin o München. */
SELECT * FROM Customers WHERE NOT Country='Germany' AND NOT Country='USA';
/* Mostrará los clientes cuyo país no sea Alemania ni USA. */
```



:black_circle: **Operadores ANY y ALL**

Los operadores `ANY` y `ALL` se utilizan solo con las cláusulas `WHERE` o `HAVING`. 

El operador `ANY` devuelve true si **alguno** de los valores de la subconsulta coinciden en la condición.

```mysql
SELECT nombreColumna(s) FROM nombreTabla
WHERE nombreColumna operator ANY (SELECT nombreColumna1 FROM nombreTabla2 WHERE condicion);
```

El operador `ALL` devuelve true si **todos** los valores de la subconsulta coincide con la condición.

```
SELECT nombreColumna(s) FROM nombreTabla
WHERE nombreColumna operator ALL (SELECT nombreColumna1 FROM nombreTabla2 WHERE condicion);
```

> 'operador' hace referencia a un operador estándar de comparación (=, <>, >, >=, <, o <=).

Algunos ejemplos serían:

```mysql
SELECT ProductName FROM Products
WHERE ProductID = ANY (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
-- Devuelve TRUE y lista el nombre de los productos si encuentra algún registro en los detalles de pedido cuya cantidad sea 10
```

```mysql
SELECT ProductName FROM Products
WHERE ProductID = ALL (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
-- Devuelve TRUE y lista los nombres de productos si TODOS los registros en los detalles de pedido tienen 10 de cantidad.
```



### :black_circle: ORDER BY

La cláusula `ORDER BY` se utiliza para ordenar el resultado de forma ascendiente o descendiente. Por defecto los resultados se ordenan de form ascendente, si quisiéramos invertirlo, se utiliza `DESC`.

```mysql
SELECT columna1, columna2 FROM NombreTabla ORDER BY columna1, columna2 [ASC]|[DESC];
SELECT * FROM Customers ORDER BY Country; 
/* Mostrará todos los resultados ordenados alfabéticamente por país (Argentina - Venezuela) */
SELECT * FROM Customers ORDER BY Country DESC;
/* Mostrará todos los resultados ordenados alfabéticamente con el orden invertido (Ven - Arg) */
```

Además se pueden agrupar varias columnas a ordenar, de forma que tendrá preferencia de izquierda a derecha.

```MYSQL
SELECT * FROM Customers ORDER BY Country, CustomerName; 
/* Mostrará todos los resultados ordenados por país en primer lugar, y entre estos ordenados por nombre del cliente */
SELECT * FROM Customers ORDER BY Country ASC, CustomerName DESC; 
/* Igual que el anterior, pero el orden de los nombres de clientes estará invertido */
```



### :black_circle:INSERT INTO

La declaración `INSERT INTO` se utiliza para insertar nuevos registros en una tabla. Es posible realizarlo de dos formas:

La primera, especificando en ambos sitios las columnas y valores que se insertan. O por otra parte si estás añadiendo todos los valores de la columna de la tabla, no necesitas especificar las columnas, pero tienes que asegurarte que el orden en el que metes los valores se corresponden a la columna.

```mysql
INSERT INTO NombreTabla (columna1,columna3) VALUES (valor1,valor3);
INSERT INTO NombreTabla VALUES (valor1, valor2, valor3, ...);
```

> Normalmente el ID de la tabla, suele ser un autoincrementable, por lo que se genera al insertar los datos en la tabla.



### :black_circle: Valores Null

Cuando un campo está definido como `NULL`, quiere decir que no tiene valor.  Si un campo en una tabla es opcional, es posible al insertar un nuevo valor o actualizarlo sin añadir un valor a este campo. Entonces este campo será guardado como `null`.

> Es importante entender que `null` no significa cero o un campo que contiene espacios. Un campo que contiene valor nulo es que quedó en blanco durante la creación del registro

No se puede comprobar valores NULL con operadores de comparación. Para poder comprobarlo tendríamos que utilizar los operadores `IS NULL` o `IS NOT NULL` en su lugar. Su sintaxis es:

```mysql
SELECT nombreColumna FROM nombreTabla WHERE nombreColumna IS NULL;
SELECT nombreColumna FROM nombreTabla WHERE nombreColumna IS NOT NULL;
```

Un ejemplo sería:

```mysql
SELECT LastName, FirstName, Address FROM Persons WHERE Address IS NULL;
/* Mostrará el apellido, el nombre y la dirección de las personas cuya dirección es NULL */
```



### :black_circle: Funciones NULL

Encontramos como funciones para los valores `null`: `IFNULL()`, `ISNULL()` y  `COALESCE()`

- La función `IFNULL()` permite devolver un valor alternativo si una expresión es NULL.

  La función `COALESCE()` realiza lo mismo.

- La función `ISNULL()` evalúa si una expresión es NULL. Devuelve 1 si es NULL, 0 si no lo es.





### :black_circle: UPDATE

La cláusula `UPDATE` se utiliza para modificar datos existentes de una tabla. Su sintaxis es la siguiente:

```mysql
UPDATE nombreTabla SET columna1 = valor1, columna2 = valor2 [WHERE condicion];
```

> Hay que tener cuidado cuando se actualizan registros en una tabla, la cláusula WHERE especifica qué registros deben ser actualizados. **Si omites la cláusula WHERE, todos los registros se actualizarán**.

Un ejemplo sería: 

```mysql
UPDATE Customers SET ContactName = 'Alfred Schmidt', City= 'Frankfurt' WHERE CustomerID = 1;
/* Actualizará de la tabla Clientes, el cliente con ID 1, cambiando los valores del UPDATE*/
```



### :black_circle: DELETE

Se utiliza `DELETE` para eliminar registros existentes en una tabla. Su sintaxis es la siguiente:

```mysql
DELETE FROM nombreTabla WHERE condicion;
```

> Hay que tener cuidado con el borrado de registros en una tabla, cuando se utiliza `WHERE`, seleccionará los registros que deben ser eliminados. Si se omite la cláusula `WHERE`, todos los registros de la tabla serán eliminados. 

Un ejemplo sería: 

```mysql
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste'; 
/* Eliminará al cliente que coincida con el nombre de la condición */
```

Si quisiéramos **eliminar todos los registros** de una tabla sin eliminar la misma, sería:

```mysql
DELETE FROM table_name;
DELETE * FROM table_name;
```



### :black_circle: FUNCIONES básicas

- **`MIN() y MAX()`**

  `MIN()` devuelve el menor valor de una columna seleccionada.  Su sintaxis es la siguiente:

  ```mysql
  SELECT MIN(nombreColumna) FROM nombreTabla WHERE condicion1;
  ```

  `MAX()` devuelve el mayor valor de una columna seleccionada. Su sintaxis es la siguiente:

  ```mysql
  SELECT MAX(nombreColumna) FROM nombreTabla WHERE condicion1;
  ```

  Unos ejemplos serían: 

  ```MYSQL
  SELECT MIN(Price) AS SmallestPrice FROM Products;
  SELECT MAX(Price) AS LargestPrice FROM Products;
  ```

- **`COUNT()`, `AVG()` y `SUM()`**

  `COUNT()` devuelve la cantidad de filas según un determinado criterio. Su sintaxis es:

  ```mysql
  SELECT COUNT(nombreColumna) FROM nombreTabla WHERE condicion1;
  ```

  `AVG()` devuelve la media aritmética de una columna numérica. Su sintaxis es: 

  ```mysql
  SELECT AVG(nombreColumna) FROM nombreTabla WHERE condicion1;
  ```

  `SUM()` devuelve la suma total de una columna numérica. Su sintaxis es:

  ```mysql
  SELECT SUM(nombreColumna) FROM nombreTabla WHERE condicion1;
  ```




### :black_circle: SELF JOIN

En el caso de `SELF JOIN` es un join normal, pero la tabla se combina con ella misma. Su sintaxis es:

```mysql
SELECT columna(s) FROM tabla1 T1, tabla1 T2 WHERE condición;
```

###  

### (INNER) JOIN

La cláusula `JOIN` se utiliza para combinar filas que se encuentran en dos o más tablas en función de una columna que se relaciona entre ellas. En otras palabras, devuelve registros que tienen valores coincidentes en ambas tablas. Un ejemplo sería:

```mysql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
-- Mostrará el ID de pedido, el nombre del cliente y la fecha del pedido.
```

![img_innerjoin](https://www.w3schools.com/sql/img_innerjoin.gif)



###  :black_circle: LEFT (OUTER) JOIN

En el caso del `LEFT JOIN` se combinarán ambas tablas pero devuelve registros de la tabla de la izquierda (tabla 1) y los registros coincidentes con la tabla de la derecha (tabla 2). **Si no hay coincidencia, devuelve null**. Un ejemplo sería lo siguiente:

```mysql
SELECT Customers.CustomerName, Orders.OrderID FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID ORDER BY Customers.CustomerName;
```

> La palabra clave `LEFT JOIN` devuelve todos los registros de la tabla de la izquierda (Clientes), incluso si no hay coincidencias en la tabla correcta (Pedidos).

![img_innerjoin](https://www.w3schools.com/sql/img_leftjoin.gif)



###  :black_circle: RIGHT (OUTER) JOIN

En el caso del `RIGHT JOIN` se combinarán ambas tablas pero devuelve registros de la tabla de la derecha (tabla 2) y los registros coincidentes con la tabla de la izquierda (tabla 1). **Si no hay coincidencias, devuelve null**. Un ejemplo sería lo siguiente:

```mysql
SELECT Orders.OrderID, Employees.LastName, Employees.FirstName FROM Orders
RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID ORDER BY Orders.OrderID;
```

> La palabra clave `RIGHT JOIN` devuelve todos los registros de la tabla correcta (Empleados), incluso si no hay coincidencias en la tabla de la izquierda (Pedidos).

![img_innerjoin](https://www.w3schools.com/sql/img_rightjoin.gif)

###  

### :black_circle: FULL (OUTER) JOIN

En el caso de `FULL JOIN` devolverá todos los registros de ambas tablas junto a las coincidencias. El lado negativo de esto es que puede dar resultados excesivamente grandes. Un ejemplo de esto sería:

```mysql
SELECT Customers.CustomerName, Orders.OrderID FROM Customers FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID ORDER BY Customers.CustomerName;
```

> La palabra clave FULL OUTER JOIN devuelve todas las filas de la tabla izquierda (Clientes) y todas las filas de la tabla derecha (Pedidos). Si hay filas en "Clientes" que no tienen coincidencias en "Pedidos", o si hay filas en "Pedidos" que no tienen coincidencias en "Clientes", esas filas también se mostrarán.

![img_innerjoin](https://www.w3schools.com/sql/img_fulljoin.gif)



### :black_circle: UNION 

El operador `UNION` se utiliza para combinar resultados de dos o más `SELECT`. Cada declaración `SELECT` sin `UNION` debe tener la misma cantidad de columnas, y los datos deben ser similares. Además las columnas de cada `SELECT` deben estar en el mismo orden. Su sintaxis es la siguiente:

```mysql
SELECT nombreColumna FROM nombreTabla UNION SELECT nombreColumna2 FROM nombreTabla2;
```

**Por defecto** `UNION` selecciona todos los valores pero **excluye los duplicados**. Si quieres permitir los valores duplicados se utiliza `UNION ALL`.

```mysql
SELECT nombreColumna1 FROM nombreTabla1 UNION ALL SELECT nombreColumna2 FROM nombreTabla2;
```

> Los nombres de columna en el conjunto de resultados, generalmente son iguales a los nombres de columna de la primera instrucción **SELECT**. 

Algunos ejemplos serían:

```mysql
SELECT City FROM Customers UNION SELECT City FROM Suppliers ORDER BY City;
/* Selecciona todas las ciudades diferentes (solo valores distintos) de Clientes y Vendedores */
SELECT City FROM Customers UNION ALL SELECT City FROM Suppliers ORDER BY City;
/* Selecciona todas las ciudades diferentes (incluyendo duplicados) de Clientes y Vendedores */
```

> Si algún cliente o vendedor tiene la misma ciudad, cada ciudad solo se listará una vez, porque `UNION` selecciona solo un valor. Se tendría que utlizar `UNION ALL` para seleccionar los duplicados.

```mysql
SELECT City, Country FROM Customers WHERE Country='Germany'
UNION SELECT City, Country FROM Suppliers WHERE Country='Germany' ORDER BY City;
/* Seleccionará todas las ciudades alemanas (sin duplicados) de Clientes y Vendedores */
SELECT City, Country FROM Customers WHERE Country='Germany'
UNION ALL SELECT City, Country FROM Suppliers WHERE Country='Germany' ORDER BY City;
/* Seleccionará todas las ciudades alemanas (con duplicados) de Clientes y Vendedores */
```



### :black_circle: GROUP BY

La declaración `GROUP BY` se utiliza para agregar funciones (`count, max, min, sum, avg`) a un grupo de resultados por una o más columnas. Su sintaxis es la siguiente:

```mysql
SELECT nombreColumna(s) FROM nombreTablas WHERE condicion1
GROUP BY nombreColumna(s) ORDER BY nombreColumna(s);
```

Unos ejemplos serían: 

```mysql
SELECT COUNT(CustomerID), Country FROM Customers GROUP BY Country;
-- Listará el número de clientes de cada país 
SELECT COUNT(CustomerID), Country FROM Customers 
GROUP BY Country ORDER BY COUNT(CustomerID) DESC; 
-- Listará el número de clientes de cada país, de mayor a menor 
```



### :black_circle: HAVING

La cláusula `HAVING` se añadió a SQL porque la palabra clave `WHERE` no se debe utilizar con funciones agregadas. Por lo que `HAVING` se utiliza únicamente con agrupaciones. Su sintaxis es la siguiente:

```mysql
SELECT nombreColumna(s) FROM nombreTabla WHERE condicion
GROUP BY nombreColumna(s) HAVING condicion ORDER BY nombreColumna(s);
```

Algunos ejemplos serían: 

```mysql
SELECT COUNT(CustomerID), Country FROM Customers GROUP BY Country
HAVING COUNT(CustomerID) > 5; 
-- Listado del número de clientes de cada país, con sólo aquellos paises con más de 5 clientes.
```

```mysql
SELECT COUNT(CustomerID), CountryFROM Customers GROUP BY Country
HAVING COUNT(CustomerID) > 5 ORDER BY COUNT(CustomerID) DESC;
-- Listado del número de clientes de cada país, ordenado de mayor a menor, incluyendo países con más de 5 clientes.
```

```mysql
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
WHERE LastName='Davolio' OR LastName='Fuller' GROUP BY LastName HAVING COUNT(Orders.OrderID)>25;
-- Listado de empleados 'Davolio' o 'Fuller' que hayan registrado más de 25 pedidos.
```







### ⚫️ SUBCONSULTAS

Una subconsulta es una consulta que aparece dentro de las cláusulas `WHERE` o `HAVING`. En la primera, ayudan a seleccionar las filas individuales que aparecen en los resultados de la consulta. En la segunda, ayuda a seleccionar los grupos de filas que aparecen en los resultados de la consulta. 

El **resultado** que debe producir es de una **única columna de datos**.  Un ejemplo de esto sería: 

```mysql
SELECT ciudad FROM oficinas 
WHERE ventas < (SELECT 0.5  UM(cuota) FROM repventas WHERE oficina_rep=oficina);
```



### :black_circle: EXISTS

El operador `EXISTS` se utiliza para probar la existencia de algún registro de una subconsulta. El operador devuelve `true` si la subconsulta devuelve uno o más valores. Su sintaxis es la siguiente: 

```mysql
SELECT nombreColumna(s) FROM nombreTabla WHERE EXISTS
(SELECT nombreColumna2 FROM nombreTabla2 WHERE condicion);
```

Algunos ejemplos serían:

```mysql
SELECT SupplierName FROM Suppliers WHERE 
EXISTS(SELECT ProductName FROM Products WHERE SupplierId=Suppliers.supplierId AND Price < 20);
-- Devuelve true y lista los vendedores con un producto cuyo precio es menor de 20.
```

```mysql
SELECT SupplierName FROM Suppliers WHERE EXISTS (
  SELECT ProductName FROM Products WHERE SupplierId = Suppliers.supplierId AND Price = 22);
-- Devuelve true y lista los vendedores cuyo precio de producto es 22.
```



### :black_circle: Funciones específicas de MySQL

Algunas funciones relacionadas con **strings** más importantes:

| Función                                  | Descripción                              | Ejemplo                                  |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `LOWER()` o `UPPER()`                    | Cambia una cadena a minúscula (lower) o mayúscula(upper). | ` SELECT LOWER(CustomerName) AS LowercaseCustomerName FROM Customers;` |
| `CHAR_LENGTH()` o `CHARACTER_LENGTH()`   | Devuelve la longitud de una cadena específica. | `SELECT CHARACTER_LENGTH(CustomerName) AS LengthOfNameFROM Customers;` |
| `CONCAT()` y `CONCAT_WS`                 | Concatena dos o más cadenas de string. `CONCAT_WS` añade separadores entre las cadenas. | ` SELECT CONCAT(Address, " ", PostalCode, " ", City) AS AddressFROM Customers;` |
| `TRIM()`                                 | Elimina espacios al inicio y al final de la cadena. | `SELECT LTRIM(" Tutorial  ") AS LeftTrimmedString;` |
| ` STRCMP()`                              | Compara si dos cadenas son idénticas. Devuelve 0 si son iguales, si s1 < s2 devolverá -1 y si es el contrario devolverá 1 | `SELECT STRCMP("SQL", "JAVA");`          |
| `REVERSE()`                              | Invierte una cadena.                     | `SELECT REVERSE("SQL");`                 |
| ` REPLACE(string, from_substring, to_substring)` | Reemplaza la cadena que se indica, con el substring que se cambiará por el que se le pasa finalmente por parámetro. | ` SELECT REPLACE("ABC ABC ABC", "A", "B");` |

Algunas funciones relacionadas con **valores numéricos** más importantes:

| Función              | Descripción                              | Ejemplo                    |
| -------------------- | ---------------------------------------- | -------------------------- |
| `ABS()`              | Devuelve el valor absoluto del parámetro que se pasa. | ` SELECT ABS(-243.5);`     |
| `DIV`                | Divide dos valores.                      | ` SELECT 10 DIV 5;`        |
| `FLOOR()` o `CEIL()` | Redondea siempre hacia su menor valor (floor) o hacia el mayor (ceil). En el ejemplo: *(Mostrará 26, si fuese floor 25)* | ` SELECT CEIL(25.75);`     |
| `PI()`               | Devuelve el número PI con 6 decimales.   | `SELECT PI();`             |
| `POW()`              | Realiza una potencia con los parámetros que se le pasen. | ` SELECT POW(4, 2);`       |
| `ROUND()`            | Redondea al número de decimales que se le indiquen. | `SELECT ROUND(135.375,2);` |
| `SQRT()`             | Realiza una raíz cuadrada del parámetro que se le pase. | ` SELECT SQRT(64);`        |

Algunas funciones relacionadas con **fechas** más importantes: 

| Función                                  | Descripción                              | Ejemplos                                 |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `CURRENT_DATE`, `CURRENT_TIME`, o ` CURRENT_TIMESTAMP(` | Obtiene la fecha actual, o la hora actual, o el conjunto de ambos. | ` SELECT CURRENT_TIMESTAMP();`           |
| `DATE_ADD`                               | Obtiene la fecha tras un intervalo de tiempo indicado. | `SELECT DATE_ADD("2017-06-25", INTERVAL 10 DAY);` |
| `DATE_FORMAT` o `TIME_FORMAT`            | Obtiene una máscara concreta de la fecha u hora que se pase. | `SELECT DATE_FORMAT("2017-06-15", "%Y");` |
| `DAY`, `MONTH`, `YEAR`                   | Extrae el día, mes o año de la fecha que se pase. | ` SELECT DAY("2017-06-15");`             |
| `SYSDATE`                                | Obtiene la fecha del sistema             | `SELECT SYSDATE();`                      |



### :notebook: Algunas consultas realizadas en clase

```MYSQL
-- Ejemplos de inner JOIN
SELECT DISTINCT oficinas.region
FROM oficinas,repventas,pedidos,productos
WHERE oficinas.oficina = repventas.oficina_rep
AND repventas.num_empl = pedidos.rep AND pedidos.fab = productos.id_fab
AND pedidos.producto = productos.id_producto AND productos.precio < 1000;

SELECT rv1.nombre, rv2.nombre FROM repventas rv1, repventas rv2 
WHERE rv1.director = rv2.num_empl;

-- F U N C I O N E S
-- Cuota total para todos los vendedores
SELECT nombre, (ventas-cuota) AS diferencia  FROM repventas 
WHERE (ventas-cuota)>0 ORDER BY diferencia DESC;

-- Cuota mínima y máxima de los vendedores.
SELECT min(cuota) AS minimo FROM repventas;
SELECT max(cuota) AS maximo FROM repventas;

-- Media aritmética de las cuotas
SELECT AVG(cuota) AS media FROM repventas WHERE cuota > 0;

-- Cantidad de vendedores que superen su cuota.
SELECT COUNT(cuota) AS VendedoresSuperanCuota FROM repventas WHERE (ventas-cuota)>0; 

-- Consultas sumarias
SELECT count(*) as VendedoresSuperanCuota, sum(cuota) AS sumaCuotasTotales, sum(ventas) AS ventasTotales, sum(ventas)/count(*) media, avg(ventas) media2 FROM repventas WHERE (ventas-cuota)>0

-- Eliminación de filas duplicadas
SELECT DISTINCT count(titulo) AS titulos FROM repventas;

-- G R O U P  B Y
-- Tamaño medio de los vendedores y la cantidad de ventas hechas
SELECT rep, clie, AVG(importe) MediaVendedor, count(*) VentasRealizadas
FROM pedidos GROUP BY rep, clie ORDER BY rep, clie;
-- En el ORDER BY si utilizas un valor numérico se referirá a la posición de la columna.

-- Pedidos totales por cliente y vendedor
SELECT rep, repventas.nombre, clie, clientes.empresa, AVG(importe) MediaVendedor, count(*) VentasRealizadas FROM pedidos, clientes, repventas 
WHERE pedidos.clie = clientes.num_clie AND pedidos.rep = repventas.num_empl 
GROUP BY rep, repventas.nombre, clie, clientes.empresa ORDER BY rep, clie;
-- Tras el GROUP BY deben aparecer aquellos elementos que no llevan funciones.

-- Número de vendedores asignados a cada oficina.
SELECT repventas.oficina_rep, count(*) EmpleadosOficina
FROM repventas GROUP BY repventas.oficina_rep 
ORDER BY repventas.oficina_rep DESC;

-- Si quisiéramos cambiar nulos por "Sin oficina" y además concatenar "Oficina" a las que tienen valor.
SELECT IFNULL(CONCAT("Oficina: ",oficina_rep), "Sin Oficina"), count(*) EmpleadosOficina 
FROM repventas GROUP BY repventas.oficina_rep ORDER BY repventas.oficina_rep DESC;

-- Mostrar la mayor y la menor cuota por agrupación 
SELECT oficina_rep, MIN(cuota) AS cuotaMinima, MAX(cuota) AS cuotaMaxima
FROM repventas GROUP BY oficina_rep;

-- H A V I N G (Condición para la agrupación - GROUP BY)
SELECT oficina_rep, count(*) numeroVendedores
FROM repventas GROUP BY oficina_rep HAVING COUNT(*)>=2 ORDER BY numeroVendedores DESC;

SELECT oficina_rep, count(*) numeroVendedores
FROM repventas WHERE oficina_rep IS NOT NULL
GROUP BY oficina_rep HAVING COUNT(*)>=2 ORDER BY numeroVendedores DESC;

-- Cantidad de empleados por región 
SELECT region, COUNT(num_empl) AS NumeroEmpleadosRegion
FROM oficinas, repventas WHERE oficinas.oficina = repventas.oficina_rep
GROUP BY region HAVING NumeroEmpleadosRegion >= 2 ORDER BY 2; 

-- Precio, existencias, y cantidad total de los pedidos de cada producto para los cuales la cantidad total pedida es superior al 75% de las existencias.
SELECT productos.id_fab, productos.id_producto, productos.precio, productos.existencias, 
SUM(pedidos.cant) AS SumaTotalCantidadPedida
FROM productos, pedidos WHERE productos.id_fab = pedidos.fab
GROUP BY productos.id_fab, productos.id_producto, productos.existencias 
HAVING SumaTotalCantidadPedida > productos.existencias*0.75
ORDER BY existencias, SumaTotalCantidadPedida DESC;

-- Subconsulta de pertenencia comparando un campo y el dato tiene que estar dentro de lo que te devuelve la otra.
SELECT * FROM oficinas 
WHERE oficina IN (SELECT oficina FROM oficinas WHERE oficina < 20);

SELECT nombre, edad FROM empleados WHERE edad = 
(SELECT max(contrato) FROM empleados WHERE edad = (SELECT max(edad) FROM empleados));

-- Lista de los vendendores que trabajan en oficinas que superan su objetivo de ventas
SELECT repventas.num_empl
FROM repventas WHERE repventas.oficina_rep IN (SELECT oficina FROM oficinas WHERE ventas > objetivo);

SELECT clientes.rep_clie FROM clientes WHERE clientes.limite_credito NOT IN (SELECT clientes.limite_credito FROM clientes WHERE clientes.limite_credito < 50000);

-- Salario y Trienio incrementado
SELECT salario*1.02 AS SalarioIncrementado, trienio*1.02 AS TrienioIncrementado FROM categorias;

-- Empleados mayores de 35 años y Administrativos
SELECT empleadis.nombre FROM empleados, categorias WHERE empleados.categoria = categorias.categoria AND categorias.titulo LIKE 'Administrativo' AND empleados.edad > 35;

-- Empleados de mayor edad
SELECT nombre, edad, contrato FROM empleados WHERE num = (SELECT num FROM empleados WHERE edad = MAX(edad) FROM empleados) AND contrato = (SELECT MAX(contrato) FROM empleados WHERE edad = (SELECT MAX(edad) FROM empleados)));

-- Misma que la anterior pero más eficiente
SELECT nombre, edad FROM empleados WHERE edad = (SELECT MAX(edad) FROM empleados);
SELECT nombre, edad FROM empleados e1 WHERE NOT EXISTS (SELECT num FROM empleados e2 WHERE e2.edad > e1.edad);
SELECT nombre, edad FROM empleados e1, empleados e2 WHERE NOT EXISTS e2.edad > e1.edad;

SELECT cat.categoria FROM categorias cat WHERE not EXISTS (SELECT * from EMPLEADOS WHERE categoria = cat.categoria);

SELECT categorias.categoria FROM categorias WHERE categoria NOT IN (SELECT DISTINCT categoria FROM empleados);

SELECT categorias.* FROM categorias LEFT JOIN empleados ON categorias.categoria = empleados.categoria;
```

