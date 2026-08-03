Conversión de Tipos de Datos en SQL Server
¿Qué es la conversión de tipos de datos?
La conversión de tipos de datos es el proceso de transformar un valor de un tipo de dato a otro.

Se utiliza cuando:
Se comparan datos de distintos tipos.
Se realizan cálculos.
Se importan o exportan datos.
Se necesita mostrar información con un formato determinado.
Tipos de Conversión

SQL Server permite dos tipos de conversión:
Conversión implícita
Conversión explícita
Conversión Implícita

La realiza automáticamente SQL Server, sin que el usuario tenga que escribir ninguna función.
Características
No es visible para el usuario.
Ocurre cuando la conversión es compatible.
Si los tipos no son compatibles puede producir un error.

Ejemplo:

DECLARE @intValue INT = 10;
DECLARE @floatValue FLOAT;

SET @floatValue = @intValue;

SELECT @floatValue;

Resultado:

10.0

En este caso SQL Server convierte automáticamente un INT en FLOAT.

Conversión Explícita

La conversión explícita ocurre cuando el programador indica de forma manual cómo convertir un dato utilizando funciones específicas.

Las funciones más utilizadas son:

CAST()
CONVERT()
CAST()

Convierte un dato de un tipo a otro siguiendo el estándar ANSI.

Sintaxis
CAST(expresión AS tipo_de_dato)
Ejemplo
SELECT CAST(123.45 AS INT);

Resultado:

123

También puede utilizarse para convertir fechas o números en texto.

CONVERT()

Realiza la conversión entre tipos de datos y permite especificar un formato, especialmente útil para trabajar con fechas.

Sintaxis
CONVERT(tipo_de_dato, expresión, estilo)
Ejemplo
SELECT CONVERT(VARCHAR, GETDATE(), 103);

Resultado:

17/01/2025

El tercer parámetro (103) indica el formato de la fecha.

¿Para qué sirve la conversión?

Las conversiones son útiles para:

Validar datos.
Importar y exportar información.
Normalizar tipos de datos.
Dar formato a fechas y números.
Compatibilizar datos de distintos tipos.
¿Cuándo se utilizan CAST y CONVERT?

Estas funciones se utilizan cuando:

Se comparan datos de distintos tipos.
Se combinan columnas con diferentes tipos de datos.
Se asignan valores a variables.
Se trabajan parámetros y resultados de procedimientos almacenados.
Se necesita convertir datos entre SQL Server y aplicaciones externas.
Ejemplos de CAST
Convertir decimal a entero
SELECT CAST(9.5 AS INT);

Resultado:

9
Convertir decimal a DECIMAL
SELECT CAST(9.5 AS DECIMAL(6,4));

Resultado:

9.5000

Ejemplo práctico de CAST

Si intentamos concatenar un texto con un número:

DECLARE @Anio INT = 2018;

PRINT 'Año:' + @Anio;

Se produce un error de conversión.

La forma correcta es convertir primero el número a texto:

DECLARE @Anio INT = 2018;

PRINT 'Año:' + CAST(@Anio AS VARCHAR);

Resultado:

Año:2018

Formatos de fecha con CONVERT

CONVERT() permite mostrar una misma fecha con distintos formatos utilizando un código de estilo.

Ejemplo:

SELECT
CONVERT(VARCHAR, GETDATE(), 101),
CONVERT(VARCHAR, GETDATE(), 103),
CONVERT(VARCHAR, GETDATE(), 105),
CONVERT(VARCHAR, GETDATE(), 111),
CONVERT(VARCHAR, GETDATE(), 112);


Formatos obtenidos:
| Código | Formato    |
| ------ | ---------- |
| 101    | MM/DD/YYYY |
| 103    | DD/MM/YYYY |
| 105    | DD-MM-YYYY |
| 111    | YYYY/MM/DD |
| 112    | YYYYMMDD   |

Diferencias entre CAST y CONVERT
| CAST                                    | CONVERT                                       |
| --------------------------------------- | --------------------------------------------- |
| Sigue el estándar ANSI.                 | Es específico de SQL Server.                  |
| Convierte un tipo de dato a otro.       | Convierte y permite aplicar formatos.         |
| Se utiliza para conversiones generales. | Muy útil para trabajar con fechas y formatos. |


Conversión implícita: SQL Server convierte los datos automáticamente.
Conversión explícita: el programador indica cómo convertir el dato.
CAST() → convierte un dato de un tipo a otro.
CONVERT() → convierte datos y permite aplicar formatos, especialmente en fechas.
Si se concatena un número con un texto, primero hay que convertir el número a VARCHAR usando CAST() o CONVERT().
Los códigos de estilo de CONVERT() permiten mostrar las fechas en diferentes formatos (101, 103, 105, 111, 112).
