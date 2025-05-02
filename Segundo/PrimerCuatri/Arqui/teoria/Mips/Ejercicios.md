````markdown
# Trabajo Práctico 1: Microprocesador MIPS

## 1. Instrucción de Alto Nivel a MIPS
**Instrucción en alto nivel:** `f = (g + h) - (i + j);`
**Variables asignadas a registros:**
* f -> `$s0` (El resultado final se guarda en $s0)
* g -> `$s1` (Primer operando)
* h -> `$s2` (Segundo operando)
* i -> `$s3` (Tercer operando)
* j -> `$s4` (Cuarto operando)

**Secuencia de instrucciones MIPS:**
```assembly
add $t0, $s1, $s2  # $t0 = g + h (Suma g y h, guarda en temporal $t0)
add $t1, $s3, $s4  # $t1 = i + j (Suma i y j, guarda en temporal $t1)
sub $s0, $t0, $t1  # f = $t0 - $t1  (Resta (g+h) - (i+j), guarda el resultado final en f ($s0))
````

## 2. Sentencia Condicional en MIPS

**Sentencia condicional en alto nivel:**

```
if (i == j)
  f = g + h;
else
  f = g - h;
```

**Variables asignadas a registros:**

- f -> `$s0` (El resultado final se guarda en $s0)
- g -> `$s1` (Primer operando)
- h -> `$s2` (Segundo operando)
- i -> `$s3` (Condición: primer valor a comparar)
- j -> `$s4` (Condición: segundo valor a comparar)

**Secuencia de instrucciones MIPS:**

```assembly
beq $s3, $s4, if_true  # Si (i == j) salta a if_true (Compara i y j. Si son iguales, salta a la etiqueta 'if_true')
sub $s0, $s1, $s2      # else: f = g - h (Si i != j, calcula g - h y guarda en f)
j endif                # Salta al final del condicional (Salta incondicionalmente a la etiqueta 'endif' para evitar ejecutar el bloque 'if')
if_true:
add $s0, $s1, $s2      # if: f = g + h (Si i == j, calcula g + h y guarda en f)
endif:                  # Etiqueta que marca el final del bloque condicional
```

## 3. Bucle `while` en MIPS

**Bucle en C:**

```c
while (save[i] == k)
  i += 1;
```

**Variables asignadas a registros:**

- i -> `$s3` (Índice del arreglo)
- k -> `$s5` (Valor a comparar con el elemento del arreglo)
- base de `save` -> `$s6` (Dirección base del arreglo 'save')

**Código ensamblador MIPS:**

```assembly
loop:
sll $t0, $s3, 2      # $t0 = i * 4  (Calcula el desplazamiento en bytes: i * tamaño de un entero (4 bytes))
add $t0, $s6, $t0      # $t0 = dirección de save[i] (Calcula la dirección en memoria de save[i]: base + desplazamiento)
lw $t1, 0($t0)       # $t1 = save[i] (Carga el valor de save[i] desde la memoria al registro temporal $t1)
bne $t1, $s5, endloop  # Si (save[i] != k) salta a endloop (Compara save[i] con k. Si no son iguales, salta fuera del bucle)
addi $s3, $s3, 1      # i = i + 1 (Incrementa el índice i)
j loop                 # Vuelve al inicio del bucle (Salta incondicionalmente al inicio del bucle)
endloop:                # Etiqueta que marca el final del bucle
```

## 4. Instrucción JR (Jump Register)

**Formato de la instrucción JR:**

```
SPECIAL
000000 rs 00000 00000 000000 001001
```

**Descripción:** PC <- Reg[rs] (El Program Counter (PC) se actualiza con el valor del registro rs)  
**a) Diagrama esquemático del procesador:**  
_(No puedo dibujar el diagrama aquí, pero la modificación principal es que la salida de la unidad de lectura de registros (Reg[rs]) debe conectarse a la entrada del multiplexor que selecciona la dirección del siguiente PC. Además, la señal de control `PCSrc` debe modificarse para incluir una opción que seleccione `Reg[rs]` como la fuente del PC)._  
**b) Señales de control:**

- **RegWrite:** 0 (No se escribe en el banco de registros porque JR solo modifica el PC)
- **ALUSrc:** X (No importa, la ALU no se usa)
- **ALUOp:** XX (No importa, la ALU no se usa)
- **RegDst:** X (No importa, no hay escritura en registros)
- **MemWrite:** 0 (No se escribe en memoria)
- **MemRead:** 0 (No se lee de memoria)
- **MemtoReg:** X (No importa, no hay escritura en registros)
- **PCSrc:** Debe tener un valor (e.g., "10") que seleccione la salida de la unidad de lectura de registros (Reg[rs]) como la fuente del PC. Esto requiere _añadir_ esta opción al multiplexor existente. (La señal PCSrc debe seleccionar la dirección contenida en el registro rs para cargarla en el PC)

## 5. Función `example` en MIPS

**Función en C:**

```c
int example (int g, int h, int i, int j) {
  int f;
  f = (g+h) - (i+j);
  return f;
}
```

**Registros:**

- g -> `$a0` (Primer argumento)
- h -> `$a1` (Segundo argumento)
- i -> `$a2` (Tercer argumento)
- j -> `$a3` (Cuarto argumento)
- f -> `$s0` (Variable local, donde se guarda el resultado)
- Dirección de retorno -> `$ra` (Guarda la dirección a la que debe retornar la función)

**Código MIPS:**

```assembly
example:
  addi $sp, $sp, -8  # Ajusta el puntero de pila para guardar $ra y $s0 (Reserva espacio en la pila para guardar dos registros: $ra y $s0)
  sw $ra, 4($sp)   # Guarda la dirección de retorno (Guarda el valor del registro $ra en la pila)
  sw $s0, 0($sp)   # Guarda el valor de $s0 (Guarda el valor del registro $s0 en la pila)

  add $t0, $a0, $a1  # $t0 = g + h (Suma g y h, guarda en temporal $t0)
  add $t1, $a2, $a3  # $t1 = i + j (Suma i y j, guarda en temporal $t1)
  sub $s0, $t0, $t1  # f = $t0 - $t1 (Resta (g+h) - (i+j), guarda el resultado en f ($s0))

  move $v0, $s0   # Mueve el resultado a $v0 (valor de retorno) (Copia el valor de f ($s0) al registro $v0, que se usa para retornar valores)

  lw $s0, 0($sp)   # Restaura el valor original de $s0 (Restaura el valor original de $s0 desde la pila)
  lw $ra, 4($sp)   # Restaura la dirección de retorno (Restaura el valor del registro $ra desde la pila)
  addi $sp, $sp, 8  # Restaura el puntero de pila (Libera el espacio reservado en la pila)
  jr $ra            # Retorna (Salta a la dirección guardada en $ra, retornando de la función)
```

## 6. Instrucción JAL (Jump and Link)

**Formato de la instrucción JAL:**

```
SPECIAL
000011 Jump_address
```

**Descripción:**

- `Reg[$ra] ← PC + 4` (Guarda la dirección de la siguiente instrucción (PC + 4) en el registro $ra)
- `PC ← PC(31:28) & Jump_address & 00` (Carga la nueva dirección en el PC, concatenando partes del PC actual con la dirección de salto)  
    **a) Diagrama esquemático del procesador:**  
    *(Nuevamente, no puedo dibujar el diagrama. Las modificaciones principales son:
- La salida de la ALU (PC + 4) debe conectarse a una entrada del multiplexor que escribe en el banco de registros, específicamente para el registro `$ra`.
- La concatenación de `PC(31:28) & Jump_address & 00` debe implementarse con lógica cableada y conectarse a la entrada del multiplexor que selecciona la dirección del siguiente PC.
- La señal de control `PCSrc` debe tener una opción para seleccionar esta dirección concatenada.*)  
    **b) Señales de control:**
- **RegWrite:** 1 (Se escribe en el banco de registros, específicamente en $ra)
- **ALUSrc:** X (No importa, la ALU no se usa directamente para el cálculo del PC)
- **ALUOp:** XX (No importa, la ALU no se usa directamente para el cálculo del PC)
- **RegDst:** Debe tener un valor que seleccione `$ra` (registro 31) como el registro destino. (Indica que el registro destino es $ra)
- **MemWrite:** 0 (No se escribe en memoria)
- **MemRead:** 0 (No se lee de memoria)
- **MemtoReg:** Debe tener un valor que seleccione la salida de la ALU (PC + 4) para escribir en `$ra`. (Indica que el valor a escribir en $ra proviene de la ALU (PC+4))
- **PCSrc:** Debe tener un valor que seleccione la dirección concatenada (`PC(31:28) & Jump_address & 00`) como la fuente del PC. (Indica que la nueva dirección del PC es la concatenación de partes del PC actual y la dirección de salto)

## 7. Llamadas a Funciones Anidadas

**Funciones en C:**

```c
int suma (int a, int b) {
  int c;
  c = a+b;
  return c;
}

int example (int g, int h, int i, int j) {
  int f;
  f = suma(g,h) - suma(i,j);
  return f;
}
```

**Registros:**

- g -> `$a0` (Primer argumento de example)
- h -> `$a1` (Segundo argumento de example)
- i -> `$a2` (Tercer argumento de example)
- j -> `$a3` (Cuarto argumento de example)
- f -> `$s0` (Variable local de example, donde se guarda el resultado)

**Código MIPS:**

```assembly
example:
  addi $sp, $sp, -24  # Ajusta el puntero de pila (6 registros * 4 bytes) (Reserva espacio en la pila para 6 registros: $ra, $s0, $a2, $a3, $a4, $a5)
  sw $ra, 20($sp)  # Guarda $ra (Guarda la dirección de retorno de example)
  sw $s0, 16($sp)  # Guarda $s0 (Guarda el valor de $s0, que se usará para f)
  sw $a2, 12($sp)  # Guarda $a2 (Guarda el valor de $a2, ya que se usará para llamar a suma)
  sw $a3, 8($sp)   # Guarda $a3 (Guarda el valor de $a3, ya que se usará para llamar a suma)
  sw $a4, 4($sp)   # Guarda $a4 (Guarda el valor de $a4, que se usará para guardar el resultado de suma(g,h))
  sw $a5, 0($sp)   # Guarda $a5 (Guarda el valor de $a5, que se usará para guardar el resultado de suma(i,j))

  # Calcula suma(g, h)
  move $a0, $a0  # a = g (Prepara el primer argumento para suma)
  move $a1, $a1  # b = h (Prepara el segundo argumento para suma)
  jal suma       # Llama a suma (Llama a la función suma)
  move $a4, $v0  # Guarda el resultado de suma(g, h) en $a4 (Guarda el valor retornado por suma en $a4)

  # Calcula suma(i, j)
  move $a0, $a2  # a = i (Prepara el primer argumento para suma)
  move $a1, $a3  # b = j (Prepara el segundo argumento para suma)
  jal suma       # Llama a suma (Llama a la función suma)
  move $a5, $v0  # Guarda el resultado de suma(i, j) en $a5 (Guarda el valor retornado por suma en $a5)

  # Calcula f = suma(g, h) - suma(i, j)
  sub $s0, $a4, $a5  # f = $a4 - $a5 (Resta los resultados de las dos llamadas a suma y guarda en f ($s0))

  # Restaura los registros
  lw $ra, 20($sp)  # Restaura $ra (Restaura la dirección de retorno de example)
  lw $s0, 16($sp)  # Restaura $s0 (Restaura el valor original de $s0)
  lw $a2, 12($sp)  # Restaura $a2 (Restaura el valor original de $a2)
  lw $a3, 8($sp)   # Restaura $a3 (Restaura el valor original de $a3)
  lw $a4, 4($sp)   # Restaura $a4 (Restaura el valor original de $a4)
  lw $a5, 0($sp)   # Restaura $a5 (Restaura el valor original de $a5)
  addi $sp, $sp, 24  # Restaura el puntero de pila (Libera el espacio reservado en la pila)

  # Retorna
  jr $ra            # Retorna (Salta a la dirección guardada en $ra, retornando de la función)

suma:
  add $v0, $a0, $a1  # c = a + b (Suma los argumentos a y b, guarda el resultado en $v0)
  jr $ra            # Retorna (Salta a la dirección guardada en $ra, retornando de la función)
```

## 8. Función Factorial (Recursiva)

**Función en C:**

```c
int factorial (int n) {
  if (n < 1)
    return 1;
  else
    return (n * factorial(n-1));
}
```

**Registro:**

- n -> `$a0` (Argumento de la función factorial)

**Código MIPS:**

```assembly
factorial:
  addi $sp, $sp, -8   # Ajusta el puntero de pila para guardar $ra y $a0 (Reserva espacio en la pila para 2 registros: $ra y $a0)
  sw $ra, 4($sp)    # Guarda $ra (Guarda la dirección de retorno)
  sw $a0, 0($sp)    # Guarda $a0 (Guarda el valor del argumento n)

  slti $t0, $a0, 1   # $t0 = 1 si n < 1, 0 en caso contrario (Compara n con 1. Si n < 1, $t0 = 1; sino, $t0 = 0)
  bne $t0, $zero, base_case # Si n < 1, salta a base_case (Si n < 1, salta al caso base)

  addi $a0, $a0, -1   # n = n - 1 (Decrementa n para la llamada recursiva)
  jal factorial      # Llama recursivamente a factorial (Llama a la función factorial con n-1)
  lw $a0, 0($sp)    # Restaura el valor original de n (Restaura el valor original de n desde la pila)
  mul $v0, $a0, $v0   # $v0 = n * factorial(n-1) (Multiplica n por el resultado de factorial(n-1) y guarda en $v0)
  j end_factorial    # Salta al final (Salta a la etiqueta 'end_factorial')

base_case:
  addi $v0, $zero, 1  # Retorna 1 (Si n < 1, retorna 1)

end_factorial:
  lw $ra, 4($sp)    # Restaura $ra (Restaura la dirección de retorno)
  addi $sp, $sp, 8   # Restaura el puntero de pila (Libera el espacio reservado en la pila)
  jr $ra             # Retorna (Salta a la dirección guardada en $ra, retornando de la función)
```

## 9. Rango de Salto de `beq`

**Instrucción:** `beq $s0, $s1, L1`  
**a) Rango de direcciones posibles de salto:**

- Dirección de la instrucción: `0x0004C000` (Dirección donde se encuentra la instrucción beq)
- El campo _immediate_ en `beq` es de 16 bits, con signo, y representa el número de _palabras_ (no bytes) a saltar relativo a la siguiente instrucción. (El valor inmediato indica el desplazamiento en palabras)
- Rango: `-2^{15}` a `2^{15}-1` palabras. (El rango de desplazamiento es de -32768 a 32767 palabras)
- En bytes: `-2^{15} * 4` a `(2^{15}-1) * 4` (Convierte el rango a bytes)
- Mínimo: `0x0004C000 + 4 + (-32768 * 4) = 0x0004C004 - 0x00020000 = 0x0002C004` (Calcula la dirección mínima de salto)
- Máximo: `0x0004C000 + 4 + (32767 * 4) = 0x0004C004 + 0x0001FFFC = 0x0006BFFC` (Calcula la dirección máxima de salto)
- Rango: `0x0002C004` a `0x0006BFFC` (El rango de direcciones de salto)  
    **b) Reemplazo con instrucciones para extender el rango:**

```assembly
bne $s0, $s1, L2  # Si ($s0 != $s1) salta a L2 (Si los registros $s0 y $s1 no son iguales, salta a la etiqueta L2)
j L1              # Salto incondicional a L1 (Si los registros $s0 y $s1 son iguales, salta a la etiqueta L1)
L2:               # Etiqueta L2
```

**c) Rango de direcciones posibles de salto (con reemplazo):**

- El rango de la instrucción `j` es mucho mayor (26 bits), cubriendo casi todo el espacio de direcciones. Está limitado por la necesidad de que la dirección esté dentro del mismo bloque de 256MB que la instrucción `j`. En la práctica, esto permite saltos a casi cualquier dirección dentro del programa. (La instrucción 'j' permite saltar a cualquier dirección dentro de un bloque de 256MB, lo que extiende significativamente el rango de salto)
