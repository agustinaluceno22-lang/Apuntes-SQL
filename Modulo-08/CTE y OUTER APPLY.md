Expresión de Tabla Común (CTE)Una CTE (Common Table Expression) es una estructura temporal en SQL que define un conjunto de resultados que solo existe durante la ejecución 
de una única consulta.  Características principales:
Temporal: Solo existe mientras se ejecuta la consulta que la invoca. 
Legibilidad: Permite dividir consultas grandes o complejas en partes más sencillas y fáciles de entender. 
No almacenada: No ocupa espacio físico en el disco ni admite la creación de índices independientes. 
Recursividad: Es la herramienta ideal para manejar estructuras jerárquicas o en forma de árbol (como organigramas). 

Sintaxis y Ejemplo:La CTE se define mediante la palabra clave WITH. 
-- Definición de la CTE
WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)
AS
(
    SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear
    FROM Sales.SalesOrderHeader
    WHERE SalesOrderID = 43659
)
-- Consulta que utiliza la CTE inmediatamente después
SELECT * FROM Sales_CTE;

Reglas importantes:Debe ir seguida inmediatamente de una única instrucción SELECT, INSERT, UPDATE o DELETE que la utilice.  
Si se define dentro de un script con múltiples sentencias (lote), la instrucción que precede a WITH debe terminar obligatoriamente con un punto y coma (;).
No se permiten usar las cláusulas INTO u ORDER BY (a menos que se use TOP) dentro de la definición de la CTE.

 Operador OUTER APPLYEl: operador OUTER APPLY se utiliza para combinar las filas de una tabla principal con el resultado de una subconsulta o función con valores de tabla (TVF) 
 que depende de los datos de esa tabla principal. 
 Características clave:
 Comportamiento: Funciona de manera similar a un LEFT JOIN.  
 Inclusión de Nulos: Devuelve todas las filas de la tabla principal. Si la subconsulta o función no devuelve ningún resultado para una fila específica,
 OUTER APPLY la conserva e introduce valores NULL en las columnas correspondientes.
 Dinámico: Es excelente para pasar parámetros dinámicos (columnas de la tabla principal) a funciones de tabla.
 SELECT *
FROM TablaPrincipal AS TP
OUTER APPLY (
    -- Subconsulta dinámica que lee datos de TP
    SELECT columna1, columna2
    FROM OtraTabla AS OT
    WHERE OT.clave = TP.clave
) AS SubconsultaAlias;

Aquí tienes la estructura de apuntes en Markdown para este nuevo documento sobre **Expresiones de Tabla Comunes (CTE)** y el operador **OUTER APPLY**. He mantenido la misma sencillez y organización directa para que se acople perfectamente en tu repositorio de GitHub.

---

# Apuntes de SQL: CTE y OUTER APPLY

## 1. Expresión de Tabla Común (CTE)

Una **CTE** (Common Table Expression) es una estructura temporal en SQL que define un conjunto de resultados que solo existe durante la ejecución de una única consulta.

### Características principales:

* **Temporal:** Solo existe mientras se ejecuta la consulta que la invoca.


* **Legibilidad:** Permite dividir consultas grandes o complejas en partes más sencillas y fáciles de entender.


* **No almacenada:** No ocupa espacio físico en el disco ni admite la creación de índices independientes.


* **Recursividad:** Es la herramienta ideal para manejar estructuras jerárquicas o en forma de árbol (como organigramas).



### Sintaxis y Ejemplo:

La CTE se define mediante la palabra clave `WITH`.

```sql
-- Definición de la CTE
WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)
AS
(
    SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear
    FROM Sales.SalesOrderHeader
    WHERE SalesOrderID = 43659
)
-- Consulta que utiliza la CTE inmediatamente después
SELECT * FROM Sales_CTE;

```

### Reglas importantes:

* Debe ir seguida inmediatamente de una única instrucción `SELECT`, `INSERT`, `UPDATE` o `DELETE` que la utilice.


* Si se define dentro de un script con múltiples sentencias (lote), la instrucción que precede a `WITH` debe terminar obligatoriamente con un punto y coma (`;`).


* No se permiten usar las cláusulas `INTO` u `ORDER BY` (a menos que se use `TOP`) dentro de la definición de la CTE.



---

## 2. Operador OUTER APPLY

El operador `OUTER APPLY` se utiliza para combinar las filas de una tabla principal con el resultado de una subconsulta o función con valores de tabla (TVF) que depende de los datos de esa tabla principal.

### Características clave:

* **Comportamiento:** Funciona de manera similar a un `LEFT JOIN`.


* **Inclusión de Nulos:** Devuelve todas las filas de la tabla principal. Si la subconsulta o función no devuelve ningún resultado para una fila específica, `OUTER APPLY` la conserva e introduce valores `NULL` en las columnas correspondientes.


* **Dinámico:** Es excelente para pasar parámetros dinámicos (columnas de la tabla principal) a funciones de tabla.



### Sintaxis básica:

```sql
SELECT *
FROM TablaPrincipal AS TP
OUTER APPLY (
    -- Subconsulta dinámica que lee datos de TP
    SELECT columna1, columna2
    FROM OtraTabla AS OT
    WHERE OT.clave = TP.clave
) AS SubconsultaAlias;

```

---

## 3. Resumen Rápido: CTE vs. Tablas Temporales

| Característica |                                    CTE (`WITH`)                                            Tabla Temporal (`#`) |

| **¿Se guarda en disco?** |               No, solo existe en memoria durante la consulta.              | Sí, se crea físicamente en la base `tempdb`.


| **¿Soporta Índices?** |                         No se puede indexar.                               | Sí, se le pueden aplicar índices primarios o secundarios.


 
| **Duración** |                              Muere inmediatamente al terminar la consulta.           Dura toda la sesión del usuario hasta cerrarse.             


 
| **Uso ideal** |                            Hacer el código limpio y manejar recursividad.             Guardar cálculos pesados con millones de registros.

 
