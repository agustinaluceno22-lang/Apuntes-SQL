Operadores en SQL
¿Qué son los operadores? Los operadores son símbolos o palabras que permiten realizar operaciones sobre datos o variables.
En SQL se utilizan para:

Hacer cálculos.
Comparar valores.
Filtrar información.
Combinar condiciones.
Tipos de operadores

1. Operadores aritméticos
Se utilizan para realizar operaciones matemáticas.
| Operador | Significado                    |
| -------- | ------------------------------ |
| +        | Suma                           |
| -        | Resta                          |
| *        | Multiplicación                 |
| /        | División                       |
| %        | Módulo (resto de una división) |

Ejemplos:
SELECT 10 + 5;

Resultado: 15

SELECT 10 % 3;

Resultado: 1 (porque sobra 1).

2. Operadores de comparación

Comparan dos valores y devuelven un resultado TRUE (verdadero) o FALSE (falso).

| Operador | Significado   |
| -------- | ------------- |
| =        | Igual         |
| <> o !=  | Distinto      |
| >        | Mayor que     |
| <        | Menor que     |
| >=       | Mayor o igual |
| <=       | Menor o igual |

Ejemplos:

WHERE Edad > 18

Devuelve personas mayores de 18 años.

WHERE Provincia = 'Buenos Aires'

Devuelve únicamente los registros cuya provincia sea Buenos Aires.

3. Operadores lógicos

Sirven para combinar varias condiciones.

AND

Todas las condiciones deben cumplirse.

Ejemplo:

WHERE Edad >= 18
AND Provincia = 'Buenos Aires'

Solo muestra personas mayores de edad que vivan en Buenos Aires.

OR

Al menos una condición debe cumplirse.

Ejemplo:

WHERE Provincia = 'Buenos Aires'
OR Provincia = 'Córdoba'

Muestra registros de cualquiera de las dos provincias.

NOT

Niega una condición.

Ejemplo:

WHERE NOT Provincia = 'Buenos Aires'

Muestra todas las provincias excepto Buenos Aires.

Cláusula WHERE

La cláusula WHERE se utiliza para filtrar registros.

Se puede usar con:

SELECT
UPDATE
DELETE
Sintaxis
SELECT *
FROM Clientes
WHERE Edad > 18;

Solo devuelve los clientes mayores de 18 años.

Ejemplo con operadores de comparación
SELECT Name, ListPrice
FROM Production.Product
WHERE ListPrice > 0
AND ListPrice < 40;

Este ejemplo devuelve los productos cuyo precio sea mayor que 0 y menor que 40.

Ejemplo con operadores lógicos
WHERE
(WeightUnitMeasureCode = 'G'
OR WeightUnitMeasureCode = 'LB')
AND
(ProductID = 513
OR ProductID = 739)

Significa:
La unidad debe ser G o LB.
Y además el ProductID debe ser 513 o 739

TABLA DE VERDAD 
| Condición 1 | Condición 2 | Resultado |
| ----------- | ----------- | --------- |
| TRUE        | TRUE        | ✅ TRUE    |
| TRUE        | FALSE       | ❌ FALSE   |
| FALSE       | TRUE        | ❌ FALSE   |
| FALSE       | FALSE       | ❌ FALSE   |
Regla: con AND, todas las condiciones deben ser verdaderas.

OR
| Condición 1 | Condición 2 | Resultado |
| ----------- | ----------- | --------- |
| TRUE        | TRUE        | ✅ TRUE    |
| TRUE        | FALSE       | ✅ TRUE    |
| FALSE       | TRUE        | ✅ TRUE    |
| FALSE       | FALSE       | ❌ FALSE   |
Regla: con OR, alcanza con que una condición sea verdadera.

Combinar AND y OR
También pueden utilizarse juntos.
Ejemplo:

WHERE
(ListPrice < 60 AND Color = 'Yellow')
OR
(ListPrice > 2318 AND Color = 'Silver')

Trae:

Productos amarillos con precio menor a 60.
O productos plateados con precio mayor a 2318.

Valores NULL

NULL significa que un dato no tiene valor.

⚠️ No es lo mismo que:

0
""
Espacio en blanco

Características:

Representa ausencia de información.
Cualquier operación con NULL devuelve NULL.
Al diseñar una tabla se puede indicar si una columna acepta NULL o no.
IS NULL e IS NOT NULL

Para buscar valores nulos se utilizan estas cláusulas.

IS NULL

Busca registros cuyo valor sea nulo.

WHERE Color IS NULL;
IS NOT NULL

Busca registros cuyo valor exista.

WHERE Weight IS NOT NULL;

También pueden combinarse:

WHERE Weight IS NOT NULL
AND Color IS NULL;

Devuelve los productos que tienen peso cargado, pero no tienen color.

⭐ Lo más importante para el examen

✅ Qué son los operadores.

✅ Operadores aritméticos:

+
-
*
/
%

✅ Operadores de comparación:

=
<>
!=
>
<
>=
<=

✅ Operadores lógicos:

AND → todas las condiciones deben cumplirse.
OR → alcanza con una condición verdadera.
NOT → niega una condición.

✅ Cláusula WHERE para filtrar registros.

✅ Qué significa NULL.

✅ Diferencia entre IS NULL e IS NOT NULL.

📝 Truco para memorizar
➕ Aritméticos = hacen cuentas.
⚖️ Comparación = comparan valores (TRUE/FALSE).
🧠 Lógicos = unen condiciones (AND, OR, NOT).
🔎 WHERE = filtra los registros.
❓ NULL = no hay dato (no es 0 ni una cadena vacía).
