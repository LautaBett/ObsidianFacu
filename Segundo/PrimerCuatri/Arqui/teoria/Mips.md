# Arquitectura del MIPS

## Repaso de Conceptos Previos

Antes de profundizar en la arquitectura MIPS, es importante recordar algunos conceptos clave vistos en cursos introductorios de arquitectura de sistemas:

*   Principios de diseño de computadoras.
*   Juego de instrucciones: El conjunto de operaciones que la CPU puede ejecutar.
*   Formato de memoria y registros internos: Cómo se organizan los datos dentro de la CPU y en la memoria.
*   Modos de direccionamiento: Las diferentes formas en que una instrucción puede especificar la ubicación de los datos que va a usar.

## Procesador MIPS (Repaso)

*   MIPS significa "Microprocessor without Interlocked Pipeline Stages".
*   Registros: El MIPS tiene 32 registros de propósito general, numerados del `$0` al `$31`. El registro `$0` siempre tiene el valor 0.
*   Tamaño de datos e instrucciones: Tanto los datos como las instrucciones tienen un tamaño de 32 bits.
*   Memorias Harvard: El MIPS utiliza memorias separadas para datos y para el programa (arquitectura Harvard).
*   Espacio de memoria: La memoria tiene un tamaño de $2^{30}$ palabras de 32 bits (o $2^{32}$ bytes).
*   Instrucciones de acceso a memoria:
    *   `load` (lw): Carga datos desde la memoria al registro.
    *   `store` (sw): Guarda datos desde un registro a la memoria.

## Acerca de las Memorias (Repaso)

*   Las instrucciones `load` y `store` transfieren datos entre la memoria de datos y los registros internos de la CPU.
*   Cada byte en la memoria tiene su propia dirección única.
*   La memoria de datos tiene un tamaño de $2^{30}$ palabras de 32 bits (4 bytes por palabra), lo que equivale a $2^{32}$ bytes.
*   La memoria de programa se accede por palabras, y las direcciones de los bytes deben ser múltiplos de 4.

## Repertorio de Instrucciones

El MIPS utiliza tres formatos principales de instrucciones:

*   **Tipo-R (Register):**
    *   Utilizado para operaciones aritméticas y lógicas entre registros.
    *   `op rs rt rd shamt funct`
    *   `op`: Código de operación.
    *   `rs`, `rt`: Registros fuente.
    *   `rd`: Registro destino.
    *   `shamt`: Cantidad de desplazamiento (para instrucciones de desplazamiento).
    *   `funct`: Código de función (para distinguir entre diferentes operaciones aritméticas/lógicas).
    *   *Ejemplos:* `add $rd, $rs, $rt` (suma), `sub $rd, $rs, $rt` (resta), `slt $rd, $rs, $rt` (set less than).
*   **Tipo-I (Immediate):**
    *   Utilizado para operaciones que involucran una constante inmediata (un valor numérico directamente en la instrucción). También se usa para instrucciones de carga/almacenamiento y saltos condicionales.
    *   `op rs rt immediate`
    *   `op`: Código de operación.
    *   `rs`: Registro fuente.
    *   `rt`: Registro destino.
    *   `immediate`: Valor inmediato (16 bits).
    *   *Ejemplos:* `addi $rt, $rs, immediate` (suma inmediata), `lw $rt, offset($rs)` (carga desde memoria), `beq $rs, $rt, label` (branch if equal).
*   **Tipo-J (Jump):**
    *   Utilizado para saltos incondicionales a una dirección específica.
    *   `op target address`
    *   `op`: Código de operación.
    *   `target address`: Dirección de destino del salto (26 bits).
    *   *Ejemplos:* `j label` (salto incondicional), `jal label` (jump and link - guarda la dirección de retorno en el registro `$31`).

## Modos de Direccionamiento (Repaso)

*   Mediante registros: Los operandos están en registros. (Tipo-R)
*   Inmediato: Un operando es una constante incluida en la instrucción. (Tipo-I)
*   Mediante registro base: La dirección de memoria se calcula sumando un valor inmediato a un registro base. (Tipo-I, `lw` y `sw`)
*   Relativo a PC: La dirección de salto se calcula sumando un desplazamiento al valor actual del Program Counter (PC). (Tipo-I, `beq`, `bne`)
*   Pseudo directo: La dirección de salto se construye combinando partes del PC actual con un valor en la instrucción. (Tipo-J, `j`, `jal`)

## Diseño del Microprocesador MIPS

*   Microprocesador de 32 bits de un ciclo (uniciclo o combinacional): Cada instrucción se ejecuta en un solo ciclo de reloj.
*   Instrucciones implementadas: El diseño se centra en las siguientes instrucciones:
    *   `lw` y `sw` (acceso a memoria)
    *   `add`, `sub`, `and`, `slt` (operaciones aritméticas y lógicas de tipo R)
    *   `beq` (salto condicional)
    *   `j` (salto incondicional)

## Ejecución RTL (Register Transfer Level)

Describe cómo se transfieren los datos entre los registros y la memoria durante la ejecución de una instrucción.

*   *Ejemplo:*
    *   `add $8, $7, $9`:
        *   `Instruction ← Mem[PC];` (Se obtiene la instrucción de la memoria)
        *   `PC ← PC + 4` (Se incrementa el PC para la siguiente instrucción)
        *   `Reg[8] = Reg[7] + Reg[9]` (Se realiza la suma y se guarda el resultado en el registro destino)
    *   `lw $12, 132($19)`:
        *   `Instruction ← Mem[PC];`
        *   `PC ← PC + 4`
        *   `Reg[12] = Mem[Reg[19] + 132]`

## Componentes Principales del Diseño

*   Fetch de la instrucción: Obtiene la instrucción de la memoria y actualiza el PC.
*   Lectura de registros: Lee uno o dos registros fuente.
*   ALU (Arithmetic Logic Unit): Realiza operaciones aritméticas, lógicas y cálculos de direcciones de memoria.
*   Acceso a memoria: Lee o escribe datos en la memoria (para `lw` y `sw`).
*   Unidad de Control: Genera las señales de control necesarias para coordinar la operación de los demás componentes.

![[Pasted image 20250421213755.png]]