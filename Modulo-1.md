Un diagrama entidad-relación (ERD, por sus siglas en inglés) es una herramienta de modelado utilizada para representar y estructurar los datos de un sistema de información que parte
de una situación real a partir de la cual se definen los componentes del diagrama.

Tipos de relaciones: 

1 a 1: Un diagrama entidad-relación (ERD, por sus
siglas en inglés) es una herramienta de modelado
utilizada para representar y estructurar los
datos de un sistema de información que parte
de una situación real a partir de la cual se
definen los componentes del diagrama.

Uno a muchos
(1:N)
Una entidad puede estar
relacionada una o más
instancias de otra entidad

Muchos a muchos
(N:N)
Una entidad puede estar
relacionada con una o más
instancias de otra entidad y
viceversa.

Clave primaria (primary key). En un diagrama entidad-relación, la clave primaria es un atributo o conjunto de atributos que identifica de forma única a cada instancia
de una entidad. La clave primaria debe ser única, no nula. Además, puede ser simple o compuesta (formada por un conjunto de dos o más atributos). La clave primaria es un elemento 
fundamental en el diseño de una base de datos relacional, ya que, una bien diseñada garantiza la integridad y laconsistencia de los datos.

Clave foránea (foreign key) Una clave foránea en una tabla es aquella que hace referencia a la clave primaria de otra tabla
o de la misma. Al realizar una consulta SQL, se verifica la validez de los datos almacenados en la clave foránea. Esto asegura la integridad referencial. La clave foránea debe tener el mismo tipo de
datos que el campo al que referencia, es decir, la clave primaria.

Que es un DER? Un Diagrama de Entidad-Relación (DER) es una herramienta gráfica utilizada en el modelado de bases de datos. Su objetivo es representar de manera visual las entidades relevantes de un
sistema, las relaciones entre ellas y los atributos de cada entidad. Es un paso fundamental en la fase de diseño de bases de datos porque ayuda a entender y estructurar la información que se manejará.

CREACION DE UNA BASE DE DATOS: Para crear una base de datos (por ejemplo, con el nombre ComercioIT), la instrucción SQL a ejecutar será: CREATE DATABASE ComercioIT;

La sentencia CREATE TABLE creará una tabla con las columnas (campos) que indiquemos.
CREATE TABLE Productos(
idProducto INT(11) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
Nombre VARCHAR(50) NOT NULL,
Precio DOUBLE,
Marca VARCHAR(30) NOT NULL,
Categoria VARCHAR(30) NOT NULL,
Stock INT(6) NOT NULL,
Disponible BOOLEAN DEFAULT false
);

ELIMINAR UNA TABLA: Para eliminar una tabla (por ejemplo, con el nombre
Productos) de una base de datos, la instrucción SQL a
ejecutar será: DROP TABLE Productos; o DROP TABLE IF EXISTS Productos;

Puntos claves
1. Los nombres de las tablas deben ser únicos
en la base de datos. 2. Los nombres de las columnas debe ser
únicos en la tabla. 3. No podrán existir dos registros con el mismo
valor de la clave primaria.

Columnas no descomponibles: Son aquellas columnas que contienen cierta información que no puede almacenarse en dos
o más columnas.
● Son fáciles de actualizar.
● Son fáciles de consultar.
● Mejoran la implementación de la integridad
de los datos.

Modificadores aplicables a los campos de una tabla NOT NULL
No permite valores nulos. La carga del dato en ese campo será obligatoria. Es decir, el campo no
puede quedar vacío. NULL constituye un valor en sí (valor desconocido). No es vacío en un campo de
tipo texto, ni 0 en un campo numérico.
DEFAULT Permite especificar un valor predeterminado. 
Clave primaria (PRIMARY KEY)
Una tabla suele tener una columna o una combinación de columnas cuyos valores identifican de
forma única a cada registro de la tabla.
Estas columnas se denominan claves principales de la tabla y exigen la integridad de entidad de la
tabla (un solo registro con ese valor de indicador único). Cuando crees o modifiques una tabla,
puedes crear una clave primaria mediante la definición de una restricción PRIMARY KEY.

UNIQUE Indica que la columna no tendrá ningún valor repetido. Similar a PRIMARY KEY, pero a diferencia de
esta última, UNIQUE permite un valor nulo, y puede haber varias columnas de este tipo en una tabla.
BINARY Indica que los valores en esta columna se almacenarán en modo binario. Respeta el uso de
mayúsculas y minúsculas.
UNSIGNED Esta columna no usará un byte para el signo; es decir, permitirá almacenar números positivos
únicamente.
ZERO FILL Indica que el contenido del campo se completará con ceros (siempre que sea numérico).
AUTO_INCREMENT El motor de base de datos incrementará automáticamente su valor. Una tabla solo puede tener un
campo autoincremental y este tiene que formar parte de la PK (PRIMARY KEY). 


A continuación, se detallan comandos necesarios para la navegación dentro del motor MySQL:
Otros comandos MySQL
Comando SHOW DATABASES / Descripcion: Muestra el catálogo de base de datos del
servidor. Sintaxis: SHOW DATABASES;

Comando USE / Descripcion: Pone en uso una base de datos del servidor.
Todos los comandos SQL que se ejecuten, se
llevarán a cabo sobre la base de datos en uso. SINTAXIS USE NombredeBaseDeDatos;

Comando SHOW TABLES / Descripcion: Muestra el catálogo o listado de tablas de la
base de datos activa. SINTAXIS SHOW TABLES; 

Comando COMENTARIOS / Descripcion: Permiten escribir texto que no será interpretado como parte de sentencias SQL, útiles para documentar y comentar acciones
realizadas por las sentencias. Se pueden utilizar las siguientes formas deescribir comentarios: SINTAXIS 
# Esto es un comentario de 1 línea
(Propia de MySQL)
/* Esto es un comentario de 1 o más líneas */
(Soportada en MySQL y otros motores)
-- Esto es un comentario de 1 línea
(Soportada en MySQL y otros motores)

Comando DESCRIBE / Descripcion: Devuelve la descripción de campos y detalles
de una tabla (estructura física). SINTAXIS DESCRIBE NombreDeTabla;

Comando SHOW CHARSET / Descripcion: Muestra los CHARSET (juegos de caracteres). SINTAXIS SHOW CHARSET;

Comando SHOW COLLATION / Descripcion: Muestra los COLLATIONS instalados SINTAXIS SHOW COLLATION;

