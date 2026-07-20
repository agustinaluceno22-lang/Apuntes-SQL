¿Qué son las operaciones DML? Las operaciones DML permiten trabajar con los datos almacenados en las tablas sin modificar su estructura.
Las principales instrucciones son:

INSERT → Agrega registros.
UPDATE → Modifica registros.
DELETE → Elimina registros.
TRUNCATE TABLE → Elimina todos los registros de una tabla de forma rápida.
INSERT

Se utiliza para agregar una o varias filas a una tabla.

Insertar una fila
INSERT INTO Sectores
VALUES ('Finanzas','Contaduría');
Insertar varias filas
INSERT INTO Sectores
VALUES
('Finanzas','Cobranzas'),
('Finanzas','Ventas');
Insertar indicando las columnas

Se usa cuando no se completan todas las columnas o cuando el orden es diferente.

INSERT INTO Sectores (Sector, Gerencia)
VALUES ('Legales','Finanzas');
DEFAULT VALUES

Inserta únicamente los valores predeterminados definidos en la tabla.

INSERT INTO Sectores
DEFAULT VALUES;
INSERT con SELECT

Permite copiar datos desde otra tabla.

INSERT INTO Sectores (Gerencia, Sector)
SELECT Name, GroupName
FROM HumanResources.Department;
Columnas IDENTITY

Una columna IDENTITY genera automáticamente un número consecutivo.

Ejemplo:

SectorID INT IDENTITY(1,1)

Si se quiere insertar manualmente un valor en esa columna, primero hay que habilitar:

SET IDENTITY_INSERT Sectores ON;

y luego deshabilitarla:

SET IDENTITY_INSERT Sectores OFF;

SELECT INTO

Sirve para crear una tabla nueva copiando los resultados de una consulta.

Ejemplo:

SELECT *
INTO NuevaTabla
FROM Productos;

Es útil para crear tablas temporales o realizar copias de datos.

UPDATE

Se utiliza para modificar datos existentes.

Actualizar una columna
UPDATE Productos
SET Precio = Precio * 2;
Actualizar varias columnas
UPDATE Empleados
SET Bonus = 6000,
    CommissionPct = 1.10;
Actualizar con WHERE

Muy importante.

UPDATE Productos
SET Color = 'Rojo'
WHERE Color = 'Red';

Si no colocas WHERE, se modificarán todas las filas.

Actualizar con valores DEFAULT
UPDATE Location
SET CostRate = DEFAULT;
UPDATE con TOP

Permite actualizar solo una cantidad determinada de registros.

UPDATE TOP (10)
Empleado
SET VacationHours = VacationHours + 8;
UPDATE con JOIN

Permite actualizar una tabla utilizando datos de otra.

UPDATE s
SET Sector = sn.SectorNuevo
FROM Sectores s
INNER JOIN SectoresNuevo sn
ON s.Sector = sn.Sector;
DELETE

Elimina registros de una tabla.

Eliminar todos los registros
DELETE FROM Empleados;

⚠️ Sin WHERE, elimina todos los registros.

Eliminar con WHERE
DELETE FROM Productos
WHERE Precio > 1000;
DELETE con JOIN

También se pueden eliminar registros relacionados con otra tabla.

DELETE s
FROM Sectores s
INNER JOIN SectoresNuevo sn
ON s.Sector = sn.Sector;
TRUNCATE TABLE

Elimina todos los registros de una tabla de forma mucho más rápida que DELETE.

TRUNCATE TABLE Sectores

DIFERENCIA ENTRE TRUNCATE Y DELETE 

| DELETE                      | TRUNCATE                   |
| --------------------------- | -------------------------- |
| Elimina una o varias filas. | Elimina todas las filas.   |
| Puede usar `WHERE`.         | No permite `WHERE`.        |
| Es más lento.               | Es más rápido.             |
| Registra cada eliminación.  | No registra fila por fila. |
| Activa triggers.            | No activa triggers.        |

Lo más importante para recordar
INSERT → Agrega registros.
UPDATE → Modifica registros.
DELETE → Elimina registros.
TRUNCATE TABLE → Borra todos los registros rápidamente.
SELECT INTO → Crea una tabla nueva con el resultado de una consulta.
Siempre utiliza WHERE en UPDATE y DELETE cuando quieras modificar o eliminar solo algunos registros. Sin esa cláusula, la operación afectará toda la tabla.
