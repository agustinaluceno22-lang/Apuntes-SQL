¿Qué son las consultas relacionadas? Permiten obtener información de dos o más tablas mediante una única consulta SELECT.
Se utilizan cuando los datos que necesitamos están distribuidos en distintas tablas.
Producto cartesiano: El producto cartesiano combina todas las filas de una tabla con todas las filas de otra.
Se obtiene incluyendo ambas tablas en el FROM sin una condición WHERE.

Sintaxis
SELECT *
FROM Productos, Marcas;
¿Qué ocurre?

Si:

Productos tiene 9 registros
Marcas tiene 9 registros

El resultado será:

9 × 9 = 81 filas

Cada producto aparecerá combinado con todas las marcas, incluso aquellas que no le pertenecen.

Relación entre tablas

En el ejemplo:

Tabla Productos

idProducto
Nombre
Precio
Marca

Tabla Marcas

idMarca
Nombre

El campo:

Productos.Marca

contiene el id de la marca.

Ese valor corresponde al campo:

Marcas.idMarca

Es decir:

Productos.Marca = Marcas.idMarca

Una marca puede tener:

Ningún producto
Uno
Muchos productos
Composición interna (INNER JOIN)

La composición interna consiste en un producto cartesiano restringido.

Solo se muestran los registros que cumplen una condición determinada.

Sintaxis
SELECT *
FROM Productos, Marcas
WHERE Productos.Marca = Marcas.idMarca;
¿Qué hace esta consulta?

Compara:

Productos.Marca

con

Marcas.idMarca

y devuelve únicamente los productos junto con su marca correspondiente.

Ejemplo:

Producto	   Marca
iPhone 6   	Apple
Galaxy S7	  Samsung
Notebook CQ40-300	HP
Diferencia entre Producto Cartesiano e INNER JOIN

Producto Cartesiano	                         Composición Interna
Combina todas las filas          	         Solo combina las relacionadas
No utiliza condición                            	Utiliza WHERE
Produce muchos registros innecesarios   	Devuelve únicamente la información útil
Poco utilizado en la práctica             	Muy utilizado en bases de datos


Conceptos importantes para recordar
Una consulta puede obtener datos de varias tablas.
El producto cartesiano genera todas las combinaciones posibles.
La composición interna (INNER JOIN) devuelve únicamente los registros relacionados.
La relación entre tablas suele realizarse mediante claves primarias y claves foráneas.
La condición de relación se especifica con WHERE (o con INNER JOIN en la sintaxis moderna).


Producto cartesiano = todas las combinaciones posibles.

INNER JOIN = solo los registros que tienen relación entre ambas tablas.

Es una de las preguntas más comunes cuando empiezan a evaluar conocimientos de SQL.
