Eliminar registros de una tabla

Para eliminar registros de una tabla se utiliza la sentencia DELETE.

Permite eliminar uno o varios registros según una condición especificada mediante la cláusula WHERE.

🗑️ DELETE

La sentencia DELETE elimina registros de una tabla sin eliminar su estructura.

Sintaxis
DELETE FROM nombre_tabla
WHERE condición;

DELETE FROM Productos
WHERE idProducto = 1;

En este caso se elimina únicamente el producto cuyo idProducto es igual a 1.

⚠️ DELETE sin WHERE

Si se ejecuta un DELETE sin especificar una condición mediante WHERE, se eliminarán todos los registros de la tabla.

Ejemplo
DELETE FROM Productos;

Importante: La estructura de la tabla permanece intacta, pero todos los datos se eliminan.

La sentencia TRUNCATE TABLE se utiliza para vaciar completamente una tabla.

Es más eficiente que DELETE cuando se desea eliminar todos los registros.

Sintaxis
TRUNCATE TABLE nombre_tabla;
Ejemplo
TRUNCATE TABLE Productos;

Al ejecutar esta sentencia:

Se eliminan todos los registros.
La tabla queda vacía.
Se reinician los valores de los campos AUTO_INCREMENT.
Tiene un mejor rendimiento que DELETE cuando se eliminan todos los registros.

Diferencias entre DELETE y TRUNCATE
DELETE	                                                                     TRUNCATE
Elimina registros específicos o todos los registros.         	Elimina todos los registros de la tabla.
Puede utilizar WHERE.                                                   	No admite WHERE.
No reinicia el AUTO_INCREMENT.	                                    Reinicia el AUTO_INCREMENT.
Es menos eficiente cuando se eliminan todos los registros.   	Es más rápido y eficiente para vaciar una tabla.

💻 Ejemplos

Eliminar un registro específico
DELETE FROM Clientes
WHERE idCliente = 11;

Elimina únicamente el cliente cuyo identificador es 11.
Eliminar registros según una condición
DELETE FROM Clientes
WHERE FechaNacimiento < '1980-01-01';

Elimina todos los clientes nacidos antes del 1 de enero de 1980.

Eliminar todos los registros

Con DELETE:

DELETE FROM Clientes;

Con TRUNCATE:

TRUNCATE TABLE Clientes;

Ambas dejan la tabla sin registros, pero TRUNCATE es la opción recomendada cuando se desea vaciar toda la tabla, ya que ofrece un mejor rendimiento y reinicia el contador de AUTO_INCREMENT.

| Comando              | Función                                                        |
| -------------------- | -------------------------------------------------------------- |
| `DELETE`             | Elimina uno o varios registros de una tabla.                   |
| `WHERE`              | Define qué registros se eliminarán.                            |
| `DELETE` sin `WHERE` | Elimina todos los registros de la tabla.                       |
| `TRUNCATE TABLE`     | Vacía completamente una tabla de forma más rápida y eficiente. |
| `AUTO_INCREMENT`     | Se reinicia al utilizar `TRUNCATE`.                            |

