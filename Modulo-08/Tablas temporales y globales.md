Tablas Temporales (Locales y Globales)
Las tablas temporales se crean en la base de datos especial tempdb y están diseñadas para almacenar datos de manera provisional sin afectar las tablas principales de la base de datos.
Son sumamente útiles para manejar datos intermedios o realizar cálculos complejos.
1. Tabla Temporal Local (#)Creación y Prefijo: Se definen anteponiendo un único símbolo de almohadilla (#) antes del nombre de la tabla.
2.  SQLCREATE TABLE #TablaTemporal (
    ID INT,
    Nombre NVARCHAR(50)
);

Visibilidad: Solo están disponibles para la sesión o conexión del usuario actual que las creó. No pueden ser compartidas con otras conexiones activas.
Duración: Se eliminan automáticamente cuando la sesión del usuario se cierra. También pueden eliminarse manualmente durante la sesión mediante la instrucción DROP TABLE #TablaTemporal. 
Particularidad: El nombre debe ser único dentro de la misma sesión, pero puede repetirse en sesiones diferentes, ya que el sistema les asigna internamente un sufijo único para diferenciarlas.

2. Tabla Temporal Global (##)Creación y Prefijo: Se definen utilizando un doble símbolo de almohadilla (##) antes del nombre de la tabla.
3.  SQLCREATE TABLE ##TablaTemporalGlobal (
    ID INT,
    Nombre NVARCHAR(50)

);
Visibilidad: Son accesibles por cualquier sesión o conexión activa en el servidor mientras existan. 
Duración: No se eliminan inmediatamente cuando la sesión que las creó finaliza, siempre y cuando existan otras conexiones activas que las estén utilizando en ese momento. 
Se destruyen automáticamente cuando la última conexión que las referencia se cierra.  Desafío de uso: Dado que múltiples usuarios o procesos pueden consultar y modificar la 
misma tabla temporal global de forma simultánea, es sumamente importante implementar estrategias de control de concurrencia para evitar conflictos o inconsistencias en los datos. 


## Tabla Comparativa: Temporal Local vs. Global

| Característica |   Local (`#`) |                   Global (`##`) |
| :--- | :--- | :--- |
| **¿Quién la ve?** | Solo tú (tu sesión). |        Todos los usuarios conectados. |
| **¿Cómo se crea?** | Con un solo numeral (`#`). |  Con doble numeral (`##`). |
| **¿Dónde se guarda?**| En `tempdb`. |                      En `tempdb`. |
| **¿Cuándo se borra?** | Al cerrar tu sesión. |      Al cerrarse la última sesión que la use. |
| **¿Para qué sirve?** | Tus propias consultas y tareas. | Compartir datos entre varias personas/procesos. |
