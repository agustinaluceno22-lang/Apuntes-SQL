Criterios de selección en SQL
¿Qué son los criterios de selección?
Los criterios de selección son condiciones que se utilizan en una consulta SQL para filtrar los datos y obtener solo aquellos registros que cumplen una condición determinada.
Estas condiciones se expresan mediante predicados, que devuelven:

✅ TRUE (Verdadero)
❌ FALSE (Falso)
BETWEEN

La cláusula BETWEEN se utiliza para buscar valores que estén dentro de un rango.

Incluye los valores de los extremos.

Sintaxis
SELECT *
FROM Productos
WHERE Precio BETWEEN 0 AND 50;

Trae todos los productos cuyo precio esté entre 0 y 50, incluyendo ambos valores.

NOT BETWEEN

Hace exactamente lo contrario.

Devuelve los registros que NO están dentro del rango.

Sintaxis
SELECT *
FROM Productos
WHERE Precio NOT BETWEEN 0 AND 50;

Trae todos los productos con precio menor que 0 o mayor que 50.

Importante

BETWEEN incluye los extremos.
Si alguno de los valores es NULL, el resultado es UNKNOWN.
IN

Se utiliza para comparar un campo con una lista de valores.

Es equivalente a escribir muchos OR.

Sintaxis
SELECT *
FROM Personas
WHERE Provincia IN ('Buenos Aires','Córdoba','Santa Fe');

Es igual que escribir:

WHERE Provincia='Buenos Aires'
OR Provincia='Córdoba'
OR Provincia='Santa Fe'

NOT IN

Hace lo contrario de IN.

Devuelve todos los registros que NO pertenecen a la lista.

Sintaxis
SELECT *
FROM Personas
WHERE Provincia NOT IN ('Buenos Aires','Córdoba');

Trae todas las provincias excepto esas dos.

LIKE

Se utiliza para buscar textos mediante patrones.

Permite utilizar caracteres comodín (wildcards) para hacer búsquedas más flexibles.

Es mucho más útil que usar solamente "=" cuando se buscan palabras o partes de ellas.

Comodines de LIKE
%

Representa cualquier cantidad de caracteres.

Empieza con
WHERE Apellido LIKE 'A%'

Empieza con A.

Ejemplo:

Alvarez
Acosta
Arias
Termina con
WHERE Apellido LIKE '%A'

Termina con A.

Ejemplo:

Sosa
Medina
Contiene
WHERE Apellido LIKE '%ra%'

Contiene "ra" en cualquier parte.

Ejemplo:

Bravo
Aranda
Abraham

_ (guion bajo)

Representa un solo carácter.

Ejemplo:

WHERE Nombre LIKE '_ean'

Coincide con:

Sean
Dean

Porque tienen cualquier letra al principio seguida de "ean".

[ ]

Permite indicar un conjunto o rango de caracteres.

Ejemplo:

LIKE '[A-C]%'

Empieza con:

A
B
C

También puede ser:

LIKE 'Zh[ae]ng'

Acepta:

Zhang
Zheng

[^ ]

Indica que NO debe coincidir con esos caracteres.

Ejemplo:

LIKE 'A[^B]%'

Empieza con A, pero la segunda letra no puede ser B.

Ejemplo válido:

Acosta

Ejemplo no válido:

Abreu

Otros ejemplos de LIKE

Apellido que comienza con A:

WHERE LastName LIKE 'A%'

Apellido que termina con A:

WHERE LastName LIKE '%A'

Apellido que contiene "ra":

WHERE LastName LIKE '%ra%'

Apellido con segunda letra cualquiera y tercera letra A:

WHERE LastName LIKE 'A_A%'

Buscar caracteres especiales

Cuando queremos buscar un símbolo como % y no usarlo como comodín, debemos utilizar ESCAPE.

Ejemplo:

WHERE comentario LIKE '%30!%%'
ESCAPE '!'

Permite buscar exactamente el texto 30%.

ORDER BY

La cláusula ORDER BY sirve para ordenar los resultados de una consulta.

Sin ORDER BY, SQL no garantiza el orden en que devolverá los registros.

Puede ordenar por:

Una columna.
Varias columnas.

ASC

Orden ascendente.

Es el valor por defecto.

Ejemplo:

ORDER BY Nombre ASC

Ordena de:

A → Z
1 → 100
DESC

Orden descendente.

Ejemplo:

ORDER BY Nombre DESC

Ordena de:

Z → A
100 → 1

Ordenar por varias columnas

También pueden ordenarse varias columnas.

Ejemplo:

SELECT FirstName, LastName
FROM Person.Person
ORDER BY FirstName ASC, LastName DESC;

Primero ordena por Nombre (A-Z).

Si hay nombres iguales, ordena los Apellidos de Z-A.

⭐ Lo más importante para el examen

✅ Qué son los criterios de selección.

✅ BETWEEN → busca datos dentro de un rango (incluye los extremos).

✅ NOT BETWEEN → fuera del rango.

✅ IN → busca varios valores específicos.

✅ NOT IN → excluye varios valores.

✅ LIKE → búsqueda por patrones.

Comodines de LIKE
% → cualquier cantidad de caracteres.
_ → un solo carácter.
[ABC] → uno de esos caracteres.
[A-Z] → un rango.
[^ABC] → cualquier carácter excepto esos.

✅ ESCAPE → buscar símbolos como % o _ de forma literal.

✅ ORDER BY → ordena los resultados.

ASC → ascendente (A-Z, menor a mayor).
DESC → descendente (Z-A, mayor a menor).
📝 Truco para memorizar
📏 BETWEEN = entre dos valores.
📋 IN = está en esta lista.
❌ NOT IN = no está en esta lista.
🔎 LIKE = buscar textos por patrón.
% = muchos caracteres.
_ = un solo carácter.
📊 ORDER BY = ordenar resultados.
⬆️ ASC = de menor a mayor (A → Z).
⬇️ DESC = de mayor a menor (Z → A).
