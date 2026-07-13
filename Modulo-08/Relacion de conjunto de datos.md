 (GROUP BY y HAVING)1.
 Cláusula GROUP BYLa cláusula GROUP BY se utiliza para proyectar y agrupar filas que comparten valores idénticos en una o más columnas seleccionadas. 
 Su propósito principal es resumir la información combinándola con funciones de agregado (SUM, AVG, COUNT, MAX, MIN).Reglas indispensables:Ubicación: 
 Se coloca después de la cláusula WHERE (si existe) y antes de la cláusula ORDER BY.
 
 Coincidencia de columnas: Cualquier columna que aparezca en la lista de selección del SELECT que no sea parte de una función de agregado, debe ser incluida de manera obligatoria 
 en la cláusula GROUP BY. 
 
 Tratamiento de valores NULL: Si las columnas de agrupación contienen valores NULL, todos estos registros se agruparán en una sola fila dentro del resultado de la consulta.
 Sintaxis básica:SQLSELECT columna1, columna2, FunciónAgregado(columna3)
FROM tabla
WHERE condiciones
GROUP BY columna1, columna2;

 CLAUSULA HAVING 
 La cláusula HAVING se utiliza para especificar condiciones de filtrado sobre grupos de filas creados por la cláusula GROUP BY.
 Funciona como un filtro de búsqueda, pero a nivel de los resultados agregados. 
 Sintaxis básica:SQLSELECT columna1, FunciónAgregado(columna2)
FROM tabla
GROUP BY columna1
HAVING condición_de_agregado;

Diferencias fundamentales: 
Clausula WHERE: Caracteristica/ Filtra filas antes de que se realice la agrupación de los datos. Uso con funciones de agregado/ No permite el uso de funciones de agregado
(ej. WHERE SUM(Monto) > 100 genera un error). Origen de los datos/ Se aplica directamente sobre las columnas de las tablas de origen

Clausula HAVING: Caracteristica/ Filtra grupos de filas después de que se ha aplicado el GROUP BY. Uso con funciones de agregado/ Sí permite y está diseñada para filtrar usando funciones de agregado.
Origen de los datos/ Se aplica sobre las columnas agrupadas o los resultados de funciones agregadas.

Ejemplo Práctico Combinado:
En esta consulta, primero filtramos filas individuales con WHERE, luego agrupamos con GROUP BY, y finalmente filtramos los grupos resultantes con HAVING:

SELECT ProductSubcategoryID, AVG(ListPrice) AS PromedioPrecio
FROM Production.Product
WHERE ListPrice > 0 -- 1. Filtra productos con precio base mayor a cero.
GROUP BY ProductSubcategoryID -- 2. Agrupa los productos restantes por subcategoría.
HAVING AVG(ListPrice) > 500; -- 3. Muestra solo los grupos cuyo promedio de precio sea mayor a 500.
