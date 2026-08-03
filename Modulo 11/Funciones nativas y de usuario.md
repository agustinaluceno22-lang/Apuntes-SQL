¿Qué son las funciones nativas?
Las funciones nativas son métodos predefinidos de SQL Server que permiten realizar operaciones comunes sin necesidad de programarlas desde cero.
Facilitan el manejo de datos, simplifican consultas complejas y mejoran el rendimiento.

Se clasifican principalmente en:

Funciones matemáticas.
Funciones de fecha.
Funciones de texto.
Funciones Matemáticas

Se utilizan para realizar operaciones con números.

ABS()
Devuelve el valor absoluto de un número.

SELECT ABS(-10);
Resultado:
10

ROUND()
Redondea un número según la cantidad de decimales indicada.
SELECT ROUND(4.55,1);
Resultado:
4.6

CEILING()
Devuelve el entero más pequeño mayor o igual al número.
SELECT CEILING(4.2);
Resultado:
5

FLOOR()
Devuelve el entero más grande menor o igual al número.
SELECT FLOOR(4.8);
Resultado:
4

SIGN()
Indica el signo del número.
Positivo → 1
Cero → 0
Negativo → -1
SELECT SIGN(-50);
Resultado:
-1

Estas funciones permiten realizar cálculos y operaciones numéricas comunes.

Funciones de Fecha

Permiten manipular y obtener información sobre fechas.

DATENAME()
Devuelve el nombre del elemento de la fecha.
SELECT DATENAME(MONTH,'2025-07-20');
Resultado:
Julio

DATEPART()
Devuelve una parte de la fecha en formato numérico.
SELECT DATEPART(MONTH,'2025-07-20');
Resultado:
7

DAY()
Obtiene el día.
SELECT DAY(GETDATE());

MONTH()
Obtiene el mes.
SELECT MONTH(GETDATE());

YEAR()
Obtiene el año.
SELECT YEAR(GETDATE());
GETDATE()

Devuelve la fecha y hora actual del servidor.
SELECT GETDATE();
DATEDIFF()

Calcula la diferencia entre dos fechas.
SELECT DATEDIFF(YEAR,'2000-01-01','2025-01-01');
Resultado:
25

DATEADD()
Suma o resta tiempo a una fecha.
SELECT DATEADD(MONTH,1,GETDATE());

Agrega un mes a la fecha actual.

Funciones de Texto

Permiten manipular cadenas de caracteres.

RIGHT()

Obtiene los caracteres de la derecha.
SELECT RIGHT('Argentina',4);
Resultado:
tina

LEFT()
Obtiene los caracteres de la izquierda.
SELECT LEFT('Argentina',3);
Resultado:
Arg

SUBSTRING()
Extrae una parte del texto.
SELECT SUBSTRING('Argentina',3,4);
Resultado:
gent

CHARINDEX()
Busca una palabra o letra dentro de un texto.
SELECT CHARINDEX('g','Argentina');
Devuelve la posición donde comienza.
REPLACE()

Reemplaza un texto por otro.
SELECT REPLACE('Hola','Hola','Chau');
Resultado:
Chau

LEN()
Cuenta la cantidad de caracteres.
SELECT LEN('Argentina');
Resultado:
9

LOWER()
Convierte el texto en minúsculas.
SELECT LOWER('HOLA');
Resultado:
hola

UPPER()
Convierte el texto en mayúsculas.
SELECT UPPER('hola');
Resultado:
HOLA

Estas funciones permiten analizar, transformar y presentar información textual en las consultas SQL.

Funciones Definidas por el Usuario (User Defined Functions)

Son funciones creadas por el programador para reutilizar código y aplicar reglas de negocio.

Características:

Reciben parámetros.
Ejecutan una acción.
Devuelven un resultado.
Pueden devolver un valor o una tabla.
Evitan repetir código y hacen las consultas más flexibles.
CREATE FUNCTION

Se utiliza para crear funciones propias.

Las funciones pueden utilizarse en:

SELECT
Aplicaciones
Otras funciones
Restricciones CHECK
Columnas calculadas
Vistas parametrizadas
Reemplazo de procedimientos almacenados
Tipos de Funciones
1. Funciones Escalares
Devuelven un único valor.
Se utilizan como cualquier función del sistema (COUNT, MAX, etc.).

Ejemplo:

SELECT dbo.fnTotalVentas(712);
2. Funciones TABLE en línea
Devuelven una tabla.
Contienen un único SELECT.
Funcionan como una vista parametrizada.

Ejemplo:

SELECT *
FROM dbo.ifTotalVentas(712);
3. Funciones TABLE Multi-sentencia
Devuelven una tabla.
Permiten utilizar varias sentencias SQL.
Se usan cuando la lógica es más compleja.
Modificar o eliminar funciones

Modificar:
ALTER FUNCTION

Eliminar:
DROP FUNCTION

Consulta para visualizar funciones creadas
SELECT definition, type
FROM sys.sql_modules AS m
JOIN sys.objects AS o
ON m.object_id = o.object_id
AND type IN ('FN','IF','TF');

Permite consultar las funciones existentes en la base de datos y conocer su definición y tipo.

Lo más importante para el examen
Funciones nativas: vienen incorporadas en SQL Server.
Funciones matemáticas: ABS, ROUND, CEILING, FLOOR, SIGN.
Funciones de fecha: GETDATE, YEAR, MONTH, DAY, DATENAME, DATEPART, DATEDIFF, DATEADD.
Funciones de texto: LEFT, RIGHT, SUBSTRING, CHARINDEX, REPLACE, LEN, LOWER, UPPER.
Funciones de usuario: se crean con CREATE FUNCTION.
Tipos de funciones de usuario:
Escalares → devuelven un valor.
Table en línea → devuelven una tabla mediante un SELECT.
Table multi-sentencia → devuelven una tabla usando múltiples sentencias SQL.
