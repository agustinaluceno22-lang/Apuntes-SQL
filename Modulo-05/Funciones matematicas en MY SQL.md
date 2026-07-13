Las funciones matemáticas son funciones integradas de MySQL que permiten realizar operaciones y cálculos numéricos sin necesidad de crear fórmulas manualmente.
Están optimizadas para ser rápidas, precisas y fáciles de utilizar.
Características principales

Las funciones matemáticas:

✅ Son predefinidas (ya vienen incorporadas en MySQL).
✅ Son eficientes para realizar cálculos rápidamente.
✅ Son precisas, incluso con números grandes o pequeños.
✅ Son portables, es decir, funcionan en cualquier instalación de MySQL.
✅ Incluyen operaciones básicas y avanzadas.
Funciones matemáticas vistas

En este módulo se presentan las siguientes funciones:

ROUND()
CEIL()
FLOOR()
MOD()
POW()
1. ROUND()

Redondea un número a la cantidad de decimales indicada.

Sintaxis
ROUND(valor, decimales)
valor → número a redondear.
decimales → cantidad de decimales que tendrá el resultado.
Ejemplo
SELECT ROUND(precio / 3, 2)
FROM articulos;

Si:

precio = 100

Entonces:

100 / 3 = 33.333333

Resultado:

33.33

Si el segundo parámetro es 0, devuelve un número entero.

SELECT ROUND(15.78,0);

Resultado:

16

Se utiliza para:

Redondear precios.
Mostrar promedios.
Presentar resultados con pocos decimales.
2. CEIL()

Devuelve el entero mayor al número indicado.

También se conoce como Ceiling (techo).

Sintaxis
CEIL(numero)
Ejemplo
SELECT CEIL(18.2);

Resultado:

19

Otro ejemplo:

SELECT precio,
       precio * 1.27 AS PrecioConAumento,
       CEIL(precio * 1.27) AS PrecioRedondeado
FROM articulos;

Si:

Precio con aumento = 25.4

Resultado:

26

Se utiliza para:

Redondear siempre hacia arriba.
Calcular cantidades mínimas necesarias.
3. FLOOR()

Devuelve el entero menor al número indicado.

Sintaxis
FLOOR(numero)
Ejemplo
SELECT FLOOR(18.9);

Resultado:

18

Otro ejemplo:

SELECT precio,
       precio * 1.27,
       FLOOR(precio * 1.27)
FROM articulos;

Si:

25.8

Resultado:

25

Se utiliza para:

Redondear siempre hacia abajo.
Eliminar la parte decimal.

Diferencia entre ROUND(), CEIL() y FLOOR()
| Función         | Ejemplo              | Resultado |
| --------------- | -------------------- | --------- |
| `ROUND(18.6,0)` | Redondeo tradicional | 19        |
| `ROUND(18.4,0)` | Redondeo tradicional | 18        |
| `CEIL(18.2)`    | Siempre hacia arriba | 19        |
| `FLOOR(18.9)`   | Siempre hacia abajo  | 18        |


4. MOD()

Obtiene el resto (residuo) de una división.

Sintaxis
MOD(dividendo, divisor)
Ejemplo
SELECT MOD(15,4);

Cálculo:

15 ÷ 4 = 3

Residuo:

3

Resultado:

3

Otro ejemplo:

SELECT MOD(20,5);

Resultado:

0

Porque la división es exacta.

Se utiliza para:

Saber si un número es par o impar.
Validaciones.
Operaciones matemáticas.
5. POW()

Eleva un número a una potencia.

Sintaxis
POW(base, exponente)
Ejemplo
SELECT POW(2,8);

Resultado:

256

Otro ejemplo:

SELECT POW(5,2);

Resultado:

25

Se utiliza para:

Potencias.
Fórmulas matemáticas.
Cálculos financieros y científicos.

RESUMEN RAPIDO PARA ESTUDIAR 
| Función   | ¿Qué hace?                                                |
| --------- | --------------------------------------------------------- |
| `ROUND()` | Redondea un número con la cantidad de decimales indicada. |
| `CEIL()`  | Devuelve el entero mayor (redondea hacia arriba).         |
| `FLOOR()` | Devuelve el entero menor (redondea hacia abajo).          |
| `MOD()`   | Devuelve el resto de una división.                        |
| `POW()`   | Eleva un número a una potencia.                           |

Truco para recordar
ROUND → redondeo normal.
CEIL → techo → siempre sube.
FLOOR → piso → siempre baja.
MOD → resto de una división.
POW → potencia (base^exponente).
