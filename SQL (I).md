## :floppy_disk: SQL Databases

### :arrow_forward: Crear

Para crear una nueva base de datos, seguimos la siguiente estructura:

```mysql
CREATE DATABASE databasename;
SHOW DATABASES; -- Mostrará un listado con las bases de datos existentes.
```

> Antes de crear una nueva BBDD hay que asegurarse de que se tienen los **privilegios** para ello. 

### :arrow_forward: Eliminar

Para eliminar una base de datos, seguimos la siguiente estructura:

```mysql
DROP DATABASE databasename;
```

> Antes de eliminar una BBDD hay que asegurarse previamente pues su borrado implica la pérdida de todos los datos que almacena.

### ▶ Tablas

​	:black_circle: **Creación** de tablas:

```mysql
  	CREATE TABLE nombreTabla (
      columna1 tipoDato,
      columna2 tipoDato,
      columna3 tipoDato, ....
	);
```

​	Podríamos realizar una copia de una tabla realizando lo siguiente:

```mysql
  CREATE TABLE nuevaTabla AS SELECT * FROM tablaExistente WHERE ....;
```

​	:black_circle: **Eliminación** de tablas:

```mysql
   DROP TABLE table_name; -- Eliminará toda la tabla, incluída ella misma.
   TRUNCATE TABLE table_name; -- Eliminará toda la información de la tabla pero no ella misma.
```

> Hay que tener cuidado al eliminar una tabla, pues eliminará toda la información que esta contiene.
>
> **Importante** NO confundir con DELETE, esto lo que hace es una consulta de eliminación, si no se especifica qué se quiere borrar, borrará toda la información pero no la tabla en sí misma siendo entonces equivalente a `DELETE * FROM nombreTabla;`

​	:black_circle: **Modificación** de tablas:

```mysql
	ALTER TABLE nombreTabla ADD nombreColumna tipoDato; -- Añade una columna
	ALTER TABLE nombreTabla DROP COLUMN nombreColumna; -- Elimina una columna
	ALTER TABLE nombreTabla MODIFY COLUMN nombreColumna tipoDato; -- Modifica una columna
```

> `MODIFY COLUMN` es específico para MySQL y Oracle, cambiando así el tipo de dato de la columna.

​	:black_circle: **Restricciones** de los datos:

```mysql
	CREATE TABLE nombreTabla (
    	columna1 tipoDato [constraint], ....
	);
```

​	**Tipos** de restricciones:	

| Restricción   | Descripción                              |
| ------------- | ---------------------------------------- |
| `NOT NULL`    | Establece que la columna no pueda ser **null**. |
| `UNIQUE`      | Establece que cada valor de la columna sea único. |
| `PRIMARY KEY` | Combina `not null` y `unique`, es un identificador de cada fila en una tabla. |
| `FOREIGN KEY` | Identificador de una fila de otra tabla. |
| `CHECK`       | Establece que todos los valores de una columna cumplan una condición específica. |
| `DEFAULT`     | Establece un valor por defecto en caso de que no sea introducido. |
| `INDEX`       | Crea y recupera datos de la base de datos más rápidamente. |

`NOT NULL` Obliga a un campo a contener siempre un valor, lo que significa que no puede insertar un nuevo registro o actualizar un registro sin agregar un valor a este campo.

> Si la tabla está creada previamente, se utiliza `ALTER TABLE`.

Sólo `UNIQUE` y `PRIMARY KEY` proporcionan una garantía de exclusividad para una columna o conjunto de columnas. Se pueden utilizar dos formas en MySQL de establecer una restricción `UNIQUE`:

```mysql
-- Forma 1
CREATE TABLE Persons (
    ID int NOT NULL, LastName varchar(255) NOT NULL, FirstName varchar(255), Age int,
    UNIQUE (ID)	);
ALTER TABLE Persons ADD UNIQUE (ID); -- Si ya está creada.
-- Forma 2
CREATE TABLE Persons (
    ID int NOT NULL, LastName varchar(255) NOT NULL, FirstName varchar(255),Age int,
    CONSTRAINT UC_Person UNIQUE (ID,LastName) );
ALTER TABLE Persons ADD CONSTRAINT UC_Person UNIQUE (ID,LastName); -- Si ya está creada.

-- Eliminación de la restricción:
ALTER TABLE Persons DROP INDEX UC_Person;
```

`CHECK` limita el rango de valores que pueden ser almacenados en una columna. Un ejemplo:

```mysql
CREATE TABLE Persons (
    ID int NOT NULL, ... , Age int,
    CHECK (Age>=18) );
ALTER TABLE Persons ADD CHECK (Age>=18);
```

`DEFAULT` establece un valor por defecto si este no se especifica, un ejemplo: 

```mysql
CREATE TABLE Persons (
    ID int NOT NULL, LastName varchar(255) NOT NULL,FirstName varchar(255),Age int,
    City varchar(255) DEFAULT 'Sandnes');
ALTER TABLE Persons ALTER City SET DEFAULT 'Sandnes';
```

>  Un uso muy útil de `DEFAULT` es para obtener valores del sistema, por ejemplo para DATE se utiliza `GETDATE()`.

Los `INDEX` se utilizan para recuperar datos de la base de datos muy rápido. Los usuarios no pueden ver los índices, solo se utilizan para acelerar las búsquedas/consultas.

> Actualizar una tabla con índices lleva más tiempo que actualizar una tabla sin (porque los índices también necesitan una actualización). Por lo tanto, solo cree índices en columnas que se buscarán con frecuencia contra.

```mysql
CREATE INDEX nombreIndex ON nombreTabla (columna1, columna2, ...); -- Permite valores duplicados
CREATE UNIQUE INDEX nombreIndex ON nombreTabla (col1, col2, ...); -- Sin valores duplicados
ALTER TABLE nombreTabla DROP INDEX nombreIndex; -- Para eliminar un índice
```

> La sintaxis para crear índices varía entre las diferentes bases de datos.

El `AUTOINCREMENT` permite que se genere un número único automáticamente cuando se inserta un nuevo registro en una tabla. A menudo, este es el campo clave principal que nos gustaría que se cree automáti-camente cada vez que se inserta un nuevo registro.

```mysql
CREATE TABLE Persons (
    ID int NOT NULL AUTO_INCREMENT,....
    PRIMARY KEY (ID) );
ALTER TABLE Persons AUTO_INCREMENT=100; -- Si queremos que comience en otro valor que no sea 0
```

### :arrow_forward: VIEWS

En SQL, una vista es una tabla virtual basada en el conjunto de resultados de una consulta de SQL.

Una vista contiene filas y columnas, al igual que una tabla real. Los campos en una vista son campos de una o más tablas reales en la base de datos. Se pueden agregar funciones de SQL, WHERE y JOIN a una vista y presentar los datos como si los datos provinieran de una sola tabla. Su sintaxis:

```mysql
CREATE VIEW nVista AS SELECT columna1, columna2, ... FROM nombreTabla WHERE condicion;
```

> **Una vista siempre muestra datos actualizados** El motor de base de datos recrea los datos, utilizando la declaración SQL de la vista, cada vez que un usuario consulta una vista.

