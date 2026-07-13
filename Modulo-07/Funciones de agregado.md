 ¿Qué son las Funciones de Agregado?Las funciones de agregado realizan cálculos sobre un conjunto de valores y devuelven un único valor resultante.
 Son fundamentales para resumir, agrupar y analizar grandes volúmenes de datos de manera eficiente.
 Funciones comunes y su propósito:  AVG: Devuelve el promedio de los valores.  MAX: Devuelve el valor máximo.  MIN: Devuelve el valor mínimo.
 SUM: Devuelve la sumatoria de los valores.  COUNT: Devuelve la cantidad de elementos en formato de tipo de datos int.
 COUNT_BIG: Devuelve la cantidad de elementos en formato de tipo de datos bigint.  VAR / VARP: Devuelven la varianza estándar y de la población, respectivamente. 
 STDEV / STDEVP: Devuelven la desviación de la población y la desviación estándar, respectivamente. 
 
  Detalle de Funciones PrincipalesA. 
  Función COUNT y COUNT_BIGAmbas funciones devuelven el número de elementos encontrados en un grupo.
  Su única diferencia radica en el tipo de datos del valor que retornan (int para COUNT y bigint para COUNT_BIG).  
  ⚠️ Importante: Las funciones de agregado como COUNT(columna) ignoran por completo los valores NULL. Sin embargo, COUNT(*) o COUNT(1) toman en cuenta todas las filas de la tabla
  sin importar si tienen nulos.  
  Ejemplo de comportamiento con NULL: Dada la siguiente tabla de ejemplo:

  ID,   MONTO
  1     10
  2     20
NULL    10
  4      5

Resultados según la sintaxis empleada:  
COUNT(*) (cuenta todas las filas físicas). 
COUNT(1)  (equivalente a contar todas las filas).  
COUNT(MONTO) (no hay valores nulos en esta columna).  
COUNT(ID) (ignora la fila donde el ID es NULL).  

B. Funciones MAX y MIN Devuelven los valores extremos de una expresión.  Tomando como referencia la tabla anterior:  MAX(MONTO) devolverá 20. 
MIN(MONTO) devolverá 5.  

Sintaxis básica de ejemplo:SQLSELECT MAX(ListPrice) AS Maximo, MIN(ListPrice) AS Minimo 
FROM Production.Product;

C. Función SUMDevuelve la suma acumulada de todos los valores (o únicamente de los valores DISTINCT si se especifica). 
Restricción: Solo se puede utilizar con columnas de tipo numérico.  Tratamiento de nulos: Se omiten los valores NULL automáticamente. 
Tomando como referencia la tabla de ejemplo, SUM(MONTO) dará como resultado 45 ($10 + 20 + 10 + 5$).  

Sintaxis básica de ejemplo:SQLSELECT SUM(ListPrice) AS Total 
FROM Production.Product;

D. Función AVGDevuelve el promedio de los valores de un grupo. Al igual que las anteriores, omite los valores NULL del cálculo. 
Tomando como referencia la tabla de ejemplo, AVG(MONTO) dará como resultado 11.25 ($45 / 4$).  
Sintaxis básica de ejemplo: SQLSELECT AVG(ListPrice) AS Promedio 
FROM Production.Product;
