Claro, aquí están las soluciones a los ejercicios del Trabajo Práctico 2, basadas en los conceptos de la nota [[Rendimiento de sistemas]]:

**1. Aceleración Global con Múltiples Mejoras**

Usamos la Ley de Amdahl extendida para múltiples mejoras:
$Acc_G = \frac{1}{(1 - \sum F_{mi}) + \sum \frac{F_{mi}}{Acc_{mi}}}$

Datos:
*   Fracción 1 ($F_{m1}$) = 0,2
*   Aceleración 1 ($Acc_{m1}$) = 2
*   Fracción 2 ($F_{m2}$) = 0,15
*   Aceleración 2 ($Acc_{m2}$) = 1,5

La fracción no mejorada es $1 - (F_{m1} + F_{m2}) = 1 - (0,2 + 0,15) = 1 - 0,35 = 0,65$.

Calculamos la aceleración global:
$Acc_G = \frac{1}{(0,65) + \frac{0,2}{2} + \frac{0,15}{1,5}}$
$Acc_G = \frac{1}{0,65 + 0,1 + 0,1}$
$Acc_G = \frac{1}{0,85} \approx 1,176$

La aceleración global del sistema es aproximadamente **1,176**.

**2. Fracción Mejorada para Aceleración Máxima**

La aceleración global máxima teórica se da por:
$Acc_{G,max} = \frac{1}{1 - F_m}$

Datos:
*   Aceleración global máxima ($Acc_{G,max}$) = 700% = 7

Calculamos la fracción mejorada ($F_m$):
$7 = \frac{1}{1 - F_m}$
$7(1 - F_m) = 1$
$7 - 7F_m = 1$
$6 = 7F_m$
$F_m = \frac{6}{7} \approx 0,857$

La fracción que involucra mejoras es **6/7** (aproximadamente 85,7%).
Para alcanzar la *máxima* aceleración teórica, la aceleración necesaria en esa fracción ($Acc_m$) tiende a infinito ($Acc_m \to \infty$).

**3. Mejora de Unidad Aritmética y Memoria**

Datos:
*   Tiempo operaciones aritméticas ($T_{arith}$) = 5 μs
*   Tiempo acceso a memoria ($T_{mem}$) = 15 μs
*   Tiempo total original ($T_o$) = 50 μs
*   Mejora aritmética: 2 veces más rápida ($Acc_{arith} = 2$)
*   Mejora memoria: Nuevo tiempo = 10 μs

a) **Hallar las fracciones mejoradas:**
*   Fracción aritmética ($F_{arith}$) = $T_{arith} / T_o = 5 / 50 = 0,1$
*   Fracción memoria ($F_{mem}$) = $T_{mem} / T_o = 15 / 50 = 0,3$

b) **Hallar las aceleraciones mejoradas:**
*   Aceleración aritmética ($Acc_{arith}$) = 2 (dado)
*   Aceleración memoria ($Acc_{mem}$) = $T_{mem\_original} / T_{mem\_mejorado} = 15 \mu s / 10 \mu s = 1,5$

**Mejora global:**
La fracción no mejorada es $1 - (F_{arith} + F_{mem}) = 1 - (0,1 + 0,3) = 1 - 0,4 = 0,6$.
$Acc_G = \frac{1}{(1 - (F_{arith} + F_{mem})) + \frac{F_{arith}}{Acc_{arith}} + \frac{F_{mem}}{Acc_{mem}}}$
$Acc_G = \frac{1}{0,6 + \frac{0,1}{2} + \frac{0,3}{1,5}}$
$Acc_G = \frac{1}{0,6 + 0,05 + 0,2}$
$Acc_G = \frac{1}{0,85} \approx 1,176$

La mejora global del sistema es aproximadamente **1,176**.

**4. Mejoras Sucesivas en Etapas del Procesador**

Datos Procesador A:
*   Tiempo total por instrucción ($T_A$) = 20+10+40+20+10 = 100 ns.
*   Etapas y tiempos: F=20, D=10, Ex=40, Mem=20, Wb=10 ns.

Procesador B (mejora F y Ex de A por 1,5):
*   $F_F = 20/100 = 0,2$; $Acc_F = 1,5$
*   $F_{Ex} = 40/100 = 0,4$; $Acc_{Ex} = 1,5$
*   $Acc_{B\_vs\_A} = \frac{1}{(1 - (0,2+0,4)) + \frac{0,2}{1,5} + \frac{0,4}{1,5}} = \frac{1}{0,4 + \frac{0,6}{1,5}} = \frac{1}{0,4 + 0,4} = \frac{1}{0,8} = 1,25$.
*   Tiempo de B: $T_B = T_A / Acc_{B\_vs\_A} = 100 ns / 1,25 = 80 ns$.

Procesador C (mejora etapas de B por 2):
Necesitamos las fracciones de tiempo de las etapas *en B*:
*   $T_{F\_B} = 20/1,5 \approx 13,33 ns$
*   $T_{D\_B} = 10 ns$
*   $T_{Ex\_B} = 40/1,5 \approx 26,67 ns$
*   $T_{Mem\_B} = 20 ns$
*   $T_{Wb\_B} = 10 ns$
*   Suma = $13,33 + 10 + 26,67 + 20 + 10 = 80 ns = T_B$.

a) **Mejora C sobre Mem y Wb de B (Acc=2):**
*   Fracciones en B: $F_{Mem\_B} = 20/80 = 0,25$; $F_{Wb\_B} = 10/80 = 0,125$.
*   $Acc_{C\_vs\_B} = \frac{1}{(1 - (F_{Mem\_B} + F_{Wb\_B})) + \frac{F_{Mem\_B}}{2} + \frac{F_{Wb\_B}}{2}}$
*   $Acc_{C\_vs\_B} = \frac{1}{(1 - (0,25 + 0,125)) + \frac{0,25}{2} + \frac{0,125}{2}}$
*   $Acc_{C\_vs\_B} = \frac{1}{(1 - 0,375) + 0,125 + 0,0625} = \frac{1}{0,625 + 0,125 + 0,0625} = \frac{1}{0,8125} = 1,2307...$
    La aceleración global de C respecto de B es **1,231**.

b) **Mejora C sobre Ex y Wb de B (Acc=2):**
*   Fracciones en B: $F_{Ex\_B} = (40/1,5) / 80 = (80/3) / 80 = 1/3$; $F_{Wb\_B} = 10/80 = 1/8$.
*   $Acc_{C\_vs\_B} = \frac{1}{(1 - (F_{Ex\_B} + F_{Wb\_B})) + \frac{F_{Ex\_B}}{2} + \frac{F_{Wb\_B}}{2}}$
*   $Acc_{C\_vs\_B} = \frac{1}{(1 - (1/3 + 1/8)) + \frac{1/3}{2} + \frac{1/8}{2}}$
*   $Acc_{C\_vs\_B} = \frac{1}{(1 - (8/24 + 3/24)) + 1/6 + 1/16} = \frac{1}{(1 - 11/24) + 1/6 + 1/16}$
*   $Acc_{C\_vs\_B} = \frac{1}{13/24 + 1/6 + 1/16} = \frac{1}{13/24 + 4/24 + 1.5/24} = \frac{1}{(26+8+3)/48} = \frac{1}{37/48} = 48/37 \approx 1,297$
    La aceleración global de C respecto de B es **48/37** (aproximadamente **1,297**).

**5. Comparación de Máquinas con Nueva Instrucción**

Máquina Original (M1):
*   $CPI_{avg1} = (0,15 \times 2) + (0,47 \times 1) + (0,32 \times 4) + (0,06 \times 6)$
*   $CPI_{avg1} = 0,30 + 0,47 + 1,28 + 0,36 = 2,41$
*   Tiempo M1: $T_1 = I \times CPI_{avg1} \times C = 2,41 \times I \times C$ (donde I=nº inst., C=ciclo reloj)

Máquina Mejorada (M2):
*   Ciclo de reloj: $C' = 1,05 \times C$.
*   Nueva instrucción reemplaza ADD (CPI=1) + LOAD (CPI=4). Se usa en 25% de las transferencias (que son 32% del total).
*   Instrucciones reemplazadas: $0,25 \times 0,32 \times I = 0,08 \times I$ secuencias ADD+LOAD.
*   Instrucciones eliminadas: $0,08 \times I$ (ADD) + $0,08 \times I$ (LOAD) = $0,16 \times I$.
*   Instrucciones nuevas añadidas: $0,08 \times I$. Asumimos CPI=4 para la nueva instrucción (similar a LOAD).
*   Total instrucciones M2: $I' = I - 0,16 I + 0,08 I = 0,92 I$.
*   Cálculo de $CPI_{avg2}$:
    *   Ciclos originales = $I \times CPI_{avg1} = 2,41 I$.
    *   Ciclos eliminados = $0,08 I \times (CPI_{ADD} + CPI_{LOAD}) = 0,08 I \times (1 + 4) = 0,4 I$.
    *   Ciclos añadidos = $0,08 I \times CPI_{nueva} = 0,08 I \times 4 = 0,32 I$.
    *   Ciclos totales M2 = $2,41 I - 0,4 I + 0,32 I = 2,33 I$.
    *   $CPI_{avg2} = \frac{Ciclos\ totales\ M2}{Instrucciones\ totales\ M2} = \frac{2,33 I}{0,92 I} \approx 2,5326$.
*   Tiempo M2: $T_2 = I' \times CPI_{avg2} \times C' = (0,92 I) \times (2,5326) \times (1,05 C)$
*   $T_2 \approx (0,92 \times 2,5326 \times 1,05) \times I \times C \approx 2,446 \times I \times C$.

Comparación:
*   $T_1 = 2,41 \times I \times C$
*   $T_2 = 2,446 \times I \times C$
Como $T_1 < T_2$, la **máquina original (M1) es más rápida**.

¿Por cuánto?
*   Relación de tiempos: $T_2 / T_1 = 2,446 / 2,41 \approx 1,015$.
*   La máquina M1 es aproximadamente un **1,5%** más rápida que M2.

**6. Comparación de Mejoras (Float vs Memoria)**

Datos:
*   Fracción coma flotante ($F_{float}$) = 0,25
*   Fracción acceso a memoria ($F_{mem}$) = 0,50
*   Fracción otras tareas ($F_{other}$) = 1 - 0,25 - 0,50 = 0,25
*   Mejora 1: Float 4x más rápido ($Acc_{float} = 4$)
*   Mejora 2: Memoria 2x más rápida ($Acc_{mem} = 2$)

a) **Efectividad de cada mejora por separado:**
*   Aceleración con Mejora 1 (Float):
    $Acc_{G1} = \frac{1}{(1 - F_{float}) + \frac{F_{float}}{Acc_{float}}} = \frac{1}{(1 - 0,25) + \frac{0,25}{4}} = \frac{1}{0,75 + 0,0625} = \frac{1}{0,8125} \approx 1,231$
*   Aceleración con Mejora 2 (Memoria):
    $Acc_{G2} = \frac{1}{(1 - F_{mem}) + \frac{F_{mem}}{Acc_{mem}}} = \frac{1}{(1 - 0,50) + \frac{0,50}{2}} = \frac{1}{0,50 + 0,25} = \frac{1}{0,75} \approx 1,333$

Como $Acc_{G2} > Acc_{G1}$, la **mejora 2 (memoria) es más efectiva**.

b) **Aceleración global aplicando ambas mejoras:**
*   $Acc_{G\_both} = \frac{1}{(1 - (F_{float} + F_{mem})) + \frac{F_{float}}{Acc_{float}} + \frac{F_{mem}}{Acc_{mem}}}$
*   $Acc_{G\_both} = \frac{1}{F_{other} + \frac{F_{float}}{Acc_{float}} + \frac{F_{mem}}{Acc_{mem}}}$
*   $Acc_{G\_both} = \frac{1}{0,25 + \frac{0,25}{4} + \frac{0,50}{2}}$
*   $Acc_{G\_both} = \frac{1}{0,25 + 0,0625 + 0,25} = \frac{1}{0,5625} = 1,777...$

La aceleración global aplicando ambas mejoras es **16/9** (aproximadamente **1,778**).

**7. Mejora con Datos Post-Mejora**

Datos:
*   Aceleración de la parte mejorada ($Acc_m$) = 10
*   Fracción del *nuevo* tiempo total usada por las instrucciones mejoradas = 50% = 0,5

Sea $T_o$ el tiempo original y $T_m$ el tiempo mejorado.
Sea $T_{o,imp}$ el tiempo original de la parte mejorada y $T_{o,unimp}$ el tiempo original de la parte no mejorada.
$T_o = T_{o,imp} + T_{o,unimp}$
$F_m = T_{o,imp} / T_o$ (Fracción de tiempo *original* mejorada)

El tiempo mejorado es $T_m = T_{m,imp} + T_{m,unimp}$.
$T_{m,unimp} = T_{o,unimp}$
$T_{m,imp} = T_{o,imp} / Acc_m = T_{o,imp} / 10$

Nos dicen que $T_{m,imp} = 0,5 \times T_m$.
Sustituyendo: $T_{o,imp} / 10 = 0,5 T_m \implies T_{o,imp} = 5 T_m$.

También sabemos que $T_m = T_{m,imp} + T_{m,unimp} = 0,5 T_m + T_{o,unimp}$.
Despejando: $0,5 T_m = T_{o,unimp}$.

Ahora sustituimos $T_{o,imp}$ y $T_{o,unimp}$ en la ecuación de $T_o$:
$T_o = T_{o,imp} + T_{o,unimp} = (5 T_m) + (0,5 T_m) = 5,5 T_m$.

a) **Mejora obtenida (Aceleración Global):**
$Acc_G = T_o / T_m = (5,5 T_m) / T_m = 5,5$.
La mejora global es **5,5**.

b) **Valor de la fracción de tiempo mejorada ($F_m$):**
$F_m = T_{o,imp} / T_o = (5 T_m) / (5,5 T_m) = 5 / 5,5 = 50 / 55 = 10 / 11$.
La fracción de tiempo original mejorada es **10/11** (aproximadamente 90,9%).

**8. Mejora en Saltos y Frecuencia de Reloj**

Datos:
*   CPI Salto original = 10 ciclos
*   CPI Otras original = 1 ciclo
*   Fracción de instrucciones de salto = 10% = 0,1
*   Mejora 1: CPI Salto nuevo = 10 / 2 = 5 ciclos ($Acc_{salto\_exec} = 2$)
*   Mejora 2: Frecuencia reloj aumenta 25% ($f' = 1,25 f \implies C' = C / 1,25 = 0,8 C$). $Acc_{clock} = 1,25$.

Calculamos la fracción de *tiempo* original dedicada a saltos ($F_{m,salto}$):
*   Ciclos por instrucción promedio original: $CPI_{avg} = (0,1 \times 10) + (0,9 \times 1) = 1 + 0,9 = 1,9$.
*   Tiempo original: $T_o = I \times CPI_{avg} \times C = 1,9 \times I \times C$.
*   Tiempo original en saltos: $T_{o,salto} = (I \times 0,1) \times 10 \times C = 1,0 \times I \times C$.
*   $F_{m,salto} = T_{o,salto} / T_o = (1,0 \times I \times C) / (1,9 \times I \times C) = 1,0 / 1,9 = 10/19$.

a) **Aceleración global aplicando solo la primera mejora (ejecución de saltos):**
*   $Acc_{G1} = \frac{1}{(1 - F_{m,salto}) + \frac{F_{m,salto}}{Acc_{salto\_exec}}}$
*   $Acc_{G1} = \frac{1}{(1 - 10/19) + \frac{10/19}{2}} = \frac{1}{9/19 + 5/19} = \frac{1}{14/19} = 19/14 \approx 1,357$
    La aceleración global solo con la mejora de saltos es **19/14**.

b) **Aceleración global aplicando ambas mejoras simultáneamente:**
La mejora del reloj afecta a todo el tiempo de ejecución restante después de aplicar la mejora de saltos. Podemos multiplicar las aceleraciones:
*   $Acc_{G\_both} = Acc_{G1} \times Acc_{clock}$
*   $Acc_{G\_both} = (19/14) \times 1,25 = (19/14) \times (5/4) = 95/56 \approx 1,696$

Alternativamente, calculamos el nuevo tiempo total $T_m$:
*   Nuevo CPI promedio: $CPI_{avg\_nuevo} = (0,1 \times 5) + (0,9 \times 1) = 0,5 + 0,9 = 1,4$.
*   Nuevo ciclo de reloj: $C' = 0,8 C$.
*   Nuevo tiempo total: $T_m = I \times CPI_{avg\_nuevo} \times C' = I \times 1,4 \times (0,8 C) = 1,12 \times I \times C$.
*   Aceleración global: $Acc_{G\_both} = T_o / T_m = (1,9 \times I \times C) / (1,12 \times I \times C) = 1,9 / 1,12 = 190 / 112 = 95 / 56$.
    La aceleración global con ambas mejoras es **95/56**.