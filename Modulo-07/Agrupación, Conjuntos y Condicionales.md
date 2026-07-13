 Cláusula DISTINCT: Se utiliza para eliminar duplicados de los resultados de una consulta, devolviendo únicamente valores únicos de las columnas seleccionadas.
 
2. Características clave:Ámbito de aplicación: Evalúa todas las columnas de forma conjunta. La combinación completa de las columnas seleccionadas debe ser única.

3.Rendimiento: Puede ralentizar la consulta en tablas grandes debido al proceso interno de identificación y descarte de duplicados.  Funciones de agregación: No se usa directamente como DISTINCT COUNT(*).
Para contar valores únicos se debe estructurar así:  SQLSELECT COUNT(DISTINCT columna) FROM tabla;

Sintaxis y Ejemplo:SQLSELECT DISTINCT columna1, columna2
FROM tabla
WHERE condiciones;
Si tenemos una tabla clientes con nombres y ciudades repetidas, al ejecutar:SQLSELECT DISTINCT nombre, ciudad
FROM clientes;
El motor omitirá los registros duplicados exactos y devolverá únicamente las combinaciones únicas.  
2. Operadores de Conjunto: UNION y UNION ALLPermiten combinar los resultados de dos o más consultas SELECT en un solo conjunto. 
Reglas obligatorias de uso:El número y el orden de las columnas debe ser el mismo en todas las consultas.  Los tipos de datos de las columnas correspondientes deben ser compatibles (directamente o mediante conversión implícita). 
Diferencias entre UNION y UNION ALL:CaracterísticaUNION  PDFUNION ALL  PDFTratamiento de duplicadosLos elimina por defecto (solo filas únicas).
Conserva todos los registros, incluidos duplicados.  RendimientoMás lento (requiere procesar y quitar duplicados). 
Más rápido (une los resultados de forma directa).  Ejemplo de Sintaxis (UNION ALL):SQLSELECT BusinessEntityID FROM Sales.SalesPerson
UNION ALL
SELECT BusinessEntityID FROM HumanResources.Employee;
5. Operador CASE  Evalúa una lista de condiciones y devuelve un resultado específico para la primera que se cumpla (similar a un if-else en programación). Cuenta con un bloque ELSE opcional para cuando ninguna condición previa se cumpla.  Formatos:CASE Sencillo: Compara una expresión directamente con un conjunto de valores discretos.  CASE Buscado: Evalúa expresiones booleanas complejas en cada condición.  Ámbito de aplicación:Se puede utilizar en casi cualquier parte de una instrucción SQL que permita expresiones válidas, como SELECT, UPDATE, SET, WHERE, HAVING y ORDER BY.  Ejemplos Prácticos:Uso dentro de SELECT (CASE Sencillo):SQLSELECT ProductLine,
       Category = CASE ProductLine
           WHEN 'R' THEN 'Road'
           WHEN 'M' THEN 'Mountain'
           WHEN 'T' THEN 'Touring'
           ELSE 'Not for sale'
       END
FROM Production.Product;
Uso dentro de ORDER BY (CASE Buscado):
Permite aplicar una lógica de ordenamiento condicional. Por ejemplo, ordenar de forma descendente si el país es 'United States', y de forma ascendente para cualquier otro caso: 
SQLSELECT LastName, CountryRegionName
FROM Sales.vSalesPerson
WHERE TerritoryName IS NOT NULL
ORDER BY 
    CASE WHEN CountryRegionName = 'United States' THEN LastName END DESC,
    CASE WHEN CountryRegionName <> 'United States' THEN LastName END ASC;
