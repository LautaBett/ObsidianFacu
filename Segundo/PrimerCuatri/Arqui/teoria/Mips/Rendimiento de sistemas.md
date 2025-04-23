
# Resumen: Rendimiento de Sistemas

Este documento explica cómo se mide y mejora el rendimiento de los sistemas informáticos.

## 1. ¿Qué es el Rendimiento?

Hay dos formas principales de medir qué tan "bueno" es un sistema:

1.  **Tiempo de Respuesta (Latencia):**
    *   Es el tiempo total que tarda una tarea en completarse, desde que empieza hasta que termina.
    *   *Ejemplo:* Cuánto tarda en abrirse una aplicación o en cargar una página web.
    *   **Mejor rendimiento = Menor tiempo de respuesta.**

2.  **Throughput (Ancho de Banda / Productividad):**
    *   Es la cantidad de trabajo que el sistema puede hacer en un período de tiempo determinado.
    *   *Ejemplo:* Cuántas búsquedas puede procesar un servidor web por segundo.
    *   **Mejor rendimiento = Mayor throughput.**

## 2. Comparando el Rendimiento

*   Cuando comparamos dos máquinas (A y B), decimos que A es más rápida si tarda menos tiempo en hacer la misma tarea.
*   La relación es: Si A es un *n%* más rápida que B, entonces:
    $\frac{T_B}{T_A} = 1 + \frac{n}{100}$
*   El rendimiento es el inverso del tiempo de ejecución:
    $R = \frac{1}{T}$
*   Por lo tanto, la relación anterior también se puede escribir como:
    $\frac{R_A}{R_B} = 1 + \frac{n}{100}$

## 3. Aceleración del Caso Común

*   **Principio Clave:** Es más efectivo mejorar las partes del sistema que se usan *más frecuentemente*.
*   Optimizar algo que casi nunca se usa tendrá poco impacto en el rendimiento general. Intentar optimizar *todo* puede ser costoso y no siempre efectivo.

## 4. Ley de Amdahl

*   **¿Para qué sirve?:** Permite estimar la *mejora máxima* de rendimiento que se puede obtener en un sistema cuando *solo una parte* de él se acelera.
*   **La Idea Central:** La mejora total está limitada por la proporción del tiempo que *no* se beneficia de la mejora. Si una tarea tiene una parte que no se puede acelerar, nunca podrás hacer que la tarea completa sea infinitamente rápida, por mucho que aceleres la otra parte.
*   **Fórmula:**
    $Acc_G = \frac{T_o}{T_m} = \frac{1}{(1 - F_m) + \frac{F_m}{Acc_m}}$
    Donde:
    *   $Acc_G$: Aceleración Global.
    *   $F_m$: Fracción mejorada.
    *   $Acc_m$: Aceleración de la parte mejorada.
    *   $T_o$: Tiempo original.
    *   $T_m$: Tiempo mejorado.
*   **Corolario (Aceleración Máxima):** La máxima aceleración teórica que se puede lograr es:
    $Aceleración\ Máxima = \frac{1}{1 - F_m}$
*   **Múltiples Mejoras:** La ley se puede extender para calcular la aceleración cuando se aplican varias mejoras a distintas partes.

## 5. Rendimiento Específico de la CPU

El tiempo que una CPU tarda en ejecutar un programa depende de:

1.  **Número de Ciclos de Reloj:**
2.  **Duración del Ciclo de Reloj (o Frecuencia):**

*   Tiempo CPU = Ciclos de reloj para el programa × Duración de un ciclo de reloj
*   $Tiempo\ CPU = \frac{Ciclos\ de\ reloj}{Frecuencia\ de\ reloj}$

También se puede usar el **CPI (Ciclos Por Instrucción):**

*   $CPI = \frac{Ciclos\ de\ reloj}{Número\ de\ instrucciones}$
*   Tiempo CPU = Número de Instrucciones × CPI × Duración de un ciclo de reloj

## 6. Factores que Influyen en el Rendimiento

El rendimiento final es una combinación de:

*   **Tecnología de Hardware:**
*   **Organización:**
*   **Arquitectura (ISA):**
*   **Compilador:**