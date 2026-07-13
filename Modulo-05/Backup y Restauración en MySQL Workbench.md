Backup y Restauración en MySQL Workbench

Un backup es una copia de seguridad de una base de datos. Su objetivo es poder recuperar la información si la base de datos se daña, se elimina accidentalmente o presenta algún 
roblema. MySQL Workbench permite crear y restaurar backups de forma sencilla mediante las opciones Server Data Export y Server Data Import.

¿Qué es un Backup?

Un backup consiste en generar una copia de una base de datos para poder restaurarla en caso de pérdida o corrupción de la información.

¿Para qué sirve?

Evitar la pérdida de datos.
Recuperar una base de datos dañada.
Guardar una copia antes de realizar cambios importantes.
Migrar una base de datos a otro equipo.
Crear un Backup en MySQL Workbench
Paso 1: Abrir la herramienta de exportación

En MySQL Workbench ir al menú:

Server → Data Export

Esto abre la ventana para generar el respaldo de la base de datos.

Paso 2: Seleccionar la base de datos

En la sección Tables to Export:

Seleccionar la base de datos que se desea respaldar.
Por defecto, se seleccionan todas las tablas.
Si es necesario, se pueden desmarcar las tablas que no se quieran incluir en el backup.
Paso 3: Elegir el tipo de exportación

Dentro de Export Options existen dos opciones principales:

Export to Dump Project Folder

Genera una carpeta con un archivo independiente para cada tabla.

Export to Self-Contained File ✅ (más utilizada)

Genera un único archivo .sql con toda la base de datos.

Es la opción recomendada cuando se desea guardar o compartir un respaldo completo.

Paso 4: Elegir la ubicación
Hacer clic en el botón de los tres puntos (...).
Elegir la carpeta donde se guardará el archivo.
Escribir el nombre del backup.

Ejemplo:

Laboratorio_Backup.sql

Paso 5: Generar el backup

Presionar:

Start Export

MySQL Workbench comenzará a crear el archivo de respaldo.

Restaurar un Backup

La restauración permite recuperar una base de datos utilizando un archivo de respaldo generado anteriormente.

Paso 1: Abrir la herramienta de importación

Ir a:

Server → Data Import

Se abrirá la ventana de restauración.

Paso 2: Seleccionar el archivo

Como el backup fue creado en un único archivo, seleccionar:

Import from Self-Contained File

Luego:

Hacer clic en los tres puntos (...).
Buscar el archivo .sql.
Seleccionarlo.
Paso 3: Restaurar

Presionar:

Start Import

MySQL restaurará la base de datos utilizando el archivo seleccionado.

Paso 4: Verificar

Una vez finalizada la importación:

Cerrar la ventana.
Verificar que la base de datos aparezca en el navegador de objetos.
Si no aparece, actualizar el panel (Refresh) para que se muestre.
Flujo completo
Crear Backup

Server
   ↓
Data Export
   ↓
Seleccionar Base de Datos
   ↓
Export to Self-Contained File
   ↓
Elegir ubicación
   ↓
Start Export

↓

Restaurar Backup

Server
   ↓
Data Import
   ↓
Import from Self-Contained File
   ↓
Seleccionar archivo .sql
   ↓
Start Import
   ↓
Verificar Base de Datos
Resumen rápido para estudiar
Acción	Menú	Botón final
Crear Backup	Server → Data Export	Start Export
Restaurar Backup	Server → Data Import	Start Import
Conceptos importantes
Backup → copia de seguridad de una base de datos.
Data Export → opción para crear un respaldo.
Data Import → opción para restaurar un respaldo.
Export to Self-Contained File → genera un único archivo .sql.
Start Export → inicia la creación del backup.
Start Import → inicia la restauración del backup.

💡 Consejo para el examen: recordá la diferencia entre Export (crear un respaldo) e Import (restaurar un respaldo). Son dos opciones que suelen preguntarse porque representan procesos opuestos dentro de MySQL Workbench.
