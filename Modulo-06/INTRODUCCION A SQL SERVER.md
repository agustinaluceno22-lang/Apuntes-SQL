Introducción a SQL Server
¿Qué es SQL Server? SQL Server es un Sistema de Gestión de Bases de Datos Relacionales (SGBD) desarrollado por Microsoft.

Su función principal es:
Almacenar datos.
Administrar información.
Procesar consultas.
Mantener la seguridad e integridad de los datos.

El motor de base de datos funciona como un servicio que almacena y procesa la información.

Características principales
✅ Almacenamiento en tablas relacionadas.
✅ Utiliza Transact-SQL (T-SQL).
✅ Seguridad mediante autenticación y permisos.
✅ Alta disponibilidad (replicación, clustering, Always On).
Usos
Gestión empresarial.
Business Intelligence (BI).
Análisis de datos.
Historia de SQL
1970: IBM desarrolla SQL (antes llamado SEQUEL).
1986: ANSI publica el estándar SQL.
1989: aparece SQL-89.
1992: SQL-92 se convierte en el estándar.
Microsoft continúa desarrollando SQL Server agregando nuevas funciones.
¿Qué es T-SQL?

Transact-SQL (T-SQL) es el lenguaje propio de SQL Server.

Está basado en SQL estándar, pero agrega funcionalidades de programación.

Diferencias con SQL

SQL estándar tiene comandos básicos:

SELECT
INSERT
UPDATE
DELETE

T-SQL agrega:

Procedimientos almacenados.
Funciones.
Variables (DECLARE).
IF...ELSE.
WHILE.
CASE.
TRY...CATCH para manejo de errores.
Ventajas de T-SQL
Mayor velocidad.
Menor tráfico de red.
Reutilización del código.
Más seguridad.
Permite programación más compleja.
Bases de datos del sistema

Son creadas automáticamente por SQL Server.

Master

Es la base más importante.

Guarda:

Información del servidor.
Usuarios.
Configuración.
Información de todas las bases de datos.

👉 Si Master falla, SQL Server no puede iniciar.

MSDB

Se utiliza para:

Jobs.
Planes de mantenimiento.
Alertas.
Historial de tareas.
TEMPDB

Almacena:

Tablas temporales.
Resultados intermedios.
Objetos temporales.

Se recrea cada vez que inicia SQL Server.

MODEL

Es una plantilla.

Cada vez que se crea una nueva base de datos, copia la configuración de MODEL.

Resource

Contiene recursos internos utilizados por SQL Server.

Autenticación

SQL Server posee dos modos.

Windows Authentication
Utiliza usuarios de Windows.
Es el método recomendado.
Es más seguro.
Mixed Mode

Permite:

Usuarios de Windows.
Usuarios propios de SQL Server.

Necesita usuario y contraseña.

Lenguajes de SQL
DDL (Data Definition Language)

Sirve para crear o modificar estructuras.

Comandos:

CREATE
ALTER
DROP
TRUNCATE

👉 Modifica la estructura.

DML (Data Manipulation Language)

Manipula los datos.

Comandos:

SELECT
INSERT
UPDATE
DELETE
MERGE

👉 Modifica los registros.

DCL (Data Control Language)

Controla permisos.

Comandos:

GRANT
DENY
REVOKE
TCL (Transaction Control Language)

Controla transacciones.

Comandos:

BEGIN TRAN
COMMIT
ROLLBACK
Diseño de una Base de Datos

Es el proceso de planificar cómo se almacenarán los datos.

Un buen diseño permite:

Mejor rendimiento.
Mayor organización.
Fácil mantenimiento.
Integridad de la información.
Tablas

Las tablas almacenan la información.

Están formadas por:

Columnas (campos) → atributos.
Filas (registros) → datos.

Características:

Cada tabla tiene un nombre único.
Puede haber muchas tablas en una base de datos.
Restricciones

Sirven para mantener la calidad de los datos.

Ejemplos:

No repetir nombres de columnas.
La clave primaria no puede repetirse.
Mantener la integridad de los datos.
Primary Key (Clave primaria)

Identifica cada registro de manera única.

Características:

Solo una por tabla.
No acepta NULL.
No acepta valores duplicados.

Ejemplo:

ID	Nombre
1	Juan
2	Ana

El ID es la Primary Key.

Foreign Key (Clave foránea)

Relaciona dos tablas.

Hace referencia a la Primary Key de otra tabla.

Sirve para mantener la integridad entre tablas.

Ejemplo:

Clientes

ID	Nombre
1	Juan

Pedidos

IDPedido	IDCliente
10	1

IDCliente es una Foreign Key.

SELECT

Se utiliza para consultar datos.

Consultar toda una tabla:

SELECT * FROM Clientes;

Consultar una columna:

SELECT Nombre
FROM Clientes;
TOP

Devuelve los primeros registros.

SELECT TOP 10 *
FROM Productos;
OFFSET

Salta una cantidad de registros.

SELECT ProductID
FROM Productos
ORDER BY ProductID
OFFSET 10 ROWS;
FETCH NEXT

Obtiene una cantidad determinada de filas.

SELECT ProductID
FROM Productos
ORDER BY ProductID
OFFSET 10 ROWS
FETCH NEXT 5 ROWS ONLY;
Comentarios

Comentario de una línea:

-- Esto es un comentario

Comentario de varias líneas:

/*
Comentario
de varias
líneas
*/
Alias

Permiten cambiar el nombre que aparece en el resultado.

Ejemplo:

SELECT Name AS Producto
FROM Production.Product;

Resultado:

Producto
Notebook
Mouse
⭐ Lo más importante para el examen

✅ Qué es SQL Server.

✅ Qué es T-SQL y en qué se diferencia de SQL.

✅ Bases de datos del sistema:

Master
MSDB
TEMPDB
MODEL

✅ Tipos de autenticación.

✅ Diferencias entre:

DDL
DML
DCL
TCL

✅ Qué es una tabla.

✅ Diferencia entre Primary Key y Foreign Key.

✅ SELECT.

✅ TOP.

✅ OFFSET y FETCH.

✅ Comentarios.

✅ Alias.

📝 Truco para memorizar
DDL → Define la estructura.
DML → Manipula los datos.
DCL → Controla permisos.
TCL → Controla transacciones.

Y para las claves:

🔑 Primary Key = identifica únicamente cada fila.
🔗 Foreign Key = conecta una tabla con otra.
