📌 Importar tablas desde orígenes externos
En muchas ocasiones, la información de una empresa se encuentra almacenada en archivos de Microsoft Excel o Microsoft Access. Cuando la cantidad de datos crece, resulta conveniente importar esa información a una base de datos MySQL para administrarla de manera más eficiente.

MySQL Workbench permite importar tablas desde archivos externos.
📄 Formatos compatibles

MySQL Workbench solo permite importar tablas desde archivos con los siguientes formatos:

CSV (.csv)
JSON (.json)

Importante: Los archivos de Excel (.xlsx) o Access (.accdb) deben convertirse previamente a un formato compatible, como CSV.

⚠️ Tipos de datos durante la importación

Al importar una tabla desde un archivo externo:

Los campos no tienen definidos tipos de datos ni restricciones.
MySQL Workbench intenta asignar automáticamente un tipo de dato a cada columna según su contenido.
El usuario puede modificar esos tipos antes de finalizar la importación.
Las restricciones (Primary Key, Foreign Key, NOT NULL, etc.) deben agregarse posteriormente utilizando ALTER TABLE.
📥 Importar una tabla desde CSV o JSON
Pasos
Abrir MySQL Workbench.
Hacer clic derecho sobre la base de datos.
Seleccionar Table Data Import Wizard.
Pulsar Browse y seleccionar el archivo CSV o JSON.
Hacer clic en Next.
Elegir una de las opciones:
Importar los datos en una tabla existente.
Crear una tabla nueva (Create New Table).
Asignar o modificar los tipos de datos de cada columna.
Confirmar la importación.
Esperar a que finalice el proceso.
Revisar el resumen de la importación.
Pulsar Finish.
Actualizar los esquemas (Refresh) para visualizar la nueva tabla.
📊 Información que muestra el asistente

Al finalizar la importación, MySQL Workbench informa:

Tiempo que tardó la importación.
Confirmación de que la tabla fue creada correctamente.
Cantidad de registros importados.
📄 Crear tablas desde un script SQL

Además de importar archivos CSV o JSON, también es posible crear tablas ejecutando un script SQL.

Un script SQL contiene instrucciones como:

CREATE DATABASE
CREATE TABLE
INSERT INTO

Al ejecutarlo, MySQL genera automáticamente la estructura de la base de datos.

▶️ Ejecutar un script SQL
Pasos
Abrir MySQL Workbench.
Seleccionar File → Open SQL Script.
Buscar y abrir el archivo .sql.
Ejecutar el script.
Actualizar los esquemas para visualizar las tablas creadas.
📝 Resumen rápido
Concepto         	Descripción
CSV	                          Formato compatible para importar tablas.
JSON                         	Formato compatible para importar tablas.
Table Data Import Wizard     	Asistente de MySQL Workbench para importar datos.
Browse	                      Permite seleccionar el archivo a importar.
Create New Table	            Crea una nueva tabla durante la importación.
ALTER TABLE                 	Permite agregar restricciones después de importar los datos.
SQL Script (.sql)            	Archivo con instrucciones SQL para crear bases de datos y tablas.
File → Open SQL Script      	Opción para abrir y ejecutar un script SQL.
