Las funciones de fecha permiten obtener información de una fecha, realizar cálculos entre fechas y sumar o restar períodos de tiempo.
Son muy útiles para trabajar con vencimientos, antigüedad, reportes y filtros por fechas.

1. YEAR()

Obtiene el año de una fecha.

Sintaxis
SELECT YEAR(fecha);
Ejemplo
SELECT YEAR(fecha) AS Año
FROM facturas;

Resultado

fecha	Año
2024-05-10	2024

Se usa para: agrupar o filtrar datos por año.

2. MONTH()

Obtiene el mes de una fecha.

Ejemplo
SELECT MONTH(fecha) AS Mes
FROM facturas;

Resultado

fecha	Mes
2024-05-10	5

Se usa para: consultas mensuales.

3. DAY()

Obtiene el día del mes.

Ejemplo
SELECT DAY(fecha) AS Dia
FROM facturas;

Resultado

fecha	Día
2024-05-10	10

4. HOUR()

Obtiene la hora de un campo DATETIME.

Ejemplo
SELECT HOUR(fecha) AS Hora
FROM facturas;

Resultado

fecha	Hora
2024-05-10 15:30:45	15

5. CURDATE()

Devuelve la fecha actual del sistema.

Ejemplo
SELECT CURDATE() AS FechaActual;

Resultado

2026-07-13

(La fecha dependerá del día en que se ejecute la consulta.)

6. CURTIME()

Devuelve la hora actual del sistema.

Ejemplo
SELECT CURTIME() AS HoraActual;

Resultado

14:35:18

(La hora dependerá del momento de ejecución.)

7. DATEDIFF()

Calcula la cantidad de días entre dos fechas.

Sintaxis
DATEDIFF(fecha_final, fecha_inicial)
Ejemplo 1
SELECT DATEDIFF('2020-06-30','2020-01-01') AS Dias;

Resultado

181
Ejemplo 2
SELECT DATEDIFF(CURDATE(), fecha_emision) AS DiasTranscurridos
FROM facturas;

Se utiliza para calcular cuántos días pasaron desde una fecha hasta hoy.

8. TIMESTAMPDIFF()

Calcula la diferencia entre dos fechas en una unidad específica.

Las unidades más comunes son:

YEAR
MONTH
DAY
HOUR
Ejemplo 1
SELECT TIMESTAMPDIFF(
MONTH,
'2020-01-01',
'2020-06-30'
) AS Meses;

Resultado:

5
Ejemplo 2
SELECT TIMESTAMPDIFF(
YEAR,
fecha_emision,
CURDATE()
) AS AñosTranscurridos
FROM facturas;

Se utiliza para calcular edad, antigüedad de empleados o tiempo desde una compra.

9. DAYNAME()

Devuelve el nombre del día de la semana.

Ejemplo
SELECT DAYNAME(CURDATE()) AS NombreDia;

Resultado:

Monday

(El idioma depende de la configuración de MySQL.)

10. DAYOFWEEK()

Devuelve el número del día de la semana.

Ejemplo
SELECT DAYOFWEEK(CURDATE()) AS NumeroDia;

Resultado aproximado:

Día	Número
Domingo	1
Lunes	2
Martes	3
Miércoles	4
Jueves	5
Viernes	6
Sábado	7

11. DAYOFYEAR()

Devuelve el número del día dentro del año.

Ejemplo
SELECT DAYOFYEAR(CURDATE()) AS DiaDelAño;

Resultado:

194

(Dependerá de la fecha actual.)

12. MONTHNAME()

Devuelve el nombre del mes.

Ejemplo
SELECT MONTHNAME(CURDATE()) AS NombreMes;

Resultado:

July

(El idioma depende de la configuración del servidor.)

13. ADDDATE()

Permite sumar días, meses o años a una fecha.

Sintaxis
ADDDATE(fecha, INTERVAL cantidad unidad)
Ejemplos

Agregar 90 días:

SELECT ADDDATE(CURDATE(), INTERVAL 90 DAY);

Agregar 2 meses:

SELECT ADDDATE(CURDATE(), INTERVAL 2 MONTH);

Agregar 2 años:

SELECT ADDDATE(CURDATE(), INTERVAL 2 YEAR);

Se utiliza para calcular fechas de vencimiento, renovaciones o plazos futuros.

RESUMEN RAPIDO PARA ESTUDIAR 
| Función           | ¿Qué hace?                                        |
| ----------------- | ------------------------------------------------- |
| `YEAR()`          | Obtiene el año.                                   |
| `MONTH()`         | Obtiene el mes.                                   |
| `DAY()`           | Obtiene el día del mes.                           |
| `HOUR()`          | Obtiene la hora.                                  |
| `CURDATE()`       | Devuelve la fecha actual.                         |
| `CURTIME()`       | Devuelve la hora actual.                          |
| `DATEDIFF()`      | Calcula días entre dos fechas.                    |
| `TIMESTAMPDIFF()` | Calcula diferencias en años, meses, días u horas. |
| `DAYNAME()`       | Devuelve el nombre del día.                       |
| `DAYOFWEEK()`     | Devuelve el número del día de la semana.          |
| `DAYOFYEAR()`     | Devuelve el número del día dentro del año.        |
| `MONTHNAME()`     | Devuelve el nombre del mes.                       |
| `ADDDATE()`       | Suma días, meses o años a una fecha.              |
