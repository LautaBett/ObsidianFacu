# Arquitectura MIPS: Resumen Detallado

Este resumen expande la información del video sobre la arquitectura MIPS, organizándola de manera más clara y agregando detalles relevantes.

## Características Fundamentales de MIPS

*   **Registros:**
    *   MIPS cuenta con 32 registros de propósito general, numerados del `$0` al `$31`.
    *   Estos registros se utilizan para almacenar datos y direcciones durante la ejecución de un programa.
    *   El registro `$0` está cableado a cero; siempre devuelve el valor 0 cuando se lee. Es útil para ciertas operaciones y como valor por defecto.
*   **Tamaño de Datos e Instrucciones:**
    *   Tanto los datos como las instrucciones tienen un tamaño fijo de 32 bits (4 bytes). Esto simplifica el diseño del procesador y facilita la gestión de la memoria.
*   **Arquitectura Harvard:**
    *   MIPS utiliza una arquitectura Harvard, lo que significa que tiene memorias separadas para datos e instrucciones.
    *   Esto permite acceder a las instrucciones y a los datos simultáneamente, mejorando el rendimiento.
*   **Espacio de Memoria:**
    *   La memoria se organiza en palabras de 32 bits.
    *   El espacio de memoria total es de $2^{30}$ palabras, lo que equivale a $2^{32}$ bytes (4 GB).
*   **Acceso a Memoria:**
    *   MIPS es una arquitectura *load-store*. Esto significa que las operaciones aritméticas y lógicas solo pueden realizarse en datos que están en los registros.
    *   Para acceder a los datos en la memoria, se utilizan las instrucciones `load` y `store`.
        *   `load` (ej., `lw` - load word): Carga datos desde la memoria a un registro.
        *   `store` (ej., `sw` - store word): Guarda datos desde un registro a la memoria.

## Organización de la Memoria

*   **Direccionamiento por Bytes:**
    *   Cada byte en la memoria tiene su propia dirección única.
*   **Acceso a la Memoria de Programa:**
    *   La memoria de programa se accede por palabras (32 bits).
    *   Las direcciones de los bytes deben ser múltiplos de 4 para acceder a una instrucción válida. Esto se debe a que las instrucciones tienen un tamaño de 4 bytes.

## Formatos de Instrucción

MIPS utiliza tres formatos principales de instrucciones: Tipo-R, Tipo-I y Tipo-J. Cada formato tiene una estructura diferente para especificar la operación, los operandos y la dirección de destino.

### Tipo-R (Register)

*   **Uso:** Operaciones aritméticas y lógicas entre registros.
*   **Formato:** `op rs rt rd shamt funct`
    *   `op` (opcode): Código de operación (6 bits).
    *   `rs` (source register): Primer registro fuente (5 bits).
    *   `rt` (source register): Segundo registro fuente (5 bits).
    *   `rd` (destination register): Registro destino (5 bits).
    *   `shamt` (shift amount): Cantidad de desplazamiento (5 bits).  Se usa en instrucciones de desplazamiento.
    *   `funct` (function code): Código de función (6 bits).  Extiende el opcode para especificar la operación exacta.
*   **Ejemplos:**
    *   `add $17, $12, $23`: `$17 = $12 + $23` (Suma el contenido de los registros `$12` y `$23`, y guarda el resultado en `$17`).
    *   `slt $1, $2, $3`: `if ($2 < $3) $1 = 1; else $1 = 0;` (Set Less Than: Si el valor en `$2` es menor que el valor en `$3`, entonces `$1` se establece a 1; de lo contrario, `$1` se establece a 0).

### Tipo-I (Immediate)

*   **Uso:** Operaciones con una constante inmediata, carga/almacenamiento, y saltos condicionales.
*   **Formato:** `op rs rt immediate`
    *   `op` (opcode): Código de operación (6 bits).
    *   `rs` (source register): Registro fuente (5 bits).
    *   `rt` (target register): Registro destino (5 bits).
    *   `immediate`: Valor inmediato (constante de 16 bits).
*   **Ejemplos:**
    *   `addi $rt, $rs, immediate`: `$rt = $rs + immediate` (Suma el valor inmediato al registro `$rs` y guarda el resultado en `$rt`).
    *   `lw $9, 76($15)`: `$9 = memory[$15 + 76]` (Carga el valor de la memoria en la dirección `$15 + 76` al registro `$9`).  `76` es el *offset*.
    *   `beq $8, $15, 134`: `if ($15 == $8) PC = PC + 4 + 134 * 4` (Branch if Equal: Si el valor en `$15` es igual al valor en `$8`, salta a la dirección `PC + 4 + 134 * 4`).

#### Saltos Condicionales (Tipo-I)

*   `beq` (Branch if Equal): Salta si dos registros son iguales.
*   `bne` (Branch if Not Equal): Salta si dos registros no son iguales.
*   **Rango de Salto:** El valor inmediato en las instrucciones de salto condicional es un desplazamiento de 16 bits *en palabras*. Esto significa que el rango de salto es de -32768 a +32767 palabras desde la instrucción siguiente.

### Tipo-J (Jump)

*   **Uso:** Saltos incondicionales a una dirección específica.
*   **Formato:** `op target address`
    *   `op` (opcode): Código de operación (6 bits).
    *   `target address`: Dirección de destino del salto (26 bits).
*   **Ejemplo:**
    *   `j 334`: `PC = (PC + 4)[31...28] & (334 * 4)` (Salta a la dirección calculada combinando los 4 bits más significativos del PC actual con la dirección de 26 bits multiplicada por 4).

#### Cálculo de la Dirección de Salto (Tipo-J)

1.  Multiplica la dirección de 26 bits por 4 (desplazamiento a nivel de byte).
2.  Reemplaza los 28 bits menos significativos del PC actual + 4 con el resultado del paso 1.
3.  Los 4 bits más significativos del PC no cambian, lo que limita el salto a un rango de 256MB.

## Modos de Direccionamiento

MIPS soporta varios modos de direccionamiento para acceder a los operandos:

*   **Mediante Registros (Tipo-R):** Los operandos están en registros. (Ej: `add`, `sub`, `and`)
*   **Inmediato (Tipo-I):** Un operando es una constante incluida en la instrucción. (Ej: `addi`, `subi`, `andi`)
*   **Registro Base (Tipo-I):** La dirección de memoria se calcula sumando un valor inmediato a un registro base. (Ej: `lw`, `sw`)
*   **Relativo a PC (Tipo-I):** La dirección de salto se calcula sumando un desplazamiento al valor actual del Program Counter (PC). (Ej: `beq`, `bne`)
*   **Pseudo Directo (Tipo-J):** La dirección de salto se construye combinando partes del PC actual con un valor en la instrucción. (Ej: `j`, `jal`)

## Consideraciones Adicionales

*   **PC + 4:** En la mayoría de las instrucciones, el Program Counter (PC) se incrementa en 4 (el tamaño de una instrucción) para apuntar a la siguiente instrucción en la secuencia.  Las instrucciones de salto (condicionales e incondicionales) modifican este comportamiento.
*   **Extensión de Signo (Sign Extension):** El valor inmediato de 16 bits en las instrucciones de Tipo-I se extiende a 32 bits antes de realizar la operación. Si el bit más significativo (bit 15) del valor inmediato es 1 (negativo), se añaden 1s a la izquierda. Si es 0 (positivo), se añaden 0s. Esto asegura que el valor se interprete correctamente como un número con signo.
BEQ
No es que `beq` *sume* o *reste* directamente valores en los registros. Más bien, `beq` *compara* dos registros y, basándose en el resultado de esa comparación, *modifica el Program Counter (PC)* para saltar a una nueva ubicación en el código.

Aquí te lo explico paso a paso:

1.  **Comparación:** `beq rs, rt, offset` compara el valor en el registro `rs` con el valor en el registro `rt`.
2.  **Condición:** Si el valor en `rs` es *igual* al valor en `rt`, la condición se cumple.
3.  **Salto (Modificación del PC):** Si la condición se cumple (es decir, `rs == rt`), el PC se modifica para saltar a una nueva instrucción. La nueva dirección se calcula de la siguiente manera:

    `PC = PC + 4 + (offset * 4)`

    *   `PC`: Es el valor actual del Program Counter (la dirección de la instrucción `beq`).
    *   `PC + 4`: Es la dirección de la *siguiente* instrucción (la que se ejecutaría si no hubiera salto). Siempre se suma 4 porque las instrucciones MIPS tienen un tamaño de 4 bytes.
    *   `offset`: Es un valor inmediato de 16 bits que indica el desplazamiento *en palabras* (no en bytes) desde la siguiente instrucción.
    *   `offset * 4`: Convierte el desplazamiento de palabras a bytes.

4.  **Si la condición no se cumple:** Si el valor en `rs` *no es igual* al valor en `rt`, el PC simplemente se incrementa en 4 (como lo haría normalmente), y la siguiente instrucción en secuencia se ejecuta. No hay salto.

**En resumen:**

*   `beq` *no* realiza una operación aritmética en los registros `rs` y `rt`.
*   `beq` *compara* los valores en `rs` y `rt`.
*   Si la comparación es verdadera (`rs == rt`), `beq` *modifica* el PC para saltar a una nueva ubicación. La suma que ves en la fórmula `PC = PC + 4 + (offset * 4)` es para calcular la *nueva dirección* del PC, no para sumar valores en los registros.
*   Si la comparación es falsa, el PC no se modifica, y el programa continúa ejecutándose en secuencia.

**Ejemplo:**

`beq $8, $15, 134`

*   Compara el valor en `$8` con el valor en `$15`.
*   Si `$8` es igual a `$15`, entonces:

    `PC = PC + 4 + (134 * 4)`

    Esto significa que el PC se actualiza para apuntar a la instrucción que está 134 palabras (536 bytes) más adelante en la memoria.



