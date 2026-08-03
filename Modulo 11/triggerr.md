TRIGGERS en SQL Server
¿Qué es un TRIGGER?

Un TRIGGER (disparador) es un objeto de SQL Server que contiene instrucciones SQL y se ejecuta automáticamente cuando ocurre un evento específico en la base de datos.

Se utilizan para:

Aplicar reglas de negocio.
Validar datos automáticamente.
Mantener la integridad de los datos.
Realizar auditorías.
Ejecutar acciones automáticas.
Tipos de TRIGGER

Existen dos tipos principales:

TRIGGER DML
TRIGGER DDL
TRIGGER DML (Data Manipulation Language)

Se ejecuta cuando se modifican los datos de una tabla o vista.

Se activa con las sentencias:

INSERT
UPDATE
DELETE
Usos principales
Mantener la integridad de los datos.
Mantener la integridad referencial.
Registrar cambios automáticamente.
TRIGGER DDL (Data Definition Language)

Se ejecuta cuando cambia la estructura de la base de datos.

Se activa con sentencias como:
CREATE
ALTER
DROP

DIFERENCIAS ENTRE TRIGGER DML Y DDL
| TRIGGER DML                            | TRIGGER DDL                                            |   |
| -------------------------------------- | ------------------------------------------------------ | - |
| Actúa sobre los datos.                 | Actúa sobre la estructura de la base de datos.         |   |
| Eventos: `INSERT`, `UPDATE`, `DELETE`. | Eventos: `CREATE`, `ALTER`, `DROP`, `GRANT`, `REVOKE`. |   |
| Se asocia a tablas o vistas.           | Se asocia a eventos de la base de datos.               |   |
| Mantiene la integridad de los datos.   | Controla cambios en la estructura.                     |   |
Usos principales
Auditar cambios en la base de datos.


Tipos de TRIGGER DML

Existen dos tipos:

AFTER TRIGGER
INSTEAD OF TRIGGER
AFTER TRIGGER

Es el tipo de trigger predeterminado en SQL Server.

Características
Se ejecuta después del evento.
Puede activarse luego de un:
INSERT
UPDATE
DELETE
Puede haber varios AFTER TRIGGER para la misma tabla.
No se ejecuta con SELECT.
Puede ser recursivo (hasta 32 niveles).
INSTEAD OF TRIGGER

Se ejecuta antes de que SQL Server realice la operación.

Características
Intercepta:
INSERT
UPDATE
DELETE
Solo puede existir uno por acción (INSERT, UPDATE o DELETE) en una misma tabla o vista.
Es útil para permitir modificaciones en vistas que normalmente no serían modificables.
No puede combinarse con claves foráneas que tengan eliminación o actualización en cascada.
Crear un TRIGGER para INSERT

Se ejecuta cuando se insertan registros.

Ejemplo:

CREATE TRIGGER TR_Prueba
ON dbo.Prueba
AFTER INSERT
AS
BEGIN
    INSERT INTO dbo.CopiaPrueba
    SELECT * FROM inserted;
END

La tabla especial inserted contiene los registros recién insertados.

Crear un TRIGGER para UPDATE

Se ejecuta cuando se modifican registros.

Ejemplo:

CREATE TRIGGER TR_Prueba
ON dbo.Prueba
AFTER UPDATE
AS
BEGIN
    UPDATE p
    SET Nombre = i.Nombre
    FROM dbo.CopiaPrueba p
    INNER JOIN inserted i
        ON p.Codigo = i.Codigo;
END

La tabla inserted contiene los nuevos valores después del UPDATE.

Crear un TRIGGER para DELETE

Se ejecuta cuando se eliminan registros.

Ejemplo:

CREATE TRIGGER TR_Prueba
ON dbo.Prueba
AFTER DELETE
AS
BEGIN
    DELETE FROM dbo.CopiaPrueba
    FROM dbo.CopiaPrueba p
    INNER JOIN deleted d
        ON p.Codigo = d.Codigo;
END

La tabla deleted contiene los registros eliminados.

Tablas especiales
inserted

Contiene los registros insertados o los nuevos valores después de un UPDATE.

deleted

Contiene los registros eliminados o los valores anteriores antes de un UPDATE. Estas tablas son utilizadas dentro de los triggers para acceder a los datos afectados.

Limitaciones de los TRIGGERS
CREATE TRIGGER debe ser la primera instrucción del lote.
Se crea únicamente en la base de datos actual.
Puede responder a más de un evento (INSERT y UPDATE, por ejemplo).
Los INSTEAD OF DELETE y INSTEAD OF UPDATE no pueden definirse en tablas con claves foráneas en cascada.
Se recomienda evitar instrucciones SELECT que devuelvan resultados dentro de un trigger.
Si se realizan asignaciones de variables, conviene usar:
SET NOCOUNT ON;

para evitar devolver resultados innecesarios.

Importante sobre TRUNCATE

Aunque TRUNCATE TABLE elimina todos los registros de una tabla, no activa los TRIGGER DELETE, ya que no elimina las filas una por una ni registra cada eliminación individual.

Lo más importante para el examen
Un TRIGGER se ejecuta automáticamente cuando ocurre un evento.
TRIGGER DML → trabaja con datos (INSERT, UPDATE, DELETE).
TRIGGER DDL → trabaja con la estructura (CREATE, ALTER, DROP).
AFTER TRIGGER → se ejecuta después del evento.
INSTEAD OF TRIGGER → reemplaza la operación antes de que ocurra.
inserted contiene los registros nuevos.
deleted contiene los registros eliminados o los valores anteriores.
TRUNCATE TABLE no dispara un TRIGGER DELETE.
Ejecutar acciones automáticas (por ejemplo, enviar un correo).
