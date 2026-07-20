¿Qué es una subconsulta? Una subconsulta es una consulta SQL que está dentro de otra consulta (SELECT, INSERT, UPDATE o DELETE). Sirve para obtener un resultado que luego utiliza la consulta principal.

Ejemplo:
SELECT *
FROM Productos
WHERE Precio > (
    SELECT AVG(Precio)
    FROM Productos
);
¿Dónde se pueden usar?
En el SELECT
Se utiliza para mostrar un valor calculado junto con cada fila, por ejemplo el precio promedio de todos los productos.
En el FROM

La subconsulta funciona como si fuera una tabla temporal sobre la que luego se pueden hacer JOIN.

En el WHERE
Es el uso más común. Permite filtrar registros según el resultado de otra consulta.
Ejemplo:

SELECT *
FROM Productos
WHERE Precio <
(
    SELECT AVG(Precio)
    FROM Productos
);
Restricciones de las subconsultas
Siempre van entre paréntesis.
Deben devolver el tipo de dato esperado por la consulta principal.
Cuando se usa un operador de comparación (=, >, <, etc.), normalmente deben devolver un solo valor.
Solo se puede usar ORDER BY junto con TOP.
Subconsultas correlacionadas

Son subconsultas que dependen de la consulta principal.

Se ejecutan una vez por cada fila de la consulta externa, por lo que suelen ser más lentas que una subconsulta simple.

Ejemplo:

Obtener el producto más barato de cada categoría.

Operador IN

Comprueba si un valor está dentro de una lista de resultados.

Ejemplo:

SELECT Nombre
FROM Personas
WHERE Id IN (
    SELECT Id
    FROM Vendedores
);
Operador NOT IN

Hace exactamente lo contrario.

Devuelve los registros que no aparecen en la subconsulta.

EXISTS

No compara valores.

Solo verifica si la subconsulta devuelve al menos una fila.

Si devuelve alguna fila → TRUE.

Si no devuelve ninguna → FALSE.

Ejemplo:

SELECT *
FROM Clientes c
WHERE EXISTS (
    SELECT *
    FROM Pedidos p
    WHERE c.Id = p.ClienteId
);
NOT EXISTS

Devuelve los registros para los que no existe ninguna fila relacionada.

ANY (o SOME)

Significa:

"Al menos uno".

Ejemplo:

Precio > ANY (...)

Es verdadero si el precio es mayor que por lo menos uno de los valores devueltos por la subconsulta.

ALL Significa: "Todos".
Ejemplo:
Precio > ALL (...)
"Todos".

DIFERENCIAS IMPORTANTES
| Operador       | ¿Qué hace?                                  |
| -------------- | ------------------------------------------- |
| `IN`           | Busca si un valor está dentro de una lista. |
| `NOT IN`       | Busca los valores que no están en la lista. |
| `EXISTS`       | Verifica si existen filas.                  |
| `NOT EXISTS`   | Verifica que no existan filas.              |
| `ANY` / `SOME` | Compara con al menos un valor.              |
| `ALL`          | Compara con todos los valores.              |


Lo más importante para recordar
Una subconsulta es una consulta dentro de otra consulta.
Se puede utilizar en SELECT, FROM y WHERE.
Las subconsultas correlacionadas dependen de la consulta principal y se ejecutan una vez por cada registro.
IN y NOT IN trabajan con listas de valores.
EXISTS y NOT EXISTS verifican la existencia de filas.
ANY significa "al menos uno".
ALL significa "todos".
