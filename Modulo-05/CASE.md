Condicional CASE en SQL; El CASE es un condicional de SQL que sirve para asignar un valor según una condición, de manera similar a un if...else en otros lenguajes de programación.

Se utiliza para:
Crear una nueva columna con valores personalizados.
Clasificar datos.
Mostrar distintos resultados según el contenido de una columna.
Sintaxis
SELECT columna,
       CASE
           WHEN condicion1 THEN resultado1
           WHEN condicion2 THEN resultado2
           ELSE resultado3
       END AS NombreColumna
FROM Tabla;
Partes del CASE
CASE → inicia el condicional.
WHEN → condición a evaluar.
THEN → resultado si la condición es verdadera.
ELSE → resultado si ninguna condición se cumple (opcional).
END → finaliza el CASE.
Cómo funciona
CASE
   ↓
¿Se cumple el WHEN?
      │
     Sí ───► ejecuta THEN
      │
     No
      │
¿Se cumple otro WHEN?
      │
     Sí ───► ejecuta ese THEN
      │
     No
      │
    ELSE
      │
     END

Ejemplo 1: Clasificar productos por precio
SELECT Nombre,
       Precio,
       CASE
           WHEN Precio < 20 THEN 'BARATO'
           WHEN Precio BETWEEN 20 AND 40 THEN 'EQUILIBRADO'
           ELSE 'CARO'
       END AS Categoria
FROM Articulos;

Resultado:

Nombre	Precio	Categoría
Mouse	15	BARATO
Teclado	30	EQUILIBRADO
Monitor	80	CARO

Este ejemplo clasifica los productos según el valor de la columna Precio.

Ejemplo 2: Clasificar empleados por puesto
SELECT IdEmpleado,
       Puesto,
       CASE
           WHEN Puesto IN ('Auxiliar','Asistente')
               THEN 'Nivel Básico'

           WHEN Puesto IN ('Analista','Programador')
               THEN 'Nivel Medio'

           ELSE 'Nivel Alto'
       END AS NivelEmpleado
FROM Empleados;

Resultado:

Empleado	Puesto	Nivel
Ana	Auxiliar	Nivel Básico
Juan	Programador	Nivel Medio
Pedro	Gerente	Nivel Alto

En este caso se usa IN para agrupar varios valores dentro de una misma condición.

Cuándo usar CASE

Usá CASE cuando necesites:

✔ Clasificar salarios (Bajo, Medio, Alto).
✔ Clasificar edades (Niño, Adulto, Mayor).
✔ Mostrar "Sí" o "No" según una condición.
✔ Cambiar el texto que devuelve una consulta.
✔ Crear columnas calculadas sin modificar la tabla.
Para recordar
CASE funciona como un IF en SQL.
Se pueden usar varios WHEN.
Solo se ejecuta el primer WHEN que se cumple.
ELSE es opcional, pero recomendable.
Siempre termina con END.
