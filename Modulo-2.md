1. ¿Qué es un esquema (Schema)? Un Schema es un contenedor donde se organizan los objetos de una base de datos.
Dentro de un schema pueden existir:
Tablas
Vistas
Procedimientos almacenados
Funciones

Ejemplo:
SQL
Production.Product
Production → Schema
Product → Tabla

2. Sentencia USE Sirve para indicar sobre qué base de datos vamos a trabajar.
Sintaxis: USE AdventureWorks2019;
GO
Después de ejecutar esa línea, todas las consultas se realizarán sobre esa base.

SELECT Es el comando más utilizado. Sirve para obtener información de una tabla.
Sintaxis:
SELECT columna
FROM tabla;
Ejemplo:
SQL
SELECT Name
FROM Production.Product;
Obtiene únicamente la columna Name.

SELECT *

El asterisco significa:

"Traeme todas las columnas"

Ejemplo:

SELECT *
FROM Production.Product;

Devuelve toda la información de la tabla.

⚠️ En proyectos reales no se recomienda usar * porque trae datos innecesarios y hace las consultas más lentas.

5. ELEGIR VARIAS COLUMNAS
Podemos indicar exactamente qué columnas queremos.
Ejemplo:
SELECT Name,
       ProductNumber,
       Color
FROM Production.Product;

6. ALIAS (AS) Permite cambiar el nombre que aparece en el resultado.
Ejemplo:
SELECT Name AS Producto
FROM Production.Product;
Resultado:Producto
Chain
Seat
Pedal
También funciona sin escribir AS:

SELECT Name Producto
FROM Production.Product;

7. DISTINCT Sirve para eliminar valores repetidos.
Ejemplo
Si una columna tiene:
Rojo
Rojo
Azul
Negro
Azul
Con:
SELECT DISTINCT Color
FROM Production.Product;
Obtendremos:
Rojo
Azul
Negro
Muy utilizado para conocer los valores diferentes de una columna.

8. TOP Limita la cantidad de registros.
Ejemplo:

SELECT TOP 10 *
FROM Production.Product;
Trae solamente los primeros diez registros.
También puede usarse con porcentaje:

SELECT TOP 20 PERCENT *
FROM Production.Product;
Trae el 20% de los registros.

9. ORDER BY Sirve para ordenar los resultados.
Ascendente:
SELECT *
FROM Production.Product
ORDER BY Name;
o
ORDER BY Name ASC;
Descendente:
SELECT *
FROM Production.Product
ORDER BY Name DESC;

10. ORDER BY con varias columnas
Ejemplo:
SELECT *
FROM Production.Product
ORDER BY Color, Name;
Primero ordena por Color.
Si dos productos tienen el mismo Color, los ordena por Name.

11. ASC y DESC - ASC significa: Ascendente
Ejemplo:
A
B
C
D
DESC significa:Descendente
Ejemplo:
D
C
B
A

12. SELECT TOP + ORDER BY
Es muy común combinar ambos.
Ejemplo:
SELECT TOP 5 Name,
              ListPrice
FROM Production.Product
ORDER BY ListPrice DESC;

Obtiene los cinco productos más caros.

Ejemplos importantes 
Mostrar todos los productos
SELECT *
FROM Production.Product;

Mostrar solamente nombre y precio
SELECT Name,
       ListPrice
FROM Production.Product;

Mostrar colores sin repetir
SELECT DISTINCT Color
FROM Production.Product;

Mostrar los primeros 20 productos
SELECT TOP 20 *
FROM Production.Product;

Productos ordenados alfabéticamente
SELECT Name
FROM Production.Product
ORDER BY Name;

Productos más caros
SELECT TOP 10 Name,
              ListPrice
FROM Production.Product
ORDER BY ListPrice DESC;

Conceptos que deberías recordar: Comando	¿Para qué sirve?
USE	Seleccionar la base de datos

SELECT	Consultar datos
SELECT *	Traer todas las columnas
DISTINCT	Eliminar valores repetidos
TOP	Limitar la cantidad de filas
ORDER BY	Ordenar resultados
ASC	Orden ascendente
DESC	Orden descendente
AS	Cambiar el nombre de una columna (alias)

