¿Qué es INSERT? La sentencia INSERT se utiliza para agregar uno o más registros nuevos a una tabla. Es una de las operaciones del lenguaje DML (Data Manipulation Language).
Sintaxis general
INSERT INTO nombre_tabla (columna1, columna2, ...)
VALUES (valor1, valor2, ...);
Cada valor corresponde a una columna y debe respetar el tipo de dato.

Formas de insertar datos 1. Manera completa ⭐ (La más utilizada) Se indican las columnas y luego los valores.
Sintaxis
INSERT INTO Productos
(Nombre, Precio, Marca, Categoria, Stock, Disponible)
VALUES
('iPhone 5', 499.99, 'Apple', 'Smartphone', 500, false);
Ventajas
Es la forma más segura. No importa el orden físico de las columnas. Si la tabla cambia, el código sigue funcionando. Es la forma recomendada.

2. Manera SQL (Solo MySQL / MariaDB) Permite asignar cada columna utilizando SET.
Sintaxis
INSERT INTO Productos
SET
Nombre = 'iPhone 5',
Precio = 499.99,
Marca = 'Apple',
Categoria = 'Smartphone',
Stock = 500,
Disponible = false;

Manera simplificada
Solo se escriben los valores.
Sintaxis
INSERT INTO Productos
VALUES
('iPhone 5', 499.99, 'Apple', 'Smartphone', 500, false);
Desventaja

Debemos respetar exactamente el orden de las columnas de la tabla. Si el orden cambia, el INSERT fallará.
Por eso se utiliza menos que la manera completa.

 VALORES NULL
¿Qué significa NULL: NULL significa:
dato desconocido
dato inexistente
dato no cargado
No significa:
0
""
"NULL"
Todos esos son valores diferentes.
INSERT INTO Productos
(Nombre, Precio, Marca, Categoria, Presentacion, Stock)
VALUES
('iPhone 7S', NULL, 'Apple', 'Smartphone', '16GB', 500);

En este caso el precio es desconocido. NULL no lleva comillas.

CAMPOS OBLIGATORIOS
Algunas columnas no permiten valores NULL.
Generalmente son:
Clave primaria (PRIMARY KEY)
Campos obligatorios definidos con NOT NULL
Si intentamos insertar NULL en esos campos, SQL mostrará un error.
Por defecto, si no se especifica NOT NULL al crear la tabla, las columnas aceptan valores NULL.

INSERT USANDO SELECT
También es posible copiar datos de una tabla a otra utilizando un SELECT.
Sintaxis
INSERT INTO TablaDestino (Columna1, Columna2)
SELECT Columna1, Columna2
FROM TablaOrigen;
Requisitos
La cantidad de columnas debe ser la misma.
Los tipos de datos deben ser compatibles.
Esta técnica permite realizar inserciones masivas de datos.

Lo más importante para recordar ⭐
✅ INSERT sirve para agregar registros.

✅ Existen tres formas de insertar datos:

Manera completa (recomendada)
Manera SQL (solo MySQL/MariaDB)
Manera simplificada

✅ NULL significa "dato desconocido" y no lleva comillas.

✅ Los campos NOT NULL son obligatorios.

✅ INSERT ... SELECT permite copiar registros entre tablas.
