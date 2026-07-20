¿Qué es el control de flujo? El control de flujo es el conjunto de instrucciones que permiten decidir cómo y cuándo se ejecuta el código dentro de un script,
procedimiento almacenado o función. Gracias a él, es posible crear lógica condicional e iterativa según determinadas condiciones.
Instrucciones condicionales

Permiten ejecutar diferentes bloques de código dependiendo de si una condición es verdadera o falsa.

IF...ELSE

Se utiliza para tomar decisiones.

Sintaxis
IF condición
BEGIN
    -- Instrucciones
END
ELSE
BEGIN
    -- Otras instrucciones
END
Ejemplo
DECLARE @valor INT = 55;

IF @valor < 10
    PRINT 'EL PRECIO ES MUY BAJO';
ELSE
    PRINT 'EL PRECIO ES MUY CARO';

Si la condición es verdadera, se ejecuta el primer bloque; si es falsa (o NULL), se ejecuta el bloque ELSE.

CASE

Es una expresión que devuelve un valor según distintas condiciones.

Se utiliza principalmente dentro de consultas SELECT.

Ejemplo:

SELECT Nombre,
CASE
    WHEN Sueldo > 2000 THEN 'Alto'
    ELSE 'Bajo'
END AS Categoria
FROM Empleados;

CASE es útil para clasificar o transformar datos directamente en una consulta.

BEGIN...END

Las palabras clave BEGIN y END permiten agrupar varias instrucciones para que se ejecuten como un solo bloque lógico. Son muy utilizadas junto con IF, ELSE y WHILE.

Ejemplo
IF @edad >= 18
BEGIN
    PRINT 'Mayor de edad';
    PRINT 'Puede ingresar';
END

Si no se usan BEGIN y END, solo se ejecutará la primera instrucción después del IF, lo que puede provocar errores.

Bucles repetitivos

Los bucles permiten ejecutar un conjunto de instrucciones varias veces mientras una condición sea verdadera. Son útiles para automatizar tareas repetitivas.

WHILE

Es el bucle más utilizado en T-SQL.

Sintaxis
WHILE condición
BEGIN
    -- Instrucciones
END
Ejemplo
DECLARE @i INT = 1;

WHILE @i <= 5
BEGIN
    PRINT @i;
    SET @i = @i + 1;
END

Este código imprime los números del 1 al 5.

BREAK

La instrucción BREAK finaliza inmediatamente el bucle WHILE.

Ejemplo:

IF @i = 9
    BREAK;

Cuando se ejecuta BREAK, el programa sale del bucle y continúa con las instrucciones posteriores.

CONTINUE

La instrucción CONTINUE salta el resto del código de la iteración actual y vuelve al inicio del WHILE.

Ejemplo:

IF @i = 7
BEGIN
    SET @i = @i + 1;
    CONTINUE;
END

En este caso, cuando @i vale 7, el resto del código de esa vuelta no se ejecuta y el ciclo continúa con la siguiente iteración.

GOTO

GOTO permite saltar directamente a una etiqueta del código.

Ejemplo:

IF @i = 8
    GOTO mensaje;

mensaje:
PRINT 'Fin del proceso';

Aunque existe, no se recomienda abusar de GOTO, ya que puede dificultar la lectura y el mantenimiento del código.

WAITFOR

La instrucción WAITFOR pausa la ejecución durante un tiempo determinado o hasta una hora específica.

Ejemplo:

WAITFOR DELAY '00:00:20';

Este código detiene la ejecución durante 20 segundos. Es útil para simular esperas o controlar tiempos entre operaciones

IMPORTANTE PARA RECORDAR

| Estructura    | ¿Para qué sirve?                                             |
| ------------- | ------------------------------------------------------------ |
| `IF...ELSE`   | Ejecuta un bloque u otro según una condición.                |
| `CASE`        | Devuelve un valor según varias condiciones.                  |
| `BEGIN...END` | Agrupa varias instrucciones en un mismo bloque.              |
| `WHILE`       | Repite instrucciones mientras una condición sea verdadera.   |
| `BREAK`       | Sale inmediatamente del bucle.                               |
| `CONTINUE`    | Omite el resto de la iteración y vuelve al inicio del bucle. |
| `GOTO`        | Salta a una etiqueta específica del código.                  |
| `WAITFOR`     | Pausa la ejecución durante un tiempo determinado.            |

El control de flujo permite decidir el orden en que se ejecutan las instrucciones.
IF...ELSE se utiliza para tomar decisiones.
CASE se emplea dentro de consultas para devolver valores según condiciones.
BEGIN...END es necesario cuando un IF, ELSE o WHILE debe ejecutar más de una instrucción.
WHILE ejecuta un bloque repetidamente mientras la condición sea verdadera.
BREAK termina el bucle, mientras que CONTINUE salta a la siguiente iteración.
WAITFOR introduce una pausa en la ejecución.
