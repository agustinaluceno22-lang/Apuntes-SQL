Transacciones Explícitas
¿Qué es una transacción?
Una transacción es un conjunto de una o más operaciones sobre la base de datos que se ejecutan como una única unidad de trabajo.
Características:

Se ejecutan completamente o no se ejecutan.
Garantizan la integridad y consistencia de los datos.
Agrupan operaciones como:
INSERT
UPDATE
DELETE

Una transacción es atómica: si ocurre un error, todos los cambios pueden deshacerse.

¿Para qué sirven las transacciones
Las transacciones permiten:

✅ Mantener la integridad de los datos.
✅ Revertir cambios con ROLLBACK.
✅ Evitar operaciones incompletas.
✅ Controlar el acceso simultáneo de varios usuarios.
✅ Ejecutar operaciones críticas de forma segura (ej. transferencias bancarias).
Transacciones explícitas

Se controlan manualmente.

Comienzan con:
BEGIN TRANSACTION

Finalizan con:

COMMIT

o

ROLLBACK
Flujo
BEGIN TRANSACTION
       ↓
Ejecutar consultas
       ↓
¿Todo salió bien?
       ↓
Sí → COMMIT
No → ROLLBACK

COMMIT

Confirma todos los cambios realizados dentro de la transacción.

BEGIN TRANSACTION;

DELETE FROM Tabla
WHERE Id = 10;

COMMIT;

Después del COMMIT, los cambios quedan guardados definitivamente.

ROLLBACK

Deshace todos los cambios realizados desde que comenzó la transacción.

BEGIN TRANSACTION;

INSERT INTO Clientes
VALUES (1,'Juan');

ROLLBACK;

El registro nunca queda almacenado.

Nombrar una transacción

También es posible asignarle un nombre.

BEGIN TRANSACTION Candidatos;

DELETE FROM HumanResources.JobCandidate
WHERE JobCandidateID = 13;

COMMIT TRANSACTION Candidatos;

Esto mejora la legibilidad del código.

Propiedades ACID

Las transacciones cumplen cuatro propiedades fundamentales.

A - Atomicidad

Todo o nada.

Si una operación falla:

ninguna modificación queda guardada.
C - Consistencia

La base de datos siempre pasa de un estado válido a otro estado válido.

Respeta:

Constraints
Triggers
Reglas del negocio
I - Isolation (Aislamiento)

Cada transacción trabaja de manera independiente.

Aunque existan varios usuarios ejecutando operaciones al mismo tiempo, las transacciones no interfieren entre sí.

D - Durabilidad

Una vez realizado el COMMIT, los datos permanecen guardados incluso ante:

cortes de energía
fallos del sistema
reinicios del servidor

Niveles de aislamiento

Determinan cómo interactúan varias transacciones ejecutándose al mismo tiempo.

READ UNCOMMITTED
Menor seguridad.
Permite leer datos que aún no fueron confirmados.
Puede producir lecturas sucias (Dirty Reads).
READ COMMITTED

Nivel por defecto de SQL Server.

No permite leer datos sin confirmar.
Evita las lecturas sucias.
REPEATABLE READ

Más restrictivo.

Impide que otros usuarios modifiquen o eliminen registros ya leídos hasta finalizar la transacción.

SNAPSHOT

La transacción trabaja con una "fotografía" de los datos al momento de comenzar.

No ve cambios realizados posteriormente por otras transacciones.

SERIALIZABLE

Es el nivel más estricto.

Además de bloquear modificaciones, impide insertar nuevas filas dentro del rango leído hasta que finalice la transacción.

Transacciones implícitas

En este modo SQL Server inicia automáticamente una transacción cuando se ejecuta una operación como:

INSERT
UPDATE
DELETE

No es necesario escribir:

BEGIN TRANSACTION

Se activa con:

SET IMPLICIT_TRANSACTIONS ON;

Se desactiva con:

SET IMPLICIT_TRANSACTIONS OFF;

SAVE TRANSACTION

Permite crear un punto de retorno dentro de una transacción.

BEGIN TRAN;

INSERT INTO Productos VALUES (...);

SAVE TRAN Registro;

INSERT INTO ProductosLog VALUES (...);

ROLLBACK TRAN Registro;

UPDATE Productos
SET Precio = 100;

COMMIT;

En este caso:

✔ El producto permanece.
❌ El registro del log se elimina.

Solo se deshacen las operaciones realizadas después del SAVE TRANSACTION

DIFERENCIAS IMPORTANTES
| Instrucción         | Función                            |
| ------------------- | ---------------------------------- |
| `BEGIN TRANSACTION` | Inicia una transacción             |
| `COMMIT`            | Guarda definitivamente los cambios |
| `ROLLBACK`          | Deshace los cambios realizados     |
| `SAVE TRANSACTION`  | Crea un punto de retorno parcial   |

Lo más importante para recordar
Una transacción ejecuta varias operaciones como una sola unidad.
Si todo sale bien → COMMIT.
Si ocurre un error → ROLLBACK.
Las propiedades ACID garantizan confiabilidad.
Existen cinco niveles de aislamiento:
READ UNCOMMITTED
READ COMMITTED
REPEATABLE READ
SNAPSHOT
SERIALIZABLE
SAVE TRANSACTION permite revertir solo una parte de la transacción.
Las transacciones implícitas pueden iniciarse automáticamente con SET IMPLICIT_TRANSACTIONS ON
