¿Qué es JOIN? La cláusula JOIN permite combinar información de dos o más tablas mediante un campo en común. Se utiliza cuando los datos necesarios están distribuidos en diferentes tablas. Estructura básica de un SELECT Una consulta SQL está compuesta por:

SELECT campos FROM tabla WHERE condición; SELECT: columnas que se desean mostrar. FROM: tabla o tablas donde se encuentran los datos. WHERE: condición que deben cumplir los registros. Cláusula JOIN

Cuando necesitamos obtener datos de varias tablas, utilizamos JOIN.

La cantidad de JOIN necesarios es:

Cantidad de tablas - 1

Ejemplo:

2 tablas → 1 JOIN 3 tablas → 2 JOIN 4 tablas → 3 JOIN

Sintaxis de JOIN

Sintaxis moderna (recomendada)

SELECT tabla1.campo, tabla2.campo FROM tabla1 JOIN tabla2 ON tabla1.campo = tabla2.campo;

Sintaxis tradicional

SELECT tabla1.campo, tabla2.campo FROM tabla1, tabla2 WHERE tabla1.campo = tabla2.campo;

Ambas producen el mismo resultado, aunque la primera es la más utilizada actualmente.

Tipos de JOIN

Los principales son:

INNER JOIN LEFT JOIN RIGHT JOIN CROSS JOIN LEFT JOIN

Devuelve:

Todos los registros de la tabla izquierda. Solo los registros coincidentes de la tabla derecha.

Si un registro de la izquierda no tiene coincidencia, igualmente aparece en el resultado (los datos de la derecha serán NULL).

Sintaxis SELECT * FROM tabla1 LEFT JOIN tabla2 ON tabla1.codigo = tabla2.codigo; ¿Cuándo usar LEFT JOIN?

Cuando queremos mostrar todos los registros principales, aunque algunos no tengan información relacionada.

Ejemplo:

Todos los clientes. Aunque algunos nunca hayan realizado compras. RIGHT JOIN

Hace lo contrario al LEFT JOIN.

Devuelve:

Todos los registros de la tabla derecha. Solo las coincidencias de la tabla izquierda.

Si un registro de la derecha no tiene coincidencia, también aparecerá en el resultado.

Sintaxis SELECT * FROM tabla1 RIGHT JOIN tabla2 ON tabla1.codigo = tabla2.codigo; ¿Cuándo usar RIGHT JOIN?

Cuando la tabla importante es la de la derecha.

Ejemplo:

Mostrar todas las marcas, incluso aquellas que todavía no tienen productos.

CROSS JOIN

El CROSS JOIN combina cada registro de una tabla con todos los registros de la otra.

No necesita una condición ON.

Equivale al producto cartesiano.

Sintaxis SELECT * FROM tabla1 CROSS JOIN tabla2; Ejemplo

Si:

Tabla1 tiene 3 registros. Tabla2 tiene 3 registros.

Resultado:

3 × 3 = 9 registros

Cada fila de la primera tabla se combina con todas las filas de la segunda.

Comparación de los JOIN JOIN Devuelve INNER JOIN Solo registros relacionados LEFT JOIN Todos los registros de la izquierda + coincidencias RIGHT JOIN Todos los registros de la derecha + coincidencias CROSS JOIN Todas las combinaciones posibles Conceptos importantes para recordar JOIN sirve para relacionar tablas mediante un campo en común. La sintaxis moderna utiliza JOIN ... ON. INNER JOIN muestra únicamente las coincidencias. LEFT JOIN conserva todos los registros de la tabla izquierda. RIGHT JOIN conserva todos los registros de la tabla derecha. CROSS JOIN genera un producto cartesiano, por lo que suele ser poco eficiente en tablas grandes. 💡 Para entrevistas QA / SQL

Es muy común que te pregunten la diferencia entre los JOIN:

INNER JOIN: solo devuelve registros que existen en ambas tablas. LEFT JOIN: devuelve todos los registros de la tabla izquierda, tengan o no coincidencia. RIGHT JOIN: devuelve todos los registros de la tabla derecha, tengan o no coincidencia. CROSS JOIN: devuelve todas las combinaciones posibles entre ambas tablas (producto cartesiano).
