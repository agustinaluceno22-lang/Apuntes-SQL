Modificación de tablas (ALTER TABLE)
¿Qué es ALTER TABLE? La sentencia ALTER TABLE se utiliza para modificar la estructura de una tabla existente sin eliminarla.
Permite agregar, eliminar o modificar columnas, cambiar el nombre de columnas o tablas, y administrar restricciones como claves primarias y foráneas.
Sintaxis general:
ALTER TABLE nombre_tabla
acción;

Agregar columnas
Se utiliza ADD COLUMN para incorporar una nueva columna a una tabla existente.
Ejemplo:
ALTER TABLE articulos
ADD COLUMN Observaciones VARCHAR(50) NULL;

Con FIRST la nueva columna se coloca como la primera de la tabla.
ALTER TABLE clientes
ADD COLUMN Primera VARCHAR(50) NULL FIRST;

Con AFTER se indica la posición donde se insertará la nueva columna.
ALTER TABLE clientes
ADD COLUMN Siguiente VARCHAR(50) NULL AFTER Nombr

Cambiar el nombre de una columna
Se utiliza CHANGE para renombrar una columna. Es necesario volver a indicar el tipo de dato.
ALTER TABLE articulos
CHANGE observaciones comentarios VARCHAR(40) NULL;

Con MODIFY se cambia el tipo de dato de una columna sin modificar su nombre.
ALTER TABLE articulos
MODIFY comentarios TEXT NULL;

Se utiliza DROP COLUMN para eliminar una columna de una tabla.
Eliminar una columna:
ALTER TABLE articulos
DROP COLUMN comentarios;

Eliminar varias columnas:
ALTER TABLE clientes
DROP COLUMN Primera,
DROP COLUMN Siguiente;

Existen dos formas de cambiar el nombre de una tabla.
Opción 1
ALTER TABLE Articulos
RENAME Productos;

Opción 2
RENAME TABLE Articulos
TO Productos;

Modificar restricciones (Constraints)
Eliminar una Primary Key

ALTER TABLE Articulos
DROP PRIMARY KEY;
Agregar una Primary Key
ALTER TABLE Articulos
ADD PRIMARY KEY (ArticuloID);
Estas operaciones permiten quitar o asignar la clave primaria de una tabla.

Modificar Foreign Keys
Eliminar una Foreign Key
ALTER TABLE facturas
DROP FOREIGN KEY fk_articulo;
Agregar una Foreign Key
ALTER TABLE facturas
ADD CONSTRAINT fk_articulo
FOREIGN KEY (ArticuloID)
REFERENCES Articulos(ArticuloID);

Las claves foráneas establecen relaciones entre tablas y ayudan a mantener la integridad referencial de la base de datos

| Comando                          | Función                                                              |
| -------------------------------- | -------------------------------------------------------------------- |
| `ALTER TABLE`                    | Modifica la estructura de una tabla.                                 |
| `ADD COLUMN`                     | Agrega una nueva columna.                                            |
| `FIRST`                          | Inserta la columna al inicio de la tabla.                            |
| `AFTER`                          | Inserta la columna después de otra columna.                          |
| `CHANGE`                         | Cambia el nombre de una columna (indicando también el tipo de dato). |
| `MODIFY`                         | Modifica el tipo de dato de una columna.                             |
| `DROP COLUMN`                    | Elimina una columna.                                                 |
| `RENAME`                         | Cambia el nombre de una tabla.                                       |
| `ADD PRIMARY KEY`                | Agrega una clave primaria.                                           |
| `DROP PRIMARY KEY`               | Elimina la clave primaria.                                           |
| `ADD CONSTRAINT ... FOREIGN KEY` | Agrega una clave foránea.                                            |
| `DROP FOREIGN KEY`               | Elimina una clave foránea.                                           |
