
**Resumen del Entorno Proporcionado:**

*   **Procesador (`Processor.vhd`):** Implementa un MIPS uniciclo con datapath y control para instrucciones R-type (add, sub, and, or, slt), lw, sw, beq, j. Usa interfaces separadas para memoria de instrucciones y datos (Harvard).
*   **Memorias (`Memory.vhd`):** Modelo genérico de memoria RAM, inicializable desde archivo hexadecimal, con flanco de reloj configurable. Se instancian dos: `Instruction_Mem` (flanco descendente por defecto, carga `program1`) y `Data_Mem` (flanco ascendente por defecto, carga `data`).
*   **ALU (`NOMBRE.vhd` renombrada a `ALU.vhd`):** Realiza las operaciones aritmético-lógicas necesarias.
*   **Banco de Registros (`registers.vhd`):** Almacena 32 registros de 32 bits, con 2 lecturas combinacionales y 1 escritura síncrona (flanco descendente). Registro 0 es fijo a cero. Reset asíncrono.
*   **Testbench (`ProcessorTB.vhd`):** Instancia el `Processor` y las dos `Memory`, genera reloj y reset, y conecta todo.
*   **Archivos de Memoria:** `program1`, `program2` (instrucciones MIPS en hexadecimal), `data` (datos iniciales en hexadecimal).

---

**Abordando los Ejercicios:**

**a. Complete la descripción del procesador MIPS [...] mediante las incorporaciones del banco de registros y la ALU.**

*   **Tarea:** Asegurarte de que los archivos `ALU.vhd` y `registers.vhd` estén correctamente integrados en el diseño principal `Processor.vhd`.
*   **Acciones:**
    1.  **Renombrar ALU:** La entidad de tu ALU se llama `NOMBRE`. Debes:
        *   **Opción 1 (Recomendada):** Cambiar `entity NOMBRE is` a `entity ALU is` en el archivo de la ALU.
        *   **Opción 2:** Cambiar la declaración del componente y la instanciación en `Processor.vhd` de `ALU` a `NOMBRE`. **¡Deben coincidir!**
    2.  **Corregir Reset en Registros:** En `registers.vhd`, el puerto se llama `reset` pero el proceso usa `rst`. Cambia `process(clk, rst)` a `process(clk, reset)` y `if rst = '1' then` a `if reset = '1' then`.
    3.  **Verificar Conexiones:** Revisa las instanciaciones `E_ALU` y `E_Regs` dentro de `Processor.vhd` para asegurarte de que los puertos estén conectados a las señales correctas del datapath. (Parece estar bien según el código que proporcionaste).
    4.  **Incluir Archivos:** Asegúrate de que los archivos `ALU.vhd` (con el nombre corregido) y `registers.vhd` (con el reset corregido) estén presentes junto con `Processor.vhd`, `Memory.vhd` y `ProcessorTB.vhd` en tu proyecto de EDA Playground.

**b. Analice y simule el procesador con los contenidos de memorias de programa (program1 y program2) y datos (data).**

*   **Tarea:** Ejecutar la simulación y observar el comportamiento del procesador con los programas dados.
*   **Acciones:**
    1.  **Configurar EDA Playground:**
        *   Carga/Pega todos los archivos VHDL (`ProcessorTB.vhd`, `Processor.vhd`, `Memory.vhd`, `ALU.vhd`, `registers.vhd`).
        *   Añade los archivos `program1` y `data` (asegúrate de que los nombres coincidan *exactamente* con `C_ELF_FILENAME` en `ProcessorTB.vhd`). Puedes pegarlos en pestañas separadas o usar la opción de subir archivos si está disponible.
        *   Selecciona `ProcessorTB` como la entidad "Top".
        *   Elige un simulador (e.g., Aldec Riviera-PRO o GHDL).
        *   Marca la opción "Open EPWave after run".
    2.  **Simular con `program1`:** Ejecuta la simulación. Observa las formas de onda (EPWave). Presta atención a:
        *   `clk`, `reset`
        *   `reg_pc`: Cómo avanza.
        *   `I_DataIn`: Qué instrucción se está buscando.
        *   Señales de control (`RegWrite`, `MemRead`, `MemWrite`, `Branch`, `Jump`, `ALUSrc`, etc.): ¿Se activan correctamente según la instrucción?
        *   `ALU_result`, `ALU_zero`: Resultados de la ALU.
        *   `data1_reg`, `data2_reg`: Valores leídos de registros.
        *   `D_Addr`, `D_DataOut`, `D_DataIn`: Interacción con la memoria de datos.
        *   `reg_wr`, `data_w_reg`: Qué se escribe en el banco de registros y cuándo (`RegWrite='1'`).
        *   Sigue la ejecución de `program1` instrucción por instrucción.
    3.  **Simular con `program2`:**
        *   Modifica `ProcessorTB.vhd`: Cambia `C_ELF_FILENAME => "program1"` a `C_ELF_FILENAME => "program2"` en la instancia `Instruction_Mem`.
        *   Asegúrate de que el archivo `program2` esté disponible en EDA Playground.
        *   Vuelve a ejecutar la simulación y analiza las formas de onda como hiciste para `program1`.

**c. Analice la latencia involucrada en la ejecución de los dos programas.**

*   **Tarea:** Determinar cuánto tiempo tarda en ejecutarse cada programa.
*   **Análisis:**
    *   En un procesador **uniciclo**, cada instrucción toma exactamente **un ciclo de reloj** para completarse.
    *   La latencia total es: `Número de instrucciones ejecutadas * Período del reloj`.
    *   El período del reloj (`tper_clk`) está definido en `ProcessorTB.vhd` como `50 ns`.
    *   Necesitas determinar cuántas instrucciones ejecuta cada programa antes de detenerse o entrar en un bucle final. Observa la secuencia de `reg_pc` en la simulación.
        *   Para `program1`: Cuenta las instrucciones desde la dirección 0 hasta que el programa salte a una dirección que indique el final o un bucle (la última instrucción `0800001c` es un `j 0x00000070`, necesitas ver si hay código allí o qué pasa).
        *   Para `program2`: Haz lo mismo. La última instrucción `08000007` es un `j 0x0000001c`.
    *   **Cálculo:** Latencia = (Número de instrucciones contadas) * 50 ns.

**d. Analice el funcionamiento de las memorias de programas y datos:**

*   **Tarea:** Entender cómo y cuándo interactúan las memorias con el resto del procesador, especialmente en relación con los flancos de reloj.
*   **Análisis:**
    *   **Flancos por Defecto:**
        *   PC (`E_PC` en `Processor`): Actualiza en `rising_edge(clk)`.
        *   Banco de Registros (`registers`): Escribe en `falling_edge(clk)`.
        *   Memoria de Instrucciones (`Instruction_Mem`): Lee/Escribe (aunque solo lee) síncronamente en `falling_edge(clk)` (porque `C_FUNC_CLK = '0'`).
        *   Memoria de Datos (`Data_Mem`): Lee/Escribe síncronamente en `rising_edge(clk)` (porque `C_FUNC_CLK = '1'`).
    *   **Implicaciones:** Hay una mezcla de flancos. La instrucción se busca (Mem Instr) y el resultado se escribe en registros en el flanco descendente, mientras que el PC se actualiza y la memoria de datos se accede en el flanco ascendente. Esto *puede* funcionar en simulación si los retrasos son ideales, pero es inusual para un ciclo único y podría ser problemático. En un ciclo único real, todo suele ocurrir referenciado a un único flanco.
    *   **Experimento con `C_FUNC_CLK`:**
        1.  **Cambia `Instruction_Mem` a Flanco Ascendente:** En `ProcessorTB.vhd`, cambia `C_FUNC_CLK => '0'` a `C_FUNC_CLK => '1'` para `Instruction_Mem`. Vuelve a simular (con `program1` o `program2`). Observa si el comportamiento cambia. ¿La instrucción se busca "demasiado tarde" o "demasiado pronto" en relación con la actualización del PC o el ciclo de control? ¿Sigue funcionando?
        2.  **Cambia `Data_Mem` a Flanco Descendente:** Restaura `Instruction_Mem` a `'0'`. Cambia `C_FUNC_CLK => '1'` a `C_FUNC_CLK => '0'` para `Data_Mem`. Vuelve a simular. Observa si el acceso a datos (lectura para `lw`, escritura para `sw`) sigue funcionando correctamente en relación con el cálculo de la dirección en la ALU y la escritura en registros.
        *   **Análisis del Experimento:** Documenta si los cambios en los flancos alteran el resultado final o el comportamiento ciclo a ciclo del procesador. Explica *por qué* crees que funciona o deja de funcionar (relación temporal entre búsqueda, decodificación, ejecución, memoria, escritura).

**e. Implemente el programa que realice lo siguiente: R2 = ∑ 𝑖 (desde i=1 hasta Mem[4]).**

*   **Tarea:** Escribir un programa MIPS en ensamblador, convertirlo a hexadecimal y simularlo.
*   **Pasos:**
    1.  **Algoritmo:**
        *   Necesitas una variable para la suma (inicializada a 0), un contador `i` (inicializado a 1) y el límite `N` (leído de `Mem[4]`).
        *   Bucle:
            *   Añadir `i` a la suma.
            *   Incrementar `i`.
            *   Comparar `i` con `N`.
            *   Si `i <= N`, volver al inicio del bucle.
        *   Al final, mover el resultado de la suma al registro $v0 (que es R2).
    2.  **Escribir en Ensamblador MIPS (usando MARS como ayuda):**
        ```mips
        .data
            # No necesitamos .data si precargamos Mem[4]

        .text
        .globl main
        main:
            # Registro $v0 = R2 (resultado final)
            # Registro $t0 = suma
            # Registro $t1 = contador i
            # Registro $t2 = N (límite)

            add $t0, $zero, $zero  # suma = 0
            addi $t1, $zero, 1     # i = 1

            # Cargar N desde Mem[4] en $t2
            # El procesador soporta lw rt, imm(rs)
            # lw $t2, 4($zero)  # N = Mem[4]
            # Hex: 100011_00000_01010_0000000000000100 => 8C0A0004 (¡Ojo! Tu procesador usa rs=I(25:21), rt=I(20:16))
            # Entonces lw $t2, 4($zero) es: Op=100011, rs($zero)=00000, rt($t2=10)=01010, imm=4
            # Instrucción: 100011 00000 01010 0000000000000100 => 8C0A0004

        loop:
            # Comparar i con N. Salir si i > N
            # slt $t3, $t2, $t1  # $t3 = 1 si N < i (i > N)
            # Instrucción R-type: op=000000, rs=$t2(10), rt=$t1(9), rd=$t3(11), shamt=0, funct=101010
            # 000000 01010 01001 01011 00000 101010 => 0149582A

            # bne $t3, $zero, endloop # Si $t3 != 0 (i > N), salta a endloop
            # ¡Tu procesador NO tiene bne, solo beq! Hay que reestructurar.

            # Alternativa: Bucle mientras i <= N
            # slt $t3, $t1, $t2  # $t3 = 1 si i < N
            # beq $t1, $t2, body # Si i == N, ejecuta el cuerpo una última vez
            # beq $t3, $zero, endloop # Si !(i < N) y !(i == N), entonces i > N, salir.

            # Otra alternativa: Contar hacia atrás desde N hasta 1.
            lw $t1, 4($zero)      # $t1 = N (contador i)
            add $t0, $zero, $zero # $t0 = suma = 0

        countdown_loop:
            # Salir si i == 0
            # beq $t1, $zero, end_countdown
            # Instrucción: op=000100, rs=$t1(9), rt=$zero(0), offset=(end_countdown - PC_actual - 4)/4
            # Asumamos que end_countdown está 3 instrucciones adelante (add, sub, j). Offset = (3*4)/4 = 3
            # 000100 01001 00000 0000000000000011 => 11200003

            # Añadir i a la suma
            # add $t0, $t0, $t1
            # Instrucción: op=000000, rs=$t0(8), rt=$t1(9), rd=$t0(8), shamt=0, funct=100000
            # 000000 01000 01001 01000 00000 100000 => 01094020

            # Decrementar i (i = i - 1)
            # Necesitamos el valor 1. Asumamos que lo cargamos en $t3 previamente.
            # O usamos addi si estuviera disponible. Como no está, necesitamos sub.
            # Necesitamos cargar 1 en un registro, digamos $t3.
            # lw $t3, 8($zero) # Asumiendo Mem[8] = 1
            # Hex: 100011 00000 01011 0000000000001000 => 8C0B0008
            # sub $t1, $t1, $t3
            # Instrucción: op=000000, rs=$t1(9), rt=$t3(11), rd=$t1(9), shamt=0, funct=100010
            # 000000 01001 01011 01001 00000 100010 => 012B4822

            # Saltar de nuevo al bucle
            # j countdown_loop
            # Instrucción: op=000010, target=(address of countdown_loop / 4)
            # Si countdown_loop está en la instrucción 2 (dirección 8), target = 8/4 = 2
            # 000010 00000000000000000000000010 => 08000002

        end_countdown:
            # Mover resultado (suma en $t0) a $v0 (R2)
            # add $v0, $t0, $zero
            # Instrucción: op=000000, rs=$t0(8), rt=$zero(0), rd=$v0(2), shamt=0, funct=100000
            # 000000 01000 00000 00010 00000 100000 => 01001020

            # Bucle infinito para detener
        halt:
            # j halt
            # Si halt está en la instrucción 6 (dirección 0x18), target = 0x18 / 4 = 6
            # 000010 00000000000000000000000110 => 08000006

        ```
    3.  **Obtener Código Máquina (Hex):** Ensambla el código anterior usando MARS (o una herramienta similar) y copia los valores hexadecimales de la columna "Code".
        ```hex
        # Código ejemplo (direcciones/offsets pueden variar un poco según el ensamblador)
        8C0A0004  # lw $t1, 4($zero)    ; Carga N en $t1
        00004020  # add $t0, $zero, $zero ; suma = 0
        8C0B0008  # lw $t3, 8($zero)    ; Carga 1 en $t3 (Necesita Mem[8]=1)
        11200003  # beq $t1, $zero, end_countdown (+3 instrucciones)
        01094020  # add $t0, $t0, $t1   ; suma = suma + i
        012B4822  # sub $t1, $t1, $t3   ; i = i - 1
        08000003  # j countdown_loop (Salta a la instrucción beq)
        01001020  # end_countdown: add $v0, $t0, $zero ; Mueve suma a $v0
        08000007  # halt: j halt (Salta a sí mismo)
        ```
    4.  **Preparar Archivos:**
        *   Crea un archivo (p. ej., `sum_program.hex`) y pega el código hexadecimal generado.
        *   Modifica tu archivo `data` para que contenga el valor de `N` en la dirección 4 y el valor `1` en la dirección 8. Por ejemplo, para N=5:
            ```
            00000000  # Addr 0
            00000005  # Addr 4 (N=5)
            00000001  # Addr 8 (Constante 1)
            ...       # Resto de datos si los hubiera
            ```
    5.  **Simular:**
        *   En `ProcessorTB.vhd`, cambia `C_ELF_FILENAME` de `Instruction_Mem` a `"sum_program.hex"` (o como lo hayas llamado).
        *   Asegúrate de que el archivo `data` modificado esté cargado.
        *   Ejecuta la simulación.
    6.  **Verificar:** Observa las formas de onda. Deja que la simulación corra hasta que entre en el bucle `halt`. Verifica el valor que se escribe en el registro $v0 (R2). Busca el momento en que `RegWrite='1'` y `reg_wr="00010"`. El valor en `data_w_reg` en ese momento debe ser la suma calculada (para N=5, la suma 1+2+3+4+5 = 15, que es `0x0000000F`).

¡Mucha suerte con el práctico! Si te atascas en algún punto específico de la simulación o el código, no dudes en preguntar.

Ejercicio1
![[Pasted image 20250428105143.png]]![[Pasted image 20250428112023.png]]
Ejercicio2 
![[Pasted image 20250428105601.png]]![[Pasted image 20250428112108.png]]Okay, analicemos eso.

**Significado de `D_RdStb` y `D_WrStb`:**

*   **`D_RdStb` (Data Read Strobe):** Es una señal de control que el **procesador (`Processor`)** activa (pone en '1') para indicarle a la **memoria de datos (`Data_Mem`)** que quiere **leer** un dato de ella en el ciclo de reloj actual. En tu procesador MIPS, esta señal se activa (`MemRead <= '1'`) únicamente durante la ejecución de una instrucción `lw` (Load Word).
*   **`D_WrStb` (Data Write Strobe):** Es una señal de control que el **procesador (`Processor`)** activa (pone en '1') para indicarle a la **memoria de datos (`Data_Mem`)** que quiere **escribir** un dato en ella en el ciclo de reloj actual. En tu procesador MIPS, esta señal se activa (`MemWrite <= '1'`) únicamente durante la ejecución de una instrucción `sw` (Store Word).

**Interpretación de tu Observación:**

Si la *única* diferencia que ves en las formas de onda (EPWave) entre la ejecución de `program1` y `program2` está en cuándo o si se activan `D_RdStb` y `D_WrStb`, esto significa:

1.  **Diferente Acceso a Memoria de Datos:** Los dos programas realizan accesos diferentes a la memoria de datos. Uno de ellos ejecuta instrucciones `lw` y/o `sw` en momentos distintos o en cantidades distintas que el otro.
2.  **Misma Ruta General (Probablemente):** Si otras señales clave como `reg_pc` (la secuencia de direcciones de instrucción), las señales de control principales (excepto `MemRead`/`MemWrite`), y los resultados de la ALU son mayormente iguales o siguen patrones muy similares (aparte de los ciclos donde ocurren los `lw`/`sw`), sugiere que la estructura general de los programas o las rutas de ejecución principales (saltos, bucles) podrían ser similares, pero difieren específicamente en cómo interactúan con la memoria de datos.

**Relación con la Latencia en un Diseño Uniciclo:**

Aquí es donde el tipo de diseño de tu procesador es **crucial**:

*   **Diseño Uniciclo:** Tu `Processor.vhd` implementa un procesador **uniciclo**. Esto significa, por definición, que **cada instrucción tarda exactamente un ciclo de reloj en completarse**, sin importar qué instrucción sea (`add`, `lw`, `sw`, `beq`, etc.).
*   **Ciclo de Reloj Fijo:** El período del reloj (`tper_clk`) es constante (50 ns en tu `ProcessorTB.vhd`). Este período debe ser lo suficientemente largo para permitir que la instrucción *más lenta* (generalmente `lw`, que pasa por todas las etapas: Fetch, Decode, Execute (cálculo de dirección), Memory Read, Write Back) se complete dentro de ese único ciclo.
*   **Impacto Nulo en la Latencia (por tipo de instrucción):** En un diseño uniciclo, el hecho de que una instrucción sea `lw` (activando `D_RdStb`) o `sw` (activando `D_WrStb`) **no cambia la duración de ese ciclo de reloj**. Sigue siendo 50 ns. Por lo tanto, la presencia o ausencia de estas señales **no afecta directamente la latencia *por instrucción***.
*   **Latencia Total:** La latencia total de un programa en un diseño uniciclo depende *únicamente* del **número total de instrucciones ejecutadas**. Si `program1` ejecuta 20 instrucciones y `program2` ejecuta 25 instrucciones, entonces:
    *   Latencia `program1` = 20 ciclos * 50 ns/ciclo = 1000 ns
    *   Latencia `program2` = 25 ciclos * 50 ns/ciclo = 1250 ns

**En Conclusión:**

El hecho de que `D_RdStb` y `D_WrStb` sean diferentes entre `program1` y `program2` te dice que los programas interactúan de manera distinta con la memoria de datos (usan `lw` y `sw` de forma diferente). Sin embargo, en tu **arquitectura uniciclo**, esto **no influye en la latencia de forma directa**. La latencia total solo cambiará si un programa ejecuta un número total de instrucciones diferente al otro (por ejemplo, si uno toma un salto condicional que el otro no, resultando en una ruta de ejecución más larga o más corta). Las señales `D_RdStb` y `D_WrStb` simplemente muestran *qué* está haciendo el procesador durante ciertos ciclos de 50 ns, no cambian la duración de esos ciclos.

Okay, analicemos los programas `program1` y `program2` para estimar la diferencia de latencia basándonos únicamente en el código hexadecimal y el conocimiento de que es un procesador MIPS uniciclo.

**Recordatorio Clave:**

*   **Procesador Uniciclo:** Cada instrucción, sin importar cuál sea, toma exactamente **1 ciclo de reloj** para ejecutarse.
*   **Latencia Total:** (Número total de instrucciones ejecutadas) * (Período del reloj).
*   **Diferencia de Latencia:** Dependerá exclusivamente de la **diferencia en el número total de instrucciones ejecutadas** por cada programa.

**Análisis de `program1`:**

```hex
8c090000 ; lw
8c0a0004 ; lw
8c0b0008 ; lw
8c0c000c ; lw
8c0d0010 ; lw
8c0e0014 ; lw
ac090018 ; sw
ac0a001c ; sw
ac0b0020 ; sw
ac0c0024 ; sw
ac0d0028 ; sw
ac0e002c ; sw
8c090018 ; lw
8c0a001c ; lw
8c0b0020 ; lw
8c0c0024 ; lw
8c0d0028 ; lw
8c0e002c ; lw
012a7820 ; add
016c8020 ; add
01a98822 ; sub
01ca9022 ; sub
012a9824 ; and
01eaa024 ; and
012aa825 ; or
020ab025 ; or
012ab82a ; slt
020ac02a ; slt
0800001c ; j 0x70
```

*   **Flujo de Ejecución:** Este programa parece ser completamente secuencial. No hay instrucciones `beq` (saltos condicionales). La única instrucción de salto es la última (`j 0x70`).
*   **Número de Instrucciones:** Contando las líneas, hay **29** instrucciones. El programa las ejecutará todas en orden y luego saltará a la dirección `0x70`.
*   **Instrucciones Ejecutadas (Estimado):** 29.

**Análisis de `program2`:**

```hex
8c090000 ; lw $t1, 0($zero)
8c0a0014 ; lw $t2, 20($zero)     ; Carga Mem[20] en $t2
00005820 ; add $t3, $zero, $zero ; $t3 = 0
116a0002 ; beq $t3, $t2, +2      ; Salta si $t3 == $t2 (0 == Mem[20]?)
01695820 ; add $t3, $t3, $t1     ; (Si no salta)
08000003 ; j 0xC                 ; (Si no salta) Salta a la instrucción beq (bucle?) - Error en mi análisis anterior, esto salta a la dirección 0xC (la beq misma).
ac0b0018 ; sw $t3, 24($zero)     ; (Destino del beq)
08000007 ; j 0x1C                 ; Salta a sí mismo (bucle infinito) - Destino del j 0xC si se toma esa ruta.
```

*   **Flujo de Ejecución:** Este programa *no* es secuencial. Contiene una instrucción `beq` y saltos `j`. El flujo depende del resultado de la comparación en `beq`.
*   **Dependencia de Datos:** La instrucción `beq $t3, $t2, +2` compara `$t3` (que es 0) con `$t2`. El valor de `$t2` se carga desde la dirección de memoria `20` (`0x14`) usando `lw $t2, 20($zero)`. Necesitamos ver el archivo `data`:
    ```
    00000001 ; Addr 0
    ...
    00000000 ; Addr 1C (decimal 28)
    00000000 ; Addr 20 (decimal 32) <- ¡Este es Mem[20]!
    ```
    El valor en `Mem[20]` es `0x00000000`.
*   **Resultado del `beq`:** Como `$t3` es 0 y `$t2` (cargado de `Mem[20]`) también es 0, la condición `$t3 == $t2` es **verdadera**. Por lo tanto, el salto `beq` **se tomará**.
*   **Ruta de Ejecución Real:**
    1.  `lw $t1, 0($zero)` (Addr 0)
    2.  `lw $t2, 20($zero)` (Addr 4)
    3.  `add $t3, $zero, $zero` (Addr 8)
    4.  `beq $t3, $t2, +2` (Addr C) -> Salto tomado. PC se calcula como `PC_actual + 4 + offset*4` = `0xC + 4 + 2*4` = `0xC + 4 + 8` = `0x18`.
    5.  `sw $t3, 24($zero)` (Addr 18) -> Se ejecuta la instrucción en el destino del salto.
    6.  `j 0x1C` (Addr 1C) -> Salta a la dirección `0x1C` (esta misma instrucción).
    7.  `j 0x1C` (Addr 1C) -> Bucle infinito.
*   **Instrucciones Ejecutadas (Estimado):** El programa ejecuta 6 instrucciones (en las direcciones 0, 4, 8, C, 18, 1C) antes de entrar en un bucle infinito en la última instrucción.

**Estimación de la Diferencia de Latencia:**

*   `program1` ejecuta 29 instrucciones.
*   `program2` ejecuta 6 instrucciones (antes de quedar atrapado en un bucle).
*   **Diferencia en número de instrucciones:** 29 - 6 = 23 instrucciones.
*   **Diferencia de Latencia Esperada:** 23 ciclos * (Período del reloj / ciclo). Si el período es 50 ns, la diferencia esperada es 23 * 50 ns = **1150 ns**.

**Conclusión:**

Basándonos únicamente en el análisis del código y el archivo de datos inicial, se espera que `program1` ejecute 23 instrucciones más que `program2` antes de que `program2` entre en su bucle final. Por lo tanto, se espera que la **latencia de `program1` sea significativamente mayor** que la de `program2` (aproximadamente 1150 ns más larga, asumiendo un reloj de 50 ns).



PARA EL EP WABE 
¡Excelente pregunta! Verás el reflejo de la diferencia de latencia directamente en el **tiempo de ejecución** visible en las formas de onda (EPWave).

Aquí te explico cómo observarlo:

1.  **Añade Señales Clave a EPWave:** Asegúrate de tener visibles al menos las siguientes señales:
    *   `clk`: Para ver los ciclos de reloj.
    *   `reset`: Para saber cuándo empieza la ejecución normal.
    *   `reg_pc`: ¡Esta es la más importante para esto! Muestra la dirección de la instrucción que se está buscando en cada ciclo.
    *   (Opcional pero útil: `I_DataIn` para ver la instrucción misma).

2.  **Identifica el Inicio de Ejecución:** Busca el momento en que la señal `reset` pasa de '1' a '0'. Este es el punto (tiempo `t_start`) donde el procesador comienza a ejecutar el programa cargado (a partir de la dirección 0, ya que `reg_pc` se resetea a 0).

3.  **Observa `reg_pc` para `program1`:**
    *   Verás que `reg_pc` empieza en 0 y se incrementa en 4 en casi cada ciclo de reloj (`0`, `4`, `8`, `C`, `10`, ...).
    *   Sigue la secuencia de `reg_pc` hasta que llegue a la dirección de la última instrucción del programa principal, que es `0x6C` (la `slt`), y luego a la dirección del salto final `j 0x70`, que es `0x70`.
    *   **Mide el Tiempo:** Usa los cursores de EPWave. Coloca un cursor en `t_start` (cuando `reset` baja) y el otro cursor en el flanco de reloj donde `reg_pc` se actualiza por primera vez al valor `0x00000070`. Anota la diferencia de tiempo (Δt1). Este Δt1 representa la latencia de ejecución de `program1`.

4.  **Observa `reg_pc` para `program2`:**
    *   Ejecuta la simulación con `program2`.
    *   Verás que `reg_pc` empieza en 0, va a 4, 8, C.
    *   En el ciclo donde `reg_pc` es `0xC`, la instrucción `beq` se evalúa. Como predijimos que el salto se toma, en el *siguiente* ciclo de reloj, `reg_pc` debería saltar a `0x18`.
    *   Después del ciclo donde `reg_pc` es `0x18`, la instrucción `j 0x1C` se ejecuta, y en el siguiente ciclo, `reg_pc` se actualizará a `0x1C`.
    *   A partir de ahí, `reg_pc` se quedará en `0x1C` (o saltará repetidamente a `0x1C`) porque entra en el bucle infinito `j 0x1C`.
    *   **Mide el Tiempo:** Usa los cursores. Coloca un cursor en `t_start` (cuando `reset` baja) y el otro cursor en el flanco de reloj donde `reg_pc` se actualiza por primera vez al valor `0x0000001C` (el inicio del bucle final). Anota la diferencia de tiempo (Δt2). Este Δt2 representa la latencia de ejecución de `program2` hasta que entra en su estado final (el bucle).

5.  **Compara los Tiempos:**
    *   Compara Δt1 (tiempo de `program1`) con Δt2 (tiempo de `program2`).
    *   **Deberías observar que Δt1 es significativamente mayor que Δt2.**
    *   **Cuantitativamente:** Como `program1` ejecuta 29 instrucciones y `program2` ejecuta 6 antes del bucle, y cada ciclo dura 50 ns:
        *   Δt1 ≈ 29 ciclos * 50 ns/ciclo = 1450 ns
        *   Δt2 ≈ 6 ciclos * 50 ns/ciclo = 300 ns
        *   La diferencia Δt1 - Δt2 ≈ 1150 ns.
    *   Busca esta diferencia de aproximadamente 1150 ns entre los tiempos medidos en EPWave.

En resumen: La diferencia de latencia se manifiesta como una **diferencia en el tiempo transcurrido en el eje horizontal de EPWave** desde el inicio de la ejecución (`reset` = '0') hasta que cada programa alcanza su punto final o estado estable (el `j 0x70` para `program1`, el bucle `j 0x1C` para `program2`), lo cual puedes rastrear observando la señal `reg_pc`.








¡Claro! Calculemos la diferencia de latencia entre los dos programas que has proporcionado, basándonos en el número de instrucciones ejecutadas y el período de reloj de 50 ns (según [[Facultad/Segundo/PrimerCuatri/Arqui/Eda/tp2/ejercicio1/Ejercicios.md]]).

**Análisis de `program1` (el segundo programa que proporcionaste):**

```mips
main:
  lw $t1, 0($zero)       # 1
  lw $t2, 4($zero)       # 2
  lw $t3, 8($zero)       # 3
  lw $t4, 12($zero)      # 4
  lw $t5, 16($zero)      # 5
  lw $t6, 20($zero)      # 6
  sw $t1, 24($zero)      # 7
  sw $t2, 28($zero)      # 8
  sw $t3, 32($zero)      # 9
  sw $t4, 36($zero)      # 10
  sw $t5, 40($zero)      # 11
  sw $t6, 44($zero)      # 12
  lw $t1, 24($zero)      # 13
  lw $t2, 28($zero)      # 14
  lw $t3, 32($zero)      # 15
  lw $t4, 36($zero)      # 16
  lw $t5, 40($zero)      # 17
  lw $t6, 44($zero)      # 18
  add $t7, $t1, $t2      # 19
  add $s0, $t3, $t4      # 20
  sub $s1, $t5, $t1      # 21
  sub $s2, $t6, $t2      # 22
  and $s3, $t1, $t2      # 23
  and $s4, $t7, $t2      # 24
  or $s5, $t1, $t2       # 25
  or $s6, $s0, $t2       # 26
  slt $s7, $t1, $t2      # 27
  slt $t8, $s0, $t2      # 28
end_program:
  j end_program          # 29 (Entra en bucle infinito aquí)
```

*   **Número de Instrucciones Ejecutadas (`program1`):** Este programa es completamente secuencial hasta el salto final. Ejecuta **29** instrucciones antes de entrar en el bucle `j end_program`.
*   **Latencia (`program1`):** 29 instrucciones * 50 ns/instrucción = **1450 ns**.

**Análisis de `program2` (el primer programa que proporcionaste, con `Mem[20]=32`):**

*   Como calculamos en la respuesta anterior, este programa ejecuta **101** instrucciones antes de entrar en su bucle infinito final (`j end_program`).
*   **Latencia (`program2`):** 101 instrucciones * 50 ns/instrucción = **5050 ns**.
* ¡Perfecto! Con el código ensamblador y la sección `.data` que proporcionaste, ahora el comportamiento tiene todo el sentido. Mi análisis anterior se basaba en una suposición diferente sobre el contenido de `data`.

Analicemos `program2` con tus datos:

**Datos Iniciales:**

*   `Mem[0]` (`num0`) = 1
*   `Mem[4]` (`num1`) = 2
*   ...
*   `Mem[20]` (`num5`) = **32**
*   `Mem[24]` (`num6`) = 0

**Código Ensamblador:**

```mips
main:
  lw $t1, 0($zero)       # $t1 = Mem[0] = 1
  lw $t2, 20($zero)      # $t2 = Mem[20] = 32
  add $t3, $zero, $zero  # $t3 = 0
init_loop:
  beq $t3,$t2,end_loop   # Salta a end_loop si $t3 == $t2
  add $t3,$t3,$t1        # Si no salta: $t3 = $t3 + $t1 (incrementa $t3 en 1)
  j init_loop            # Vuelve al beq
end_loop:
  sw $t3, 24($zero)      # Almacena el valor final de $t3 en Mem[24]
end_program:
  j end_program          # Bucle infinito final
```

**Flujo de Ejecución Detallado:**

1.  **Setup (3 instrucciones):**
    *   `lw $t1, 0($zero)` -> `$t1` se carga con 1.
    *   `lw $t2, 20($zero)` -> `$t2` se carga con 32.
    *   `add $t3, $zero, $zero` -> `$t3` se inicializa a 0.

2.  **Bucle `init_loop`:**
    *   **Iteración 1:**
        *   `beq $t3,$t2,end_loop` -> Compara `$t3`(0) con `$t2`(32). No son iguales. **No salta.** (1 instrucción)
        *   `add $t3,$t3,$t1` -> `$t3` = 0 + 1 = 1. (1 instrucción)
        *   `j init_loop` -> Salta a `init_loop`. (1 instrucción)
    *   **Iteración 2:**
        *   `beq $t3,$t2,end_loop` -> Compara `$t3`(1) con `$t2`(32). No son iguales. **No salta.** (1 instrucción)
        *   `add $t3,$t3,$t1` -> `$t3` = 1 + 1 = 2. (1 instrucción)
        *   `j init_loop` -> Salta a `init_loop`. (1 instrucción)
    *   ... (Este patrón de 3 instrucciones por iteración se repite) ...
    *   **Iteración 32:**
        *   `beq $t3,$t2,end_loop` -> Compara `$t3`(31) con `$t2`(32). No son iguales. **No salta.** (1 instrucción)
        *   `add $t3,$t3,$t1` -> `$t3` = 31 + 1 = 32. (1 instrucción)
        *   `j init_loop` -> Salta a `init_loop`. (1 instrucción)
    *   **Última comprobación del `beq`:**
        *   `beq $t3,$t2,end_loop` -> Compara `$t3`(32) con `$t2`(32). ¡Son iguales! **Salta** a `end_loop`. (1 instrucción)

3.  **Después del Bucle (1 instrucción):**
    *   `sw $t3, 24($zero)` -> Almacena `$t3`(32) en `Mem[24]`.

4.  **Bucle Final (1 instrucción + repeticiones):**
    *   `j end_program` -> Salta a sí mismo, quedando en un bucle infinito.

**Conteo Total de Instrucciones (antes del bucle final):**

*   Setup: 3 instrucciones.
*   Iteraciones del bucle donde NO se salta: El bucle (`beq` no tomado + `add` + `j`) se ejecuta cuando `$t3` va de 0 a 31. Eso son 32 iteraciones. Cada iteración son 3 instrucciones. Total = 32 * 3 = 96 instrucciones.
*   Última comprobación del `beq` (cuando SÍ se salta): 1 instrucción.
*   Instrucción `sw` después del bucle: 1 instrucción.
*   **Total = 3 + 96 + 1 + 1 = 101 instrucciones.**

**Conclusión:**

Tu análisis es correcto. Con los datos proporcionados (`Mem[20] = 32`), el programa `program2` ejecuta un **bucle finito** (`init_loop`) que itera 32 veces (incrementando `$t3` de 0 a 32). El número total de instrucciones ejecutadas antes de entrar en el bucle infinito final (`j end_program`) es exactamente **101**. Esto coincide perfectamente con tu observación de que ejecuta "alrededor de 100 instrucciones".

**Diferencia de Latencia:**

*   Diferencia = Latencia(`program2`) - Latencia(`program1`)
*   Diferencia = 5050 ns - 1450 ns = **3600 ns**

**Conclusión:**

El `program2` (el que tiene el bucle `init_loop`) tiene una latencia significativamente mayor que el `program1` (el secuencial). La diferencia de latencia es de **3600 ns**. Esto se debe a que `program2` ejecuta 101 - 29 = 72 instrucciones más que `program1` antes de alcanzar su estado final de bucle infinito.


al final para calcular la latencia de program dos como cantidad de instrucciones se toma solo antes del bucle