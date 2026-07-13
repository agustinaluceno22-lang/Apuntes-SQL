Las funciones de texto de MySQL sirven para manipular, modificar, buscar o combinar cadenas de caracteres. Facilitan la presentación y el tratamiento de los datos en las consultas. 
Un detalle importante es que no debe haber espacios entre el nombre de la función y el paréntesis (por ejemplo, UPPER(nombre) y no UPPER (nombre))

1. CONCAT()

Une varios textos o columnas en una sola cadena.

Sintaxis
SELECT CONCAT(texto1, texto2, texto3);
Ejemplo
SELECT CONCAT('Sr. ', Nombre, ' ', Apellido) AS NombreCompleto
FROM Clientes;

Resultado

NombreCompleto
Sr. Juan Pérez

Se usa para: unir nombres, direcciones, mensajes, etc.

2. CONCAT_WS()

Hace lo mismo que CONCAT, pero agrega un separador entre los valores (WS = With Separator).

Sintaxis
SELECT CONCAT_WS(',', columna1, columna2);
Ejemplo
SELECT CONCAT_WS(', ', Nombre, Apellido, Direccion)
FROM Clientes;

Resultado

Juan, Pérez, Av. Siempre Viva 123

Se usa para: listas separadas por comas, guiones, espacios, etc.

3. UPPER()

Convierte un texto a mayúsculas.

Ejemplo
SELECT UPPER(Nombre)
FROM Clientes;

Resultado

JUAN
MARIA
PEDRO

4. LOWER()

Convierte un texto a minúsculas.

Ejemplo
SELECT LOWER(Apellido)
FROM Clientes;

Resultado

perez
gomez
lopez

5. LEFT()

Obtiene los primeros caracteres de un texto.

Sintaxis
LEFT(texto, cantidad)
Ejemplo
SELECT LEFT(Nombre,3)
FROM Clientes;

Resultado

Juan → Jua
Pedro → Ped

También puede utilizarse junto con CONCAT:

SELECT CONCAT(LEFT(Nombre,1),'.')
FROM Clientes;

Resultado:

J.
M.
P.

6. RIGHT()

Obtiene los últimos caracteres.

Ejemplo
SELECT RIGHT(CUIT,1)
FROM Clientes;

Resultado:

20333444551 → 1

Se usa mucho para obtener el último dígito de un código.

7. SUBSTRING()

Extrae una parte del texto.

Sintaxis
SUBSTRING(texto, posicion, cantidad)
texto → cadena original.
posición → desde dónde empieza.
cantidad → cuántos caracteres toma.
Ejemplo
SELECT SUBSTRING(CUIT,4,8)
FROM Clientes;

Si el CUIT es:

20-12345678-9

Resultado:

12345678

8. CHAR_LENGTH()

Cuenta la cantidad de caracteres de una cadena (incluye espacios).

Ejemplo
SELECT Direccion,
       CHAR_LENGTH(Direccion)
FROM Clientes;

Resultado:

"Av. Rivadavia" → 13

9. LOCATE()

Busca una palabra o texto dentro de otra cadena y devuelve la posición donde aparece por primera vez.

Sintaxis
LOCATE('texto', columna)
Ejemplo
SELECT LOCATE('ara',Direccion)
FROM Clientes;

Si la dirección es:

Aráoz 123

Resultado:

1

Si no encuentra el texto:

0

10. LTRIM()

Elimina los espacios al comienzo del texto.

Ejemplo
SELECT LTRIM(Direccion)
FROM Clientes;
"     Av. Mayo"

↓

"Av. Mayo"

11. RTRIM()

Elimina los espacios al final del texto.

Ejemplo
SELECT RTRIM(Direccion)
FROM Clientes;
"Av. Mayo      "

↓

"Av. Mayo"

12. TRIM()

Elimina los espacios al principio y al final.

Ejemplo
SELECT TRIM(Direccion)
FROM Clientes;
"     Av. Mayo      "

↓

"Av. Mayo"

13. REPLACE()

Busca un texto y lo reemplaza por otro.

Sintaxis
REPLACE(texto, 'buscar', 'reemplazar')
Ejemplo
SELECT REPLACE(Direccion,
               'Av.',
               'Avenida')
FROM Clientes;

Resultado:

Av. Santa Fe

↓

Avenida Santa Fe

RESUMEN RAPIDO PARA ESTUDIAR
| Función         | ¿Qué hace?                             |
| --------------- | -------------------------------------- |
| `CONCAT()`      | Une textos.                            |
| `CONCAT_WS()`   | Une textos con un separador.           |
| `UPPER()`       | Convierte a mayúsculas.                |
| `LOWER()`       | Convierte a minúsculas.                |
| `LEFT()`        | Obtiene los primeros caracteres.       |
| `RIGHT()`       | Obtiene los últimos caracteres.        |
| `SUBSTRING()`   | Extrae una parte del texto.            |
| `CHAR_LENGTH()` | Cuenta los caracteres.                 |
| `LOCATE()`      | Busca la posición de un texto.         |
| `LTRIM()`       | Elimina espacios al inicio.            |
| `RTRIM()`       | Elimina espacios al final.             |
| `TRIM()`        | Elimina espacios al inicio y al final. |
| `REPLACE()`     | Reemplaza un texto por otro.           |


Truco para recordar
CONCAT → une.
UPPER / LOWER → cambia mayúsculas/minúsculas.
LEFT / RIGHT → toma izquierda/derecha.
SUBSTRING → corta una parte del texto.
CHAR_LENGTH → cuenta caracteres.
LOCATE → busca una palabra.
LTRIM / RTRIM / TRIM → eliminan espacios.
REPLACE → reemplaza texto.
