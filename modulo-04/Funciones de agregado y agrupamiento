¿Qué son las funciones de agregado?

Son funciones que realizan cálculos sobre un conjunto de registros y devuelven un único resultado. Se utilizan para obtener estadísticas o resúmenes de los datos.

Las funciones principales son:

COUNT()
SUM()
MIN()
MAX()
AVG()

COUNT()

Cuenta la cantidad de registros de una tabla o de una columna.

Sintaxis
SELECT COUNT(*) FROM Productos;
Ejemplo

Obtener la cantidad total de productos.

SELECT COUNT(*) FROM Productos;

También puede combinarse con WHERE.

Ejemplo: contar los productos cuyo nombre contiene "iPhone".

SELECT COUNT(*)
FROM Productos
WHERE Nombre LIKE '%iPhone%';

SUM()

Calcula la suma de todos los valores de una columna numérica.

Sintaxis
SELECT SUM(Stock)
FROM Productos;
Ejemplo

Obtener el stock total de productos.

SELECT SUM(Stock)
FROM Productos;

MIN()

Obtiene el valor mínimo de una columna.

Sintaxis
SELECT MIN(Precio)
FROM Productos;
Ejemplo

Conocer el producto con el menor precio.

SELECT MIN(Precio)
FROM Productos;


MAX()

Obtiene el valor máximo de una columna.

Sintaxis
SELECT MAX(Precio)
FROM Productos;
Ejemplo

Conocer el precio más alto de los productos.

SELECT MAX(Precio)
FROM Productos;

AVG()

Calcula el promedio de una columna numérica.

Sintaxis
SELECT AVG(Precio)
FROM Productos;
Ejemplo

Obtener el precio promedio de los productos.

SELECT AVG(Precio)
FROM Productos;

GROUP BY

La cláusula GROUP BY agrupa registros que tienen un valor en común.

Generalmente se utiliza junto con funciones de agregado como:

COUNT()
SUM()
AVG()
MIN()
MAX()
Sintaxis
SELECT columna, funcion_agregado(columna)
FROM tabla
GROUP BY columna;

Ejemplo

Calcular el stock total por categoría.

SELECT Categoria, SUM(Stock)
FROM Productos
GROUP BY Categoria;

| Categoría  | Stock Total |
| ---------- | ----------: |
| Smartphone |        1250 |
| Impresoras |         380 |
| Notebooks  |         100 |


HAVING

HAVING sirve para filtrar grupos creados con GROUP BY.

La diferencia principal es:

WHERE filtra registros antes del agrupamiento.
HAVING filtra grupos después del agrupamiento.
Sintaxis
SELECT columna, funcion_agregado(columna)
FROM tabla
GROUP BY columna
HAVING condicion;
Ejemplo

Mostrar solamente las categorías cuyo stock total sea mayor a 250.
SELECT Categoria, SUM(Stock)
FROM Productos
GROUP BY Categoria
HAVING SUM(Stock) > 250;

| WHERE                             | HAVING                                                       |
| --------------------------------- | ------------------------------------------------------------ |
| Filtra registros individuales.    | Filtra grupos de registros.                                  |
| Se ejecuta antes del `GROUP BY`.  | Se ejecuta después del `GROUP BY`.                           |
| No utiliza funciones de agregado. | Puede utilizar funciones de agregado (`SUM`, `COUNT`, etc.). |


RESUMEN PARA RECORDAR 
| Función    | ¿Para qué sirve?                  |
| ---------- | --------------------------------- |
| `COUNT()`  | Contar registros                  |
| `SUM()`    | Sumar valores                     |
| `AVG()`    | Calcular promedio                 |
| `MIN()`    | Obtener el valor mínimo           |
| `MAX()`    | Obtener el valor máximo           |
| `GROUP BY` | Agrupar registros por una columna |
| `HAVING`   | Filtrar grupos después de agrupar |

