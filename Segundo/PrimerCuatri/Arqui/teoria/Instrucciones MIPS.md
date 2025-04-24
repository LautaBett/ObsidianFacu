¡Claro! Aquí tienes la clasificación de las instrucciones MIPS utilizadas en la nota [[Ejercicios]] según su formato (Tipo-R, Tipo-I, Tipo-J), basándonos en las definiciones de [[Mips]] y [[Primer video]]:

**Recordatorio de Formatos:**

*   **Tipo-R (Register):** Operaciones entre registros. Campos `op`, `rs`, `rt`, `rd`, `shamt`, `funct`. (Ej: `add`, `sub`, `sll`, `slt`, `jr`, `mul`).
*   **Tipo-I (Immediate):** Operaciones con un valor inmediato, cargas/almacenamientos, saltos condicionales. Campos `op`, `rs`, `rt`, `immediate`. (Ej: `addi`, `slti`, `lw`, `sw`, `beq`, `bne`).
*   **Tipo-J (Jump):** Saltos incondicionales largos. Campos `op`, `target address`. (Ej: `j`, `jal`).

---

**Ejercicio 1: `f = (g + h) - (i + j);`**

*   `add $t0, $s1, $s2`: **Tipo-R** (Operación aritmética entre registros).
*   `add $t1, $s3, $s4`: **Tipo-R** (Operación aritmética entre registros).
*   `sub $s0, $t0, $t1`: **Tipo-R** (Operación aritmética entre registros).

---

**Ejercicio 2: Sentencia Condicional `if/else`**

*   `beq $s3, $s4, if_true`: **Tipo-I** (Salto condicional, compara registros y usa un offset inmediato).
*   `sub $s0, $s1, $s2`: **Tipo-R** (Operación aritmética entre registros).
*   `j endif`: **Tipo-J** (Salto incondicional a una dirección/etiqueta).
*   `add $s0, $s1, $s2`: **Tipo-R** (Operación aritmética entre registros).

---

**Ejercicio 3: Bucle `while`**

*   `sll $t0, $s3, 2`: **Tipo-R** (Desplazamiento lógico, usa registro fuente `rt`=$s3, destino `rd`=$t0 y campo `shamt`=2).
*   `add $t0, $s6, $t0`: **Tipo-R** (Operación aritmética entre registros).
*   `lw $t1, 0($t0)`: **Tipo-I** (Carga desde memoria, usa registro base `$t0` y offset inmediato 0).
*   `bne $t1, $s5, endloop`: **Tipo-I** (Salto condicional, compara registros y usa un offset inmediato).
*   `addi $s3, $s3, 1`: **Tipo-I** (Suma un valor inmediato a un registro).
*   `j loop`: **Tipo-J** (Salto incondicional a una dirección/etiqueta).

---

**Ejercicio 4: Instrucción `JR`**

*   `jr $rs`: **Tipo-R** (Aunque es un salto, usa el formato R con opcode 0 y un código `funct` específico. El registro `rs` contiene la dirección de salto).

---

**Ejercicio 5: Función `example`**

*   `addi $sp, $sp, -8`: **Tipo-I** (Suma un valor inmediato a un registro).
*   `sw $ra, 4($sp)`: **Tipo-I** (Almacena en memoria, usa registro base `$sp` y offset inmediato 4).
*   `sw $s0, 0($sp)`: **Tipo-I** (Almacena en memoria, usa registro base `$sp` y offset inmediato 0).
*   `add $t0, $a0, $a1`: **Tipo-R** (Operación aritmética entre registros).
*   `add $t1, $a2, $a3`: **Tipo-R** (Operación aritmética entre registros).
*   `sub $s0, $t0, $t1`: **Tipo-R** (Operación aritmética entre registros).
*   `move $v0, $s0`: **Pseudo-instrucción**, típicamente implementada como `add $v0, $s0, $zero`, que es **Tipo-R**.
*   `lw $s0, 0($sp)`: **Tipo-I** (Carga desde memoria, usa registro base `$sp` y offset inmediato 0).
*   `lw $ra, 4($sp)`: **Tipo-I** (Carga desde memoria, usa registro base `$sp` y offset inmediato 4).
*   `addi $sp, $sp, 8`: **Tipo-I** (Suma un valor inmediato a un registro).
*   `jr $ra`: **Tipo-R** (Salto a la dirección contenida en el registro `$ra`).

---

**Ejercicio 6: Instrucción `JAL`**

*   `jal target`: **Tipo-J** (Salto incondicional con enlace, usa una dirección de destino).

---

**Ejercicio 7: Llamadas a Funciones Anidadas**

*   `addi $sp, $sp, -24`: **Tipo-I**.
*   `sw $ra, 20($sp)`: **Tipo-I**.
*   `sw $s0, 16($sp)`: **Tipo-I**.
*   `sw $a2, 12($sp)`: **Tipo-I**.
*   `sw $a3, 8($sp)`: **Tipo-I**.
*   `sw $a4, 4($sp)`: **Tipo-I**.
*   `sw $a5, 0($sp)`: **Tipo-I**.
*   `move $a0, $a0`: Pseudo-instrucción (**Tipo-R**).
*   `move $a1, $a1`: Pseudo-instrucción (**Tipo-R**).
*   `jal suma`: **Tipo-J**.
*   `move $a4, $v0`: Pseudo-instrucción (**Tipo-R**).
*   `move $a0, $a2`: Pseudo-instrucción (**Tipo-R**).
*   `move $a1, $a3`: Pseudo-instrucción (**Tipo-R**).
*   `jal suma`: **Tipo-J**.
*   `move $a5, $v0`: Pseudo-instrucción (**Tipo-R**).
*   `sub $s0, $a4, $a5`: **Tipo-R**.
*   `lw $ra, 20($sp)`: **Tipo-I**.
*   `lw $s0, 16($sp)`: **Tipo-I**.
*   `lw $a2, 12($sp)`: **Tipo-I**.
*   `lw $a3, 8($sp)`: **Tipo-I**.
*   `lw $a4, 4($sp)`: **Tipo-I**.
*   `lw $a5, 0($sp)`: **Tipo-I**.
*   `addi $sp, $sp, 24`: **Tipo-I**.
*   `jr $ra`: **Tipo-R**.
*   *Dentro de `suma`:*
    *   `add $v0, $a0, $a1`: **Tipo-R**.
    *   `jr $ra`: **Tipo-R**.

---

**Ejercicio 8: Función Factorial (Recursiva)**

*   `addi $sp, $sp, -8`: **Tipo-I**.
*   `sw $ra, 4($sp)`: **Tipo-I**.
*   `sw $a0, 0($sp)`: **Tipo-I**.
*   `slti $t0, $a0, 1`: **Tipo-I** (Set Less Than Immediate, compara registro con inmediato).
*   `bne $t0, $zero, base_case`: **Tipo-I**.
*   `addi $a0, $a0, -1`: **Tipo-I**.
*   `jal factorial`: **Tipo-J**.
*   `lw $a0, 0($sp)`: **Tipo-I**.
*   `mul $v0, $a0, $v0`: **Tipo-R** (Multiplicación, generalmente formato R con `funct` específico, usa registros HI/LO no mostrados explícitamente).
*   `j end_factorial`: **Tipo-J**.
*   `addi $v0, $zero, 1`: **Tipo-I**.
*   `lw $ra, 4($sp)`: **Tipo-I**.
*   `addi $sp, $sp, 8`: **Tipo-I**.
*   `jr $ra`: **Tipo-R**.

---

**Ejercicio 9: Rango de Salto de `beq`**

*   `beq $s0, $s1, L1`: **Tipo-I**.
*   *Código de reemplazo:*
    *   `bne $s0, $s1, L2`: **Tipo-I**.
    *   `j L1`: **Tipo-J**.

---

Esta clasificación te ayuda a ver cómo se utilizan los diferentes formatos de instrucción MIPS para construir las secuencias de código de los ejercicios.


¡Entendido! Quieres una explicación detallada de cada tipo de instrucción (R, I, J) y de las instrucciones específicas que aparecen en la nota [[Ejercicios]], explicando qué hacen, su formato general y cómo se usan en los ejemplos.

Aquí vamos, basándonos en la información de [[Mips]], [[Primer video]] y los ejemplos de [[Ejercicios]]:

---

## Formato Tipo-R (Register)

*   **Propósito:** Realizar operaciones (aritméticas, lógicas, desplazamientos) utilizando únicamente registros como operandos fuente y destino.
*   **Formato General:** `op rs rt rd shamt funct`
    *   `op`: Código de operación principal (suele ser 0 para Tipo-R).
    *   `rs`: Primer registro fuente.
    *   `rt`: Segundo registro fuente (o registro a desplazar en `sll`/`srl`).
    *   `rd`: Registro destino donde se guarda el resultado.
    *   `shamt`: Cantidad de desplazamiento (usado solo en instrucciones de desplazamiento como `sll`).
    *   `funct`: Código de función que especifica la operación exacta (ej. suma, resta, AND, OR, desplazamiento).

**Instrucciones Tipo-R en [[Ejercicios]]:**

1.  **`add rd, rs, rt`**
    *   **Operación (`funct`):** Suma con signo (maneja overflow).
    *   **Qué hace:** Suma el contenido del registro `rs` y el registro `rt`. Guarda el resultado de 32 bits en el registro `rd`.
    *   **Uso:** `rd = rs + rt`
    *   **Ejemplo Explicado:** `add $t0, $s1, $s2` (Ejercicio 1)
        *   Suma el valor en `$s1` (variable `g`) y el valor en `$s2` (variable `h`).
        *   Guarda el resultado (`g + h`) en el registro temporal `$t0`.

2.  **`sub rd, rs, rt`**
    *   **Operación (`funct`):** Resta con signo (maneja overflow).
    *   **Qué hace:** Resta el contenido del registro `rt` del contenido del registro `rs`. Guarda el resultado de 32 bits en el registro `rd`.
    *   **Uso:** `rd = rs - rt`
    *   **Ejemplo Explicado:** `sub $s0, $t0, $t1` (Ejercicio 1)
        *   Resta el valor en `$t1` (que contiene `i + j`) del valor en `$t0` (que contiene `g + h`).
        *   Guarda el resultado final (`(g + h) - (i + j)`) en el registro `$s0` (variable `f`).

3.  **`sll rd, rt, shamt`** (Shift Left Logical)
    *   **Operación (`funct`):** Desplazamiento lógico a la izquierda.
    *   **Qué hace:** Desplaza los bits del registro `rt` hacia la izquierda tantas posiciones como indique el valor `shamt` (un número entre 0 y 31). Los bits que "entran" por la derecha son siempre ceros. El registro `rs` no se usa.
    *   **Uso:** `rd = rt << shamt` (Equivalente a multiplicar `rt` por $2^{shamt}$).
    *   **Ejemplo Explicado:** `sll $t0, $s3, 2` (Ejercicio 3)
        *   Toma el valor del índice `i` (en `$s3`) y lo desplaza 2 bits a la izquierda.
        *   Esto es equivalente a multiplicar `i` por 4 ($2^2$).
        *   Guarda el resultado (el desplazamiento en bytes dentro del array `save`) en `$t0`.

4.  **`jr rs`** (Jump Register)
    *   **Operación (`funct`):** Salto a registro.
    *   **Qué hace:** Cambia el flujo del programa saltando incondicionalmente a la dirección de memoria contenida en el registro `rs`. Los campos `rt`, `rd` y `shamt` no se usan.
    *   **Uso:** `PC = rs` (El Program Counter se carga con el valor de `rs`).
    *   **Ejemplo Explicado:** `jr $ra` (Ejercicios 5, 7, 8)
        *   Salta a la dirección contenida en el registro `$ra`.
        *   Se usa típicamente para retornar de una función, ya que `$ra` contiene la dirección a la que se debe volver después de que la función termine (guardada por `jal`).

5.  **`mul rd, rs, rt`** (Multiply - A menudo pseudo-instrucción o usa HI/LO)
    *   **Operación (`funct`):** Multiplicación.
    *   **Qué hace:** Multiplica el contenido de `rs` por el de `rt`. En implementaciones simples o como pseudo-instrucción, puede guardar los 32 bits inferiores del resultado en `rd`. (En MIPS real, la multiplicación de 32x32 produce 64 bits, guardados en registros especiales HI y LO).
    *   **Uso (simplificado):** `rd = rs * rt`
    *   **Ejemplo Explicado:** `mul $v0, $a0, $v0` (Ejercicio 8)
        *   Multiplica el valor original de `n` (restaurado en `$a0`) por el resultado de `factorial(n-1)` (que está en `$v0` tras la llamada recursiva).
        *   Guarda el resultado de la multiplicación (`n * factorial(n-1)`) en `$v0` para ser retornado.

6.  **`move rd, rs`** (Pseudo-instrucción)
    *   **Implementación:** Generalmente `add rd, rs, $zero` (Tipo-R) o `or rd, rs, $zero` (Tipo-R).
    *   **Qué hace:** Copia el contenido del registro `rs` al registro `rd`.
    *   **Uso:** `rd = rs`
    *   **Ejemplo Explicado:** `move $v0, $s0` (Ejercicio 5)
        *   Copia el valor calculado de `f` (que está en `$s0`) al registro `$v0`.
        *   Se usa para poner el valor de retorno de la función en el registro `$v0`, según la convención de llamada.

---

## Formato Tipo-I (Immediate)

*   **Propósito:** Realizar operaciones que involucran un valor constante (inmediato), cargar datos desde memoria, guardar datos en memoria y realizar saltos condicionales.
*   **Formato General:** `op rs rt immediate`
    *   `op`: Código de operación principal.
    *   `rs`: Registro fuente (o registro base para `lw`/`sw`).
    *   `rt`: Registro destino (para `addi`, `lw`) o segundo registro fuente (para `beq`/`bne`, `sw`).
    *   `immediate`: Valor constante de 16 bits. Se extiende con signo para operaciones aritméticas (`addi`) y cálculo de direcciones (`lw`/`sw`, `beq`/`bne`).

**Instrucciones Tipo-I en [[Ejercicios]]:**

1.  **`addi rt, rs, immediate`** (Add Immediate)
    *   **Operación (`op`):** Suma inmediata con signo (maneja overflow).
    *   **Qué hace:** Suma el contenido del registro `rs` con el valor `immediate` (extendido a 32 bits con signo). Guarda el resultado en `rt`.
    *   **Uso:** `rt = rs + sign_extend(immediate)`
    *   **Ejemplo Explicado:** `addi $s3, $s3, 1` (Ejercicio 3)
        *   Suma 1 al valor actual del registro `$s3` (índice `i`).
        *   Guarda el resultado (`i + 1`) de nuevo en `$s3`. Se usa para incrementar el índice del bucle.
    *   **Ejemplo Explicado:** `addi $sp, $sp, -8` (Ejercicio 5)
        *   Suma -8 al valor actual del puntero de pila (`$sp`).
        *   Guarda el nuevo valor (`$sp - 8`) de nuevo en `$sp`. Se usa para reservar 8 bytes en la pila.

2.  **`lw rt, immediate(rs)`** (Load Word)
    *   **Operación (`op`):** Cargar palabra desde memoria.
    *   **Qué hace:** Calcula una dirección de memoria sumando el valor `immediate` (offset con signo) al contenido del registro base `rs`. Carga la palabra (32 bits) desde esa dirección de memoria y la guarda en el registro `rt`.
    *   **Uso:** `rt = Mem[rs + sign_extend(immediate)]`
    *   **Ejemplo Explicado:** `lw $t1, 0($t0)` (Ejercicio 3)
        *   Calcula la dirección: `$t0 + 0`. El registro `$t0` ya contiene la dirección calculada de `save[i]`.
        *   Carga la palabra de 32 bits desde esa dirección de memoria.
        *   Guarda el valor cargado (el contenido de `save[i]`) en el registro `$t1`.
    *   **Ejemplo Explicado:** `lw $ra, 4($sp)` (Ejercicio 5)
        *   Calcula la dirección: `$sp + 4`.
        *   Carga la palabra desde esa dirección de la pila.
        *   Guarda el valor cargado (la dirección de retorno original) en `$ra`. Se usa para restaurar `$ra` antes de retornar.

3.  **`sw rt, immediate(rs)`** (Store Word)
    *   **Operación (`op`):** Guardar palabra en memoria.
    *   **Qué hace:** Calcula una dirección de memoria sumando el valor `immediate` (offset con signo) al contenido del registro base `rs`. Guarda (almacena) el contenido del registro `rt` en esa dirección de memoria.
    *   **Uso:** `Mem[rs + sign_extend(immediate)] = rt`
    *   **Ejemplo Explicado:** `sw $ra, 4($sp)` (Ejercicio 5)
        *   Calcula la dirección: `$sp + 4`.
        *   Guarda el contenido del registro `$ra` (la dirección de retorno) en esa dirección de la memoria (en la pila). Se usa para guardar `$ra` al inicio de la función.

4.  **`beq rs, rt, label`** (Branch on Equal)
    *   **Operación (`op`):** Salto condicional si son iguales.
    *   **Qué hace:** Compara el contenido de `rs` y `rt`. Si son iguales, calcula la dirección de destino sumando el `immediate` (offset de 16 bits, multiplicado por 4 y con signo) a la dirección de la *siguiente* instrucción (PC+4) y salta a esa dirección. Si no son iguales, continúa con la siguiente instrucción (PC+4).
    *   **Uso:** `if (rs == rt) PC = PC + 4 + (sign_extend(immediate) * 4)`
    *   **Ejemplo Explicado:** `beq $s3, $s4, if_true` (Ejercicio 2)
        *   Compara `$s3` (`i`) y `$s4` (`j`).
        *   Si son iguales, salta a la instrucción etiquetada como `if_true`.
        *   Si no son iguales, ejecuta la siguiente instrucción (`sub $s0, $s1, $s2`).

5.  **`bne rs, rt, label`** (Branch on Not Equal)
    *   **Operación (`op`):** Salto condicional si no son iguales.
    *   **Qué hace:** Compara el contenido de `rs` y `rt`. Si *no* son iguales, calcula la dirección de destino sumando el `immediate` (offset de 16 bits, multiplicado por 4 y con signo) a la dirección de la *siguiente* instrucción (PC+4) y salta a esa dirección. Si son iguales, continúa con la siguiente instrucción (PC+4).
    *   **Uso:** `if (rs != rt) PC = PC + 4 + (sign_extend(immediate) * 4)`
    *   **Ejemplo Explicado:** `bne $t1, $s5, endloop` (Ejercicio 3)
        *   Compara `$t1` (valor de `save[i]`) y `$s5` (valor de `k`).
        *   Si *no* son iguales, salta a la instrucción etiquetada como `endloop` (sale del bucle).
        *   Si son iguales, ejecuta la siguiente instrucción (`addi $s3, $s3, 1`).

6.  **`slti rt, rs, immediate`** (Set on Less Than Immediate)
    *   **Operación (`op`):** Comparación "menor que" con inmediato.
    *   **Qué hace:** Compara el contenido del registro `rs` con el valor `immediate` (extendido con signo). Si `rs` es menor que `immediate`, guarda 1 en `rt`. Si no, guarda 0 en `rt`.
    *   **Uso:** `rt = (rs < sign_extend(immediate)) ? 1 : 0`
    *   **Ejemplo Explicado:** `slti $t0, $a0, 1` (Ejercicio 8)
        *   Compara el valor de `n` (en `$a0`) con el inmediato 1.
        *   Si `$a0 < 1`, guarda 1 en `$t0`.
        *   Si `$a0 >= 1`, guarda 0 en `$t0`. Se usa para la condición del caso base `if (n < 1)`.

---

## Formato Tipo-J (Jump)

*   **Propósito:** Realizar saltos incondicionales a una dirección lejana (dentro del mismo segmento de 256MB).
*   **Formato General:** `op target_address`
    *   `op`: Código de operación principal.
    *   `target_address`: Campo de 26 bits que forma parte de la dirección de destino.

**Instrucciones Tipo-J en [[Ejercicios]]:**

1.  **`j label`** (Jump)
    *   **Operación (`op`):** Salto incondicional.
    *   **Qué hace:** Calcula la dirección de destino tomando los 4 bits más significativos del PC actual (PC+4) y concatenándolos con los 26 bits del `target_address` de la instrucción, desplazados 2 bits a la izquierda (multiplicados por 4). Salta incondicionalmente a esa dirección.
    *   **Uso:** `PC = (PC+4)[31:28] | (target_address << 2)`
    *   **Ejemplo Explicado:** `j endif` (Ejercicio 2)
        *   Salta incondicionalmente a la instrucción etiquetada como `endif`. Se usa para saltar el código del bloque `if` después de ejecutar el bloque `else`.
    *   **Ejemplo Explicado:** `j loop` (Ejercicio 3)
        *   Salta incondicionalmente a la instrucción etiquetada como `loop`. Se usa para volver al inicio del bucle `while`.

2.  **`jal label`** (Jump and Link)
    *   **Operación (`op`):** Salto incondicional con enlace.
    *   **Qué hace:** Primero, guarda la dirección de la instrucción *siguiente* a `jal` (PC+4) en el registro `$ra` (registro 31). Luego, calcula la dirección de destino y salta a ella de la misma manera que la instrucción `j`.
    *   **Uso:** `$ra = PC + 4; PC = (PC+4)[31:28] | (target_address << 2)`
    *   **Ejemplo Explicado:** `jal suma` (Ejercicio 7)
        *   Guarda la dirección de la instrucción siguiente (el `move $a4, $v0` o `move $a5, $v0`) en `$ra`.
        *   Salta a la primera instrucción de la función `suma`.
    *   **Ejemplo Explicado:** `jal factorial` (Ejercicio 8)
        *   Guarda la dirección de la instrucción siguiente (el `lw $a0, 0($sp)`) en `$ra`.
        *   Salta a la primera instrucción de la función `factorial` (llamada recursiva).

---

Espero que esta explicación detallada de cada instrucción y su uso en los ejemplos te sea útil para entender el código MIPS de la nota [[Ejercicios]].