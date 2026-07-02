Cláusula WHERE: La cláusula WHERE permite filtrar registros de una tabla según una o varias condiciones. Se utiliza después de la cláusula FROM.
Sintaxis
SELECT columnas
FROM tabla
WHERE condición;

Orden correcto de las cláusulas SQL
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
WHERE se utiliza para especificar qué registros queremos obtener.

Permiten comparar valores dentro de una condición.

Operador	Descripción
=	          Igual a
<>	      Distinto de
>          Mayor que
<	         Menor que
>=	    Mayor o igual que
<=	    Menor o igual que

Ejemplos
SELECT Nombre
FROM Articulos
WHERE codigo = 1;

SELECT Nombre, Precio
FROM Articulos
WHERE Precio > 150;

Operadores lógicos Permiten combinar varias condiciones.

AND
Se deben cumplir todas las condiciones.

SELECT *
FROM Articulos
WHERE Precio < 20
AND Stock >= 100;

OR
Debe cumplirse al menos una de las condiciones.

SELECT *
FROM Articulos
WHERE Precio >= 500
OR Stock >= 100;

NOT
Niega una condición.
SELECT *
FROM Articulos
WHERE NOT Precio > 100;

COMPARACIONES CON NULL
Cuando una comparación incluye un valor NULL, el resultado normalmente también es NULL.
Existe un operador especial: <=>
Este operador realiza comparaciones seguras con valores NULL.
Si ambos valores son NULL, el resultado es TRUE.

BETWEEN / NOT BETWEEN
Se utilizan para verificar si un valor está dentro de un rango.
Sintaxis
BETWEEN valor_inicial AND valor_final
Ejemplo

SELECT *
FROM Articulos
WHERE Precio BETWEEN 100 AND 200;

NOT BETWEEN
SELECT *
FROM Articulos
WHERE Precio NOT BETWEEN 100 AND 200;

IN / NOT IN
Permiten comprobar si un valor pertenece a una lista.
IN
SELECT *
FROM Articulos
WHERE Codigo IN (1,2,3);

SELECT *
FROM Articulos
WHERE Nombre IN ('Pala','Maza');

NOT IN
SELECT *
FROM Articulos
WHERE Nombre NOT IN ('Pala','Maza');
Es una alternativa más limpia que escribir muchas condiciones con OR.

LIKE / NOT LIKE

Se utilizan para buscar texto mediante patrones.

Comodines 
Comodín	          Significado
%	          Cualquier cantidad de caracteres
_	               Un único carácter


BUSCAR UNA PALABRA 
SELECT *
FROM Articulos
WHERE Nombre LIKE '%Pala%';
Devuelve todos los registros que contengan la palabra Pala.
Importante: En MySQL, LIKE generalmente no distingue entre mayúsculas y minúsculas, salvo que la configuración indique lo contrario.

Secuencias de escape
Cuando queremos buscar los caracteres especiales % o _ literalmente, debemos escaparlos utilizando \.

Ejemplo
SELECT *
FROM Clientes
WHERE Mail LIKE '%\_%';

Busca correos electrónicos que contengan el carácter _.

🚫 IS NULL / IS NOT NULL
Se utilizan para comprobar si un campo tiene o no un valor.

IS NULL
SELECT *
FROM Clientes
WHERE Comentarios IS NULL;

Devuelve los registros cuyo campo Comentarios está vacío.

IS NOT NULL
SELECT *
FROM Clientes
WHERE Comentarios IS NOT NULL;
Devuelve los registros que sí tienen información cargada en ese campo.

Resumen rápido
Operador	        Función
WHERE            	Filtra registros según una condición.
=	                Igual a.
<>              	Distinto de.
>	                Mayor que.
<                	Menor que.
>=              	Mayor o igual que.
<=              	Menor o igual que.
AND             	Todas las condiciones deben cumplirse.
OR	              Al menos una condición debe cumplirse.
NOT	              Niega una condición.
BETWEEN	          Busca valores dentro de un rango.
NOT BETWEEN	      Excluye un rango de valores.
IN	              Busca valores dentro de una lista.
NOT IN	          Excluye valores de una lista.
LIKE	            Busca texto mediante patrones.
%	                Cualquier cantidad de caracteres.
_	                Un solo carácter.
IS NULL	          Busca campos sin valor.
IS NOT NULL	      Busca campos con valor.




