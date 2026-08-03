¿Qué es un cursor?
Un cursor es una estructura de SQL Server que permite recorrer fila por fila el resultado de una consulta.
Se utiliza cuando es necesario procesar los datos de forma secuencial, algo que una consulta SQL tradicional no puede realizar directamente.

Características
Permite recorrer un conjunto de resultados fila por fila.
Facilita realizar cálculos o actualizaciones sobre cada registro.
Consume más recursos que las operaciones en bloque.
Debe utilizarse únicamente cuando sea necesario.

Importante: Siempre que sea posible, es preferible utilizar consultas en bloque (JOIN, GROUP BY, subconsultas, etc.), ya que son más eficientes.

¿Cuándo usar un cursor?

Se recomienda utilizar cursores cuando:

Es necesario procesar cada fila individualmente.
Una operación depende del resultado de la fila anterior.
Cada registro requiere una validación o cálculo diferente.
Se necesita recorrer una tabla para migrar datos aplicando transformaciones específicas.

Evitar usar cursores cuando una consulta SQL tradicional pueda resolver el problema, ya que los cursores son más lentos y consumen más recursos.

Ciclo de vida de un cursor

El uso de un cursor sigue siempre los mismos pasos:

DECLARE → Declarar el cursor.
OPEN → Abrir el cursor.
FETCH NEXT → Leer una fila.
Procesar la fila.
Repetir hasta terminar.
CLOSE → Cerrar el cursor.
DEALLOCATE → Liberar la memoria.

Flujo de un cursor
DECLARE
    ↓
OPEN
    ↓
FETCH
    ↓
¿Hay más filas?
    ↓
Sí ───► Procesar fila
 │
No
 ↓
CLOSE
 ↓
DEALLOCATE

DECLARE CURSOR

Se utiliza para crear el cursor indicando la consulta que recorrerá.

DECLARE NombreCursor CURSOR
FOR
SELECT ...

Permite definir:

La consulta que recorrerá.
El comportamiento del cursor.
Su forma de desplazamiento.

OPEN

Abre el cursor para comenzar a recorrer el conjunto de resultados.

OPEN NombreCursor;
FETCH

Obtiene una fila del cursor.

La opción más utilizada es:

FETCH NEXT

que devuelve la siguiente fila disponible.

@@FETCH_STATUS

Es una función del sistema que indica el resultado del último FETCH.

Generalmente se utiliza para controlar el recorrido del cursor.

WHILE @@FETCH_STATUS = 0
BEGIN

    -- Procesar fila

END

Cuando el valor deja de ser 0, significa que ya no quedan registros por recorrer.

Tipos de FETCH
FETCH NEXT

Obtiene la siguiente fila.

Es la opción predeterminada.

FETCH PRIOR

Obtiene la fila anterior.

FETCH FIRST

Obtiene la primera fila.

FETCH LAST

Obtiene la última fila.

CLOSE

Cierra el cursor.

CLOSE NombreCursor;

Después de cerrarlo ya no puede seguir recorriéndose hasta volver a abrirlo.

DEALLOCATE

Libera completamente los recursos utilizados por el cursor.

DEALLOCATE NombreCursor;

Después de ejecutarlo, el cursor deja de existir.

PROCEDIMIENTOS ALMACENADOS RELACIONADOS CON CURSORES
SQL Server incluye procedimientos del sistema para trabajar con cursores.
| Procedimiento                | Función                                      |
| ---------------------------- | -------------------------------------------- |
| `sp_cursor_list`             | Lista los cursores abiertos                  |
| `sp_describe_cursor`         | Describe un cursor                           |
| `sp_describe_cursor_columns` | Describe las columnas del cursor             |
| `sp_describe_cursor_tables`  | Describe las tablas utilizadas por el cursor |
Estos procedimientos se almacenan en la base de datos master y ayudan en la administración y monitoreo de cursores.

Ejemplo básico
DECLARE Cursor_Titulos CURSOR
FOR
SELECT ...

OPEN Cursor_Titulos;

FETCH NEXT
FROM Cursor_Titulos
INTO @Variables;

WHILE @@FETCH_STATUS = 0
BEGIN

    -- Procesar datos

    FETCH NEXT
    FROM Cursor_Titulos
    INTO @Variables;

END

CLOSE Cursor_Titulos;

DEALLOCATE Cursor_Titulos;

Este ejemplo recorre un conjunto de registros y los almacena en una tabla temporal (#pvt).

RESUMEN RAPIDO
| Instrucción      | Función                    |
| ---------------- | -------------------------- |
| `DECLARE CURSOR` | Crea el cursor             |
| `OPEN`           | Abre el cursor             |
| `FETCH NEXT`     | Obtiene la siguiente fila  |
| `@@FETCH_STATUS` | Indica si quedan registros |
| `WHILE`          | Recorre todas las filas    |
| `CLOSE`          | Cierra el cursor           |
| `DEALLOCATE`     | Libera la memoria          |


Ventajas
Permite trabajar registro por registro.
Facilita validaciones complejas.
Útil para migraciones y procesos secuenciales.
Ofrece un control preciso sobre cada fila.

Desventajas
Es más lento que las consultas tradicionales.
Consume más memoria y recursos.
No es recomendable para grandes volúmenes de datos.
Siempre debe considerarse primero una solución basada en operaciones en bloque.

💡 Lo más importante para recordar
Un cursor recorre los resultados de una consulta fila por fila.
Solo debe utilizarse cuando una consulta SQL convencional no pueda resolver el problema.
El ciclo completo de un cursor es:
DECLARE
   ↓
OPEN
   ↓
FETCH
   ↓
WHILE @@FETCH_STATUS = 0
   ↓
Procesar registros
   ↓
CLOSE
   ↓
DEALLOCATE
FETCH NEXT es la opción más utilizada para recorrer registros.
@@FETCH_STATUS permite saber cuándo finalizar el recorrido.
Siempre cerrar (CLOSE) y liberar (DEALLOCATE) el cursor para evitar consumir recursos innecesarios.
