¿Qué es una variable? Una variable es un espacio de memoria donde se almacena un valor temporal para utilizarlo durante la ejecución de un script, procedimiento o lote. Se declara con DECLARE y se le asigna un valor con SET o SELECT. Si no se inicializa, su valor será NULL.

Declaración de variables

Se utiliza la instrucción DECLARE.

Sintaxis
DECLARE @Contador INT;

También se pueden declarar varias variables al mismo tiempo:

DECLARE @Contador INT,
        @Edad INT;

Inicializar una variable

Hay dos formas principales:

1. Al declararla
DECLARE @Contador INT = 0;
2. Con SET
DECLARE @Mensaje VARCHAR(50);

SET @Mensaje = 'Hola Mundo';

Alcance de las variables

Las variables son locales, es decir:

Solo existen dentro del bloque donde fueron declaradas.
No pueden utilizarse desde otros procedimientos o scripts.

Esto evita conflictos entre variables.

Tipos de datos

Una variable puede tener cualquier tipo de dato válido, por ejemplo:

INT
VARCHAR
DATE
DECIMAL
TABLE

Las variables también pueden utilizarse en estructuras como:

IF
CASE
WHILE

para controlar el flujo del programa.

Inicialización múltiple

Es posible declarar e inicializar varias variables en una sola instrucción.

DECLARE
    @Contador INT = 0,
    @Nombre VARCHAR(50) = 'Juan';

Esto hace que el código sea más limpio y fácil de leer.

Buenas prácticas

El documento recomienda:

Inicializar las variables siempre que sea posible.
Usar nombres descriptivos.
Declarar solo las variables necesarias.

Así se mejora la legibilidad y se evitan errores con valores NULL.

Variables tipo tabla

Una variable tipo tabla permite almacenar datos temporales como si fuera una tabla.

Ejemplo:

DECLARE @VariableTabla TABLE(
    ID INT,
    Apellido VARCHAR(50),
    Nombre VARCHAR(50)
);

Características
Se almacenan temporalmente.
Se crean con DECLARE.
Solo existen durante la ejecución del bloque.
Se eliminan automáticamente cuando finaliza el proceso.
No requieren borrarlas manualmente.

Ventajas de las variables tipo tabla
Tienen un alcance bien definido.
Consumen menos recursos que una tabla temporal.
Generan menos recompilaciones.
No necesitan bloqueos importantes.

Desventajas
No se puede modificar su estructura después de crearla.
No permiten índices avanzados.
No pueden utilizarse con SELECT INTO.
Tienen algunas restricciones respecto a claves e índices.

Variables tipo tabla vs. Tablas temporales
Variables tipo tabla
Mejor para pequeñas cantidades de datos.
Más rápidas para operaciones simples.
Se eliminan automáticamente.
Tablas temporales
Mejor para grandes volúmenes de datos.
Permiten crear índices.
Son recomendables cuando la información se utilizará muchas veces.

El documento concluye que, en general, conviene usar variables tipo tabla, salvo cuando se manejan grandes cantidades de datos y se necesitan índices.

VARIABLES GLOBALES DEL SISTEMA

| Variable        | ¿Qué devuelve?                                         |
| --------------- | ------------------------------------------------------ |
| `@@ROWCOUNT`    | Cantidad de filas afectadas por la última instrucción. |
| `@@IDENTITY`    | Último valor IDENTITY generado.                        |
| `@@SERVERNAME`  | Nombre del servidor SQL Server.                        |
| `@@SPID`        | Identificador de la sesión actual.                     |
| `@@VERSION`     | Versión de SQL Server instalada.                       |
| `@@LANGUAGE`    | Idioma configurado para la sesión.                     |
| `@@SERVICENAME` | Nombre del servicio de SQL Server.                     |

Lo más importante para recordar
DECLARE → Declara una variable.
SET → Asigna un valor a una variable.
Las variables locales solo existen dentro del bloque donde se crean.
Si no se inicializan, comienzan con valor NULL.
Las variables tipo tabla almacenan datos temporales y son ideales para conjuntos pequeños de información.
Las tablas temporales son más adecuadas cuando se trabaja con grandes volúmenes de datos.
Las variables globales (@@ROWCOUNT, @@IDENTITY, @@VERSION, etc.) proporcionan información del sistema y de la sesión actual.
