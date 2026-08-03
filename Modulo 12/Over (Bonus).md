¿Qué es OVER?
La cláusula OVER define una ventana (subconjunto de filas) sobre la cual se aplican las funciones de ventana.
Permite realizar cálculos sin agrupar los datos, manteniendo visible cada fila del resultado.
Con OVER se pueden obtener:

Promedios móviles.
Totales acumulados.
Rankings.
Totimos (Top N) por grupo.

Ventajas de OVER
Mantiene todas las filas originales.
No requiere utilizar GROUP BY.
Permite realizar cálculos avanzados sobre cada registro.
Se pueden utilizar varias funciones de ventana en una misma consulta.

PARTITION BY

PARTITION BY divide el conjunto de resultados en grupos.

La función de ventana trabaja independientemente dentro de cada grupo.

Si no se utiliza PARTITION BY, la función considera todo el resultado como una sola partición.

OVER(PARTITION BY Columna ORDER BY Columna)

ORDER BY en OVER

ORDER BY define el orden en que se procesan las filas dentro de la ventana.

Es fundamental para funciones como:

ROW_NUMBER()
RANK()
LEAD()
LAG()

Limitaciones de OVER
No puede utilizarse con CHECKSUM.
Algunas funciones no admiten ORDER BY.
Algunas funciones no admiten ROWS o RANGE.
Es especialmente útil para cálculos sobre series temporales.

Funciones de categoría (Ranking)

Estas funciones asignan una posición a cada fila.

ROW_NUMBER()

Numera las filas consecutivamente.

ROW_NUMBER() OVER(ORDER BY Columna)
RANK()

Asigna posiciones.

Si existen empates:

1
2
2
4
DENSE_RANK()

También asigna posiciones.

Pero los empates no generan saltos.

1
2
2
3
NTILE()

Divide el resultado en una cantidad determinada de grupos.

Ejemplo:

NTILE(4)

Divide los registros en cuatro grupos aproximadamente iguales.

Funciones de agregado con OVER

Las funciones de agregado también pueden utilizar la cláusula OVER.

Ejemplo:

AVG(SalesYTD)
OVER(PARTITION BY TerritoryID)

Esto calcula el promedio por territorio sin perder las filas originales.

Se pueden utilizar funciones como:

AVG()
SUM()
COUNT()
MIN()
MAX()

Funciones analíticas

Permiten realizar cálculos avanzados sobre un conjunto de datos sin reducir la cantidad de filas.

Son útiles para:

medias móviles;
totales acumulados;
rankings;
porcentajes;
comparación entre registros.


Principales funciones analíticas
| Función             | Descripción                           |
| ------------------- | ------------------------------------- |
| `LEAD()`            | Obtiene el valor de la siguiente fila |
| `LAG()`             | Obtiene el valor de la fila anterior  |
| `FIRST_VALUE()`     | Devuelve el primer valor              |
| `LAST_VALUE()`      | Devuelve el último valor              |
| `CUME_DIST()`       | Distribución acumulada                |
| `PERCENT_RANK()`    | Ranking porcentual                    |
| `PERCENTILE_CONT()` | Percentil continuo                    |
| `PERCENTILE_DISC()` | Percentil discreto                    |

LEAD()
Permite consultar el valor de la siguiente fila.

Ejemplo:

LEAD(SalesQuota,1,0)
OVER(ORDER BY QuotaDate)

Parámetros:

columna
cantidad de filas
valor por defecto

PIVOT
¿Qué es?
PIVOT transforma los valores de una columna en nuevas columnas.
Sirve para resumir información y reorganizar datos.

Ejemplo conceptual:

| Año  | Ventas |
| ---- | ------ |
| 2011 | 100    |
| 2012 | 200    |

Ventajas de PIVOT
Sintaxis más sencilla que múltiples CASE.
Facilita el análisis de datos.
Mejora la legibilidad del código.
Resume información rápidamente.

Sintaxis básica de PIVOT
SELECT ...
FROM (...)

PIVOT
(
SUM(Columna)
FOR Campo IN (...)
) AS Alias;

UNPIVOT
¿Qué es?

Realiza exactamente el proceso contrario a PIVOT.

Transforma columnas en filas.

Ejemplo:
| Enero | Febrero | Marzo |
| ----- | ------- | ----- |
| 100   | 120     | 90    |
Despespues
| Mes     | Valor |
| ------- | ----- |
| Enero   | 100   |
| Febrero | 120   |
| Marzo   | 90    |


Sintaxis básica de UNPIVOT
SELECT ...

FROM (...)

UNPIVOT
(
Valor
FOR Mes
IN(Enero,Febrero,Marzo)
)

Diferencias entre PIVOT y UNPIVOT
| PIVOT                           | UNPIVOT                     |
| ------------------------------- | --------------------------- |
| Convierte filas en columnas     | Convierte columnas en filas |
| Resume información              | Detalla información         |
| Utiliza funciones de agregación | Reorganiza datos            |

RESUMEN RAPIDO 
| Concepto       | Función                       |
| -------------- | ----------------------------- |
| `OVER`         | Define la ventana de trabajo  |
| `PARTITION BY` | Divide el resultado en grupos |
| `ORDER BY`     | Ordena la ventana             |
| `ROW_NUMBER()` | Numera filas                  |
| `RANK()`       | Ranking con saltos            |
| `DENSE_RANK()` | Ranking sin saltos            |
| `NTILE()`      | Divide en grupos              |
| `LEAD()`       | Obtiene el siguiente valor    |
| `LAG()`        | Obtiene el valor anterior     |
| `PIVOT`        | Filas → Columnas              |
| `UNPIVOT`      | Columnas → Filas              |


Lo más importante para recordar
OVER permite aplicar funciones de ventana sin utilizar GROUP BY.
PARTITION BY divide los datos en grupos sobre los que se realizan los cálculos.
ROW_NUMBER(), RANK(), DENSE_RANK() y NTILE() se utilizan para generar rankings.
LEAD() y LAG() permiten acceder a la siguiente o anterior fila.
PIVOT convierte filas en columnas.
UNPIVOT convierte columnas en filas.
PIVOT y UNPIVOT son útiles para reorganizar y analizar datos de forma más clara.
