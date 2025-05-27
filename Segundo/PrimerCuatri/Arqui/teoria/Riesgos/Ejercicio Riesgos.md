¡Excelente! Con la información de [[Clase 13-5]], [[Mips]], [[Mips segmentado]] y [[Instrucciones MIPS]], puedo ayudarte a resolver los ejercicios del Práctico 3. Vamos paso a paso:

**1. ¿Cuáles de las instrucciones siguientes no corresponden a una arquitectura RISC? En su caso sustituya la instrucción por la instrucción o secuencia de instrucciones RISC que realicen la misma función.**

*   **ADD R3, R28, R32 ; R3 <= R28 + R32**
    *   Esta instrucción es típica de RISC. Suma el contenido de los registros R28 y R32, y guarda el resultado en R3. En MIPS, sería algo como `add $t0, $s0, $s1` (usando registros MIPS en lugar de R3, R28, R32).
*   **ST R2, 4(R27) ; M[R27+4] <= R2**
    *   Esta instrucción es un "store" (almacenamiento en memoria). Es común en RISC. Guarda el valor del registro R2 en la dirección de memoria calculada como R27 + 4. En MIPS, sería `sw $t0, 4($s0)` (guardar el valor de `$t0` en la dirección `$s0 + 4`).
*   **ADD R4, (R6), $34 ; R4 <= M[R6] + M[34]**
    *   **Esta instrucción NO es RISC.** En RISC, las operaciones aritméticas generalmente se realizan entre registros, no directamente entre ubicaciones de memoria. Esta instrucción intenta sumar el contenido de dos ubicaciones de memoria (M[R6] y M[34]) y guardar el resultado en R4.
    *   **Sustitución RISC (MIPS):**
        ```assembly
        lw $t0, ($s0)    ; Cargar el valor de M[R6] en $t0 (asumiendo R6 -> $s0)
        lw $t1, var34   ; Cargar el valor de M[34] en $t1 (asumiendo M[34] es 'var34')
        add $t2, $t0, $t1  ; Sumar $t0 y $t1, guardar el resultado en $t2
        move $s1, $t2   ; Mover el resultado de $t2 a R4 (asumiendo R4 -> $s1)
        ```
*   **LD R17, (R21) ; R17 <= M[R21]**
    *   Esta instrucción es un "load" (carga desde memoria). Es común en RISC. Carga el valor de la dirección de memoria apuntada por R21 en el registro R17. En MIPS, sería `lw $t0, ($s0)` (cargar el valor de la dirección apuntada por `$s0` en `$t0`).

**2. Proponga traducciones a MIPS para las siguientes instrucciones simples escritas en lenguaje C:**

*   **a) a = b + 777 ; con a  t2 y b  t5**
    ```assembly
    addi $t2, $t5, 777  ; Sumar 777 a $t5 (b) y guardar en $t2 (a)
    ```
*   **b) x[20] = x[21] + c ; con c  t3 y x[0]  memoria[100]**
    ```assembly
    lw $t0, 84(zero)   ; Cargar x[21] (mem[100 + 21*4]) en $t0. 21 * 4 = 84
    add $t0, $t0, $t3  ; Sumar x[21] y c, guardar en $t0
    sw $t0, 80(zero)   ; Guardar $t0 en x[20] (mem[100 + 20*4]). 20 * 4 = 80
    ```
*   **c) x[i] = x[i-1] + c ; con i  t7, c  t5 y x[0]  memoria[100]**
    ```assembly
    addi $t6, $t7, -1  ; Calcular i-1, guardar en $t6
    sll $t6, $t6, 2    ; Multiplicar (i-1) por 4 (tamaño de un entero)
    add $t6, $t6, 100  ; Calcular la dirección de x[i-1] (100 + (i-1)*4)
    lw $t0, ($t6)      ; Cargar x[i-1] en $t0
    add $t0, $t0, $t5  ; Sumar x[i-1] y c, guardar en $t0
    sll $t7, $t7, 2    ; Multiplicar i por 4
    add $t7, $t7, 100  ; Calcular la dirección de x[i] (100 + i*4)
    sw $t0, ($t7)      ; Guardar $t0 en x[i]
    ```
*   **d) - - i ; con i  t1**
    ```assembly
    addi $t1, $t1, -1  ; Decrementar i (restar 1 a $t1)
    ```

**3. Se tiene un procesador segmentado con ejecución en orden (emisión y finalización en orden). La segmentación se produce en 5 etapas: (1) captura de instrucción, (2) decodificación y lectura de operandos de registros, (3) ejecución, (4) acceso a memoria de datos, (5) escritura en registros. Dicho procesador no dispone de adelantamiento de datos. Para cierto programa, el porcentaje de uso de cada tipo de instrucción es el reflejado en la siguiente tabla:**

| Tipo instr. | ENTEROS | SALTOS | LOAD | STORE |
| :---------- | :------ | :----- | :--- | :---- |
| % uso       | 70%     | 5%     | 15%  | 10%   |

**Con dicho programa y procesador se ha medido un CPI promedio de 3. Se pretende añadir adelantamiento de datos para reducir el CPI.**

**a) El adelantamiento de datos se aplica sólo si el dato lo genera una instrucción con enteros. Suponga que hay riesgos RAW con instrucciones en la siguiente posición de memoria el 20% de las veces y con instrucciones dos posiciones de memoria después el 15% de las veces. Por simplicidad, se puede suponer que ambas circunstancias nunca suceden a la vez. Calcular el nuevo CPI.**

*   **Análisis:** Sin forwarding, cada riesgo RAW causa una detención (stall) de 2 ciclos (ya que el resultado está disponible al final de EX y se necesita al inicio de ID de la siguiente instrucción). Con forwarding solo para enteros, los riesgos RAW entre instrucciones enteras se eliminan.
*   **Cálculo:**
    *   Porcentaje de instrucciones enteras: 70%
    *   Riesgos RAW eliminados por forwarding: 70% * (20% + 15%) = 70% * 35% = 24.5% del total de instrucciones.
    *   Ciclos ahorrados por forwarding: 24.5% * 2 = 0.49 ciclos por instrucción.
    *   Nuevo CPI: 3 - 0.49 = 2.51

**b) El adelantamiento de datos se aplica sólo a los datos obtenidos con cargas (LOAD). Suponga que en todos los casos de adelantamiento de datos se tiene éxito en caché (no hay demoras en memoria de datos) y que hay riesgos RAW con instrucciones en la siguiente posición de memoria el 20% de las veces y con instrucciones dos posiciones de memoria después el 15% de las veces. Por simplicidad, se puede suponer que ambas circunstancias nunca suceden a la vez. Calcular el nuevo CPI.**

*   **Análisis:** Sin forwarding, un `lw` seguido inmediatamente por una instrucción que usa el valor cargado requiere 1 ciclo de stall (load-use hazard). Con forwarding para `lw`, este stall se elimina.
*   **Cálculo:**
    *   Porcentaje de instrucciones `lw`: 15%
    *   Riesgos RAW eliminados por forwarding: 15% * (20% + 15%) = 15% * 35% = 5.25% del total de instrucciones.
    *   Ciclos ahorrados por forwarding: 5.25% * 1 = 0.0525 ciclos por instrucción.
    *   Nuevo CPI: 3 - 0.0525 = 2.9475

**c) Aplicar ambas mejoras simultáneamente y calcular el nuevo CPI.**

*   **Cálculo:**
    *   Ciclos ahorrados por forwarding de enteros: 0.49
    *   Ciclos ahorrados por forwarding de `lw`: 0.0525
    *   Ciclos totales ahorrados: 0.49 + 0.0525 = 0.5425
    *   Nuevo CPI: 3 - 0.5425 = 2.4575

**4. Un procesador sin segmentar necesita 200 ns para ejecutar una instrucción. Sin considerar el periodo de llenado del procesador, calcular la aceleración en los siguientes casos:**

**a) Un procesador ideal con 5 estados, en el que todos los estados utilizan el mismo tiempo. Debido a la segmentación, cada estado incorpora 4 ns adicionales de retardo en el tiempo de ejecución. No existen paradas debidas a problemas de saltos o de dependencia de datos.**

*   **Tiempo de ciclo del procesador segmentado:** (200 ns / 5 estados) + 4 ns = 40 ns + 4 ns = 44 ns
*   **Aceleración:** 200 ns / 44 ns = 4.545

**b) En un procesador más real también de 5 estados. Cada estado necesita 30 ns, 30 ns, 40 ns, 50 ns y 50 ns respectivamente. Al igual que en el caso anterior la segmentación añade un retardo de 4 ns por estado.**

*   **Tiempo de ciclo del procesador segmentado:** max(30, 30, 40, 50, 50) + 4 ns = 50 ns + 4 ns = 54 ns
*   **Aceleración:** 200 ns / 54 ns = 3.704

**c) Considerando el caso b), ahora se tiene que debido a los riesgos de datos y control en el 20% de las instrucciones se produce una parada de un ciclo de reloj y en el 5% de dos ciclos.**

*   **CPI:** 1 + (0.20 * 1) + (0.05 * 2) = 1 + 0.20 + 0.10 = 1.3
*   **Tiempo promedio por instrucción segmentada:** 54 ns * 1.3 = 70.2 ns
*   **Aceleración:** 200 ns / 70.2 ns = 2.849

**5. En la tabla adjunta se muestra la estadística de uso de un conjunto de instrucciones para un determinado procesador con estructura Harvard.**

| Tipo Instrucción    | LOAD/STORE | Saltos Condicionales | Otras |
| :------------------ | :--------- | :------------------- | :---- |
| Promedio de uso     | 15%        | 25%                  | 60%   |

**El procesador está segmentado en seis etapas. 1) Captura instrucción, 2) Decodificación y detección de riesgos, 3) Captura de operandos y cálculo de la dirección efectiva en saltos. 4) Ejecución, cálculo de la dirección efectiva en accesos a memoria y en su caso cálculo de la condición. 5) Acceso a memoria y 6) Escritura de resultados en el banco de registros. Se supone que los únicos riesgos que reducen el rendimiento ideal del sistema (CPI = 1) son lo riesgos de control. Todas las instrucciones pasan por todos los segmentos. Se pide:**

**a) Sabiendo que el 80% de los saltos son efectivos, indicar el CPI real del sistema sabiendo que al detectar un riesgo, el procesador se detiene hasta que se soluciona. Utilizar el diagrama adjunto.**

*   **Análisis:** Con una segmentación de 6 etapas y detención hasta resolver el riesgo de control, cada salto efectivo causa una detención de 5 ciclos (ya que la decisión se toma en la etapa 4, y hay que vaciar las 5 etapas siguientes).
*   **Cálculo:**
    *   Porcentaje de saltos condicionales: 25%
    *   Porcentaje de saltos efectivos: 25% * 80% = 20%
    *   Ciclos perdidos por saltos efectivos: 20% * 5 = 1 ciclo por instrucción
    *   CPI real: 1 + 1 = 2

**b) Utilizando necesariamente las variables definidas por la ley de Amdahl calcular la mejora que se produce si, se diseña un sistema de predicción estática en donde siempre predice efectivo.**

*   **Ley de Amdahl:**  `Aceleración total = 1 / [(1 - Fracción mejorada) + (Fracción mejorada / Aceleración de la mejora)]`
*   **Variables:**
    *   Fracción mejorada: Fracción del tiempo de ejecución original que se puede mejorar. En este caso, el tiempo gastado en saltos efectivos.
    *   Aceleración de la mejora: Factor por el cual se reduce el tiempo de ejecución de la parte mejorada.

*   **Cálculo:**
    *   Fracción mejorada: 20% (0.20)
    *   Aceleración de la mejora: En el caso de predicción estática siempre efectivo, los saltos efectivos ya no causan detenciones. Por lo tanto, el tiempo gastado en ellos se reduce a 0, lo que implica una aceleración infinita. Sin embargo, como la predicción es siempre tomada, los saltos no tomados ahora tendrán una penalización de 1 ciclo.
    *   Porcentaje de saltos no efectivos: 25% * (100% - 80%) = 5%
    *   Ciclos perdidos por predicción incorrecta: 5% * 5 = 0.25 ciclos por instrucción
    *   CPI con predicción estática: 1 + 0.25 = 1.25
    *   Aceleración total = 2 / 1.25 = 1.6

**6. Un procesador segmentado con 5 etapas...**

**a) Identificar, señalando el tipo, todos los posibles conflictos que pueden surgir por dependencias entre operandos.**

| Instrucción | Código        | Función          | Dependencia | Tipo |
| :---------- | :------------ | :--------------- | :---------- | :--- |
| 1           | LW R1,2000(R0) | R1  M[R0+2000] |             |      |
| 2           | LW R2,2004(R0) | R2  M[R0+2004] |             |      |
| 3           | ADD R3,R2,R1  | R3  R2+R1      | 1->3, 2->3 | RAW  |
| 4           | ADDI R1,R2,8  | R1  R2+8       | 2->4,       | RAW  |
| 5           | SUBI R4,R0,2  | R4  R0-2       |             |      |
| 6           | AND R5,R3,R2  | R5  R3 and R2  | 3->6, 2->6 | RAW  |
| 7           | SW R4,2000(R0) | M[R0+2000]  R4 | 5->7        | RAW  |
| 8           | SW R5,2004(R0) | M[R0+2004]  R5 | 6->8        | RAW  |
| 9           | SW R1,2008(R0) | M[R0+2008]  R1 | 1->9, 4->9 | RAW  |

**b) Suponiendo que el procesador no tiene la posibilidad de parar el pipeline, insertar en el programa fuente el mínimo número de instrucciones NOP que se consideren necesarias para eliminar las dependencias de datos. Asumir que el procesador no dispone de mecanismos de “Forwarding” (avance de resultado en la salida de la ALU) y que no se puede cambiar el orden de la secuencia de instrucciones**

```assembly
LW R1,2000(R0)
LW R2,2004(R0)
NOP
NOP
ADD R3,R2,R1
NOP
ADDI R1,R2,8
NOP
AND R5,R3,R2
SUBI R4,R0,2
NOP
SW R4,2000(R0)
NOP
SW R5,2004(R0)
NOP
SW R1,2008(R0)
```

**c) Representar gráficamente paso a paso el estado del pipeline. Rellenar el cuadro adjunto de la misma manera a como se muestra para la primera instrucción.**

| Instrucción   | 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 |
| :------------ | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- |
| LW R1,2000(R0) | IF | ID | EX | M  | WB |    |    |    |    |    |    |    |    |    |    |    |    |    |
| LW R2,2004(R0) |    | IF | ID | EX | M  | WB |    |    |    |    |    |    |    |    |    |    |    |    |
| NOP           |    |    | IF | ID | EX | M  | WB |    |    |    |    |    |    |    |    |    |    |    |
| NOP           |    |    |    | IF | ID | EX | M  | WB |    |    |    |    |    |    |    |    |    |    |
| ADD R3,R2,R1  |    |    |    |    | IF | ID | EX | M  | WB |    |    |    |    |    |    |    |    |    |
| NOP           |    |    |    |    |    | IF | ID | EX | M  | WB |    |    |    |    |    |    |    |    |
| ADDI R1,R2,8  |    |    |    |    |    |    | IF | ID | EX | M  | WB |    |    |    |    |    |    |    |
| NOP           |    |    |    |    |    |    |    | IF | ID | EX | M  | WB |    |    |    |    |    |    |
| AND R5,R3,R2  |    |    |    |    |    |    |    |    | IF | ID | EX | M  | WB |    |    |    |    |    |
| SUBI R4,R0,2  |    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | WB |    |    |    |    |
| NOP           |    |    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | WB |    |    |    |
| SW R4,2000(R0) |    |    |    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | WB |    |    |
| NOP           |    |    |    |    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | WB |    |
| SW R5,2004(R0) |    |    |    |    |    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | WB |
| NOP           |    |    |    |    |    |    |    |    |    |    |    |    |    |    | IF | ID | EX | M  |
| SW R1,2008(R0) |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    | IF | ID | EX |

**d) ¿Cuál es la mejora producida por utilizar segmentación?**

*   Sin segmentación, el CPI sería 5 (cada instrucción tarda 5 ciclos). Con segmentación y los NOPs insertados, el número de ciclos para ejecutar las 9 instrucciones es 18.
*   Si cada instrucción tarda 5 ciclos, 9 instrucciones tardarían 45 ciclos.
*   La mejora es 45/18 = 2.5

**7. Se tiene un microprocesador segmentado en las siguientes 5 etapas...**

**a) Suponiendo que no hay adelantamiento de datos (forwarding) y que los saltos condicionales se predicen como no efectivos, rellenar el siguiente cronograma.**

| Instrucciones   | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 |
| :------------ | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- |
| ADD R1, R2, R3  | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| LOAD R4, 0(R1)  |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| MUL R5, R4, R4  |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| BNE R1, R4, L1  |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| SUB R5, R5, R2  |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| ADD R7, R4, R5  |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| L1: ADD R6, R1, R5 |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |
| OR R1, R7, R8   |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |
| ST R6, 0(R1)    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |

**Con los stalls:**

| Instrucciones   | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 |
| :------------ | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- |
| ADD R1, R2, R3  | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| LOAD R4, 0(R1)  |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| MUL R5, R4, R4  |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| BNE R1, R4, L1  |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| SUB R5, R5, R2  |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| ADD R7, R4, R5  |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| L1: ADD R6, R1, R5 |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |
| OR R1, R7, R8   |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |
| ST R6, 0(R1)    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |

**Con los stalls:**

| Instrucciones   | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 |
| :------------ | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- |
| ADD R1, R2, R3  | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| LOAD R4, 0(R1)  |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| MUL R5, R4, R4  |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| BNE R1, R4, L1  |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| SUB R5, R5, R2  |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| ADD R7, R4, R5  |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| L1: ADD R6, R1, R5 |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |
| OR R1, R7, R8   |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |
| ST R6, 0(R1)    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |

**Con los stalls:**

| Instrucciones   | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 |
| :------------ | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- | :- |
| ADD R1, R2, R3  | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| LOAD R4, 0(R1)  |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| MUL R5, R4, R4  |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| BNE R1, R4, L1  |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| SUB R5, R5, R2  |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| ADD R7, R4, R5  |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| L1: ADD R6, R1, R5 |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |    |
| OR R1, R7, R8   |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |    |
| ST R6, 0(R1)    |    |    |    |    |    |    |    |    | IF | ID | EX | M  | W  |    |    |    |    |    |    |    |    |    |    |    |

**Con los stalls:**

| Instrucciones   | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 