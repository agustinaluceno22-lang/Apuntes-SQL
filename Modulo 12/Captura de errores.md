¿Qué es la captura de errores?
La captura de errores es el proceso de detectar, controlar y gestionar los errores que ocurren durante la ejecución de instrucciones o transacciones en SQL Server.
Su objetivo es evitar que la base de datos quede en un estado inconsistente y facilitar la identificación del problema.

¿Para qué sirve?
La captura de errores permite:
✅ Detectar y gestionar errores de forma controlada.
✅ Facilitar el diagnóstico y la depuración.
✅ Mantener la consistencia de los datos.
✅ Revertir transacciones cuando ocurre un error.

TRY...CATCH

Es el mecanismo recomendado por SQL Server para controlar errores.
Su funcionamiento es similar al manejo de excepciones de otros lenguajes de programación.

Estructura
BEGIN TRY

    -- Código

END TRY

BEGIN CATCH

    -- Manejo del error

END CATCH

Si ocurre un error dentro del bloque TRY, la ejecución pasa automáticamente al bloque CATCH.

Ejemplo con transacciones
BEGIN TRY

    BEGIN TRANSACTION

    INSERT INTO Errores(id)
    VALUES(1);

    UPDATE Errores
    SET Valor = 1/0;

    COMMIT;

END TRY

BEGIN CATCH

    ROLLBACK;
    THROW;

END CATCH

En este ejemplo:

ocurre una división por cero;
la transacción se revierte con ROLLBACK;
el error se vuelve a lanzar mediante THROW.
Funcionamiento de TRY...CATCH
Si NO hay errores
TRY
 ↓
Ejecuta todas las instrucciones
 ↓
END TRY
 ↓
Continúa el programa normalmente
Si ocurre un error
TRY
 ↓
Error
 ↓
CATCH
 ↓
Maneja el error
 ↓
Continúa la ejecución

Características importantes
Detecta errores de ejecución con gravedad superior a 10.
El bloque CATCH debe ir inmediatamente después del TRY.
Puede utilizarse dentro de procedimientos almacenados.
Se pueden anidar bloques TRY...CATCH.
No puede utilizarse dentro de funciones definidas por el usuario.

Funciones para obtener información del error

Dentro del bloque CATCH existen funciones que permiten conocer los detalles del error.
| Función             | Devuelve                    |
| ------------------- | --------------------------- |
| `ERROR_NUMBER()`    | Número del error            |
| `ERROR_SEVERITY()`  | Nivel de gravedad           |
| `ERROR_STATE()`     | Estado del error            |
| `ERROR_PROCEDURE()` | Procedimiento donde ocurrió |
| `ERROR_LINE()`      | Línea del error             |
| `ERROR_MESSAGE()`   | Mensaje completo del error  |
Estas funciones solo funcionan dentro del bloque CATCH.

Ejemplo
BEGIN TRY

SELECT 1/0;

END TRY

BEGIN CATCH

SELECT ERROR_NUMBER();

END CATCH

Resultado:

8134

@@ERROR

@@ERROR es una variable del sistema que devuelve el código del error producido por la última instrucción SQL ejecutada.

Si no hubo errores:

@@ERROR = 0

Actualmente sigue existiendo, pero el PDF indica que la mejor práctica es utilizar TRY...CATCH, ya que es una solución más moderna y robusta.

THROW

THROW genera una excepción o vuelve a lanzar el error capturado.

Ejemplo:

BEGIN CATCH

ROLLBACK;

THROW;

END CATCH
Consideraciones
La instrucción anterior debe terminar con ;.
Cuando se utiliza sin parámetros debe estar dentro de un CATCH.
Finaliza el lote de instrucciones.

RAISERROR

Permite crear mensajes de error personalizados.

Ejemplo:

RAISERROR(
'Este es un error personalizado',
16,
1
);

Parámetros principales:

Mensaje → texto del error.
Severidad → nivel de gravedad.
Estado → identificador del error.

Limitaciones de RAISERROR

El PDF indica que:

Tiene una sintaxis más compleja.
Es una característica anterior a SQL Server 2012.
Se recomienda utilizar THROW en desarrollos nuevos.

Diferencias entre RAISERROR y THROW
| RAISERROR                           | THROW                          |
| ----------------------------------- | ------------------------------ |
| Más antiguo                         | Introducido en SQL Server 2012 |
| Requiere severidad y estado         | Sintaxis más simple            |
| Permite mensajes dinámicos (%s, %d) | Solo texto estático            |
| Debe reconstruir el error           | Puede relanzarlo con `THROW;`  |
| Puede quedar obsoleto               | Recomendado actualmente        |

Vista del sistema: sys.messages

sys.messages es una vista de catálogo que almacena todos los mensajes de error del sistema y los personalizados.

Consulta:

SELECT *
FROM sys.messages;

Columnas importantes de sys.messages
| Columna           | Descripción                     |
| ----------------- | ------------------------------- |
| `message_id`      | Identificador del mensaje       |
| `language_id`     | Idioma                          |
| `severity`        | Nivel de gravedad               |
| `is_event_logged` | Indica si se registra en el log |
| `text`            | Texto del mensaje               |


RESUMEN RAPIDO 
| Concepto          | Función                                                     |
| ----------------- | ----------------------------------------------------------- |
| `TRY`             | Ejecuta el código protegido                                 |
| `CATCH`           | Captura el error                                            |
| `ERROR_MESSAGE()` | Devuelve el mensaje del error                               |
| `ERROR_NUMBER()`  | Devuelve el código del error                                |
| `THROW`           | Relanza una excepción                                       |
| `RAISERROR`       | Genera un error personalizado                               |
| `@@ERROR`         | Devuelve el error de la última instrucción (método antiguo) |
| `sys.messages`    | Contiene los mensajes de error del sistema                  |
