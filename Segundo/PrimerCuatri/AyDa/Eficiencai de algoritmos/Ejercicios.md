Okay, aquí tienes la resolución de los ejercicios nuevamente, con explicaciones más detalladas paso a paso, ejemplos concretos y la corrección/clarificación del ejercicio 3, todo formateado para Obsidian.

```markdown
# Ejercicios Resueltos: Análisis de Complejidad y Recursión (Detallado)

Basado en los conceptos de [[Eficiencia de algoritmos]] y [[Tecnica diseño de algoritmos]].

---

## Parte 1: Análisis de Complejidad (Notación Big-Oh)

### 1. Funcion1

```cpp
unsigned int Funcion1 (unsigned int i){
    // Paso 1: Caso Base
    if (i <= 1)
        return 1; // Costo constante: c1 -> O(1)
    // Paso 2: Caso Recursivo
    else {
        // Paso 2a: Llamada recursiva
        unsigned int aux = Funcion1 (i-1); // Costo: T(i-1)
        // Paso 2b: Trabajo adicional (multiplicación, retorno)
        return 2 * aux; // Costo constante: c2 -> O(1)
    }
}
```

*   **Análisis Paso a Paso:**
    1.  **Identificar Costos:**
        *   Caso Base (i <= 1): Costo constante $c_1$.
        *   Caso Recursivo (i > 1): Costo de la llamada recursiva $T(i-1)$ más el costo del trabajo adicional $c_2$.
    2.  **Ecuación de Recurrencia:**
        *   $T(i) = c_1$ si $i \le 1$
        *   $T(i) = T(i-1) + c_2$ si $i > 1$
    3.  **Resolver por Expansión (Sustitución Iterativa):**
        *   $T(i) = T(i-1) + c_2$
        *   $T(i) = [T(i-2) + c_2] + c_2 = T(i-2) + 2c_2$  *(Sustituimos T(i-1))*
        *   $T(i) = [T(i-3) + c_2] + 2c_2 = T(i-3) + 3c_2$ *(Sustituimos T(i-2))*
        *   ... (Después de $k$ pasos) ...
        *   $T(i) = T(i-k) + k \cdot c_2$
    4.  **Llegar al Caso Base:** Queremos que $i-k = 1$ (o 0, da igual asintóticamente). Esto ocurre cuando $k = i-1$. Sustituimos $k = i-1$:
        *   $T(i) = T(1) + (i-1)c_2$
        *   $T(i) = c_1 + (i-1)c_2 = c_1 + i c_2 - c_2$
    5.  **Determinar Orden (Big-Oh):** La expresión $c_1 + i c_2 - c_2$ es una función lineal de $i$. Los términos constantes ($c_1, -c_2$) y el coeficiente constante ($c_2$) no afectan el orden de magnitud.
        *   $T(i) \in O(i)$.

*   **Ejemplo: `Funcion1(3)`**
    1.  `Funcion1(3)` llama a `Funcion1(2)` (costo $T(2) + c_2$)
    2.  `Funcion1(2)` llama a `Funcion1(1)` (costo $T(1) + c_2$)
    3.  `Funcion1(1)` retorna 1 (costo $c_1$)
    4.  `Funcion1(2)` recibe 1, retorna $2*1=2$ (costo total $c_1 + c_2$)
    5.  `Funcion1(3)` recibe 2, retorna $2*2=4$ (costo total $(c_1 + c_2) + c_2 = c_1 + 2c_2$)
    *   El número de llamadas es 3 (proporcional a $i=3$). El costo total es lineal en $i$.

*   **Complejidad Temporal:** $T(i) \in O(i)$.

### 2. Funcion2 y Comparación

```cpp
unsigned int Funcion2 (unsigned int i){
    // Paso 1: Caso Base
    if (i <= 1)
        return 1; // Costo constante: c1 -> O(1)
    // Paso 2: Caso Recursivo
    else
        // Paso 2a: Dos llamadas recursivas + suma
        return Funcion2 (i-1) + Funcion2 (i-1); // Costo: T(i-1) + T(i-1) + c2
}
```

*   **Análisis Paso a Paso:**
    1.  **Identificar Costos:**
        *   Caso Base (i <= 1): Costo constante $c_1$.
        *   Caso Recursivo (i > 1): Costo de dos llamadas recursivas $T(i-1) + T(i-1)$ más el costo de la suma $c_2$.
    2.  **Ecuación de Recurrencia:**
        *   $T(i) = c_1$ si $i \le 1$
        *   $T(i) = 2T(i-1) + c_2$ si $i > 1$
    3.  **Resolver por Expansión:**
        *   $T(i) = 2T(i-1) + c_2$
        *   $T(i) = 2[2T(i-2) + c_2] + c_2 = 4T(i-2) + 2c_2 + c_2$
        *   $T(i) = 4[2T(i-3) + c_2] + 2c_2 + c_2 = 8T(i-3) + 4c_2 + 2c_2 + c_2$
        *   ... (Después de $k$ pasos) ...
        *   $T(i) = 2^k T(i-k) + c_2 \sum_{j=0}^{k-1} 2^j$
    4.  **Llegar al Caso Base:** Ocurre cuando $k = i-1$.
        *   $T(i) = 2^{i-1} T(1) + c_2 (2^{i-1} - 1)$ *(Usando la fórmula de la suma geométrica $\sum_{j=0}^{k-1} a^j = (a^k - 1)/(a-1)$ con $a=2$)*
        *   $T(i) = 2^{i-1} c_1 + c_2 2^{i-1} - c_2 = (c_1 + c_2) 2^{i-1} - c_2$
    5.  **Determinar Orden (Big-Oh):** La expresión es dominada por el término $2^{i-1}$, que es exponencial en $i$.
        *   $T(i) \in O(2^i)$.

*   **Ejemplo: `Funcion2(3)`**
    *   `Funcion2(3)`
        *   Llama `Funcion2(2)` (1ra vez)
            *   Llama `Funcion2(1)` (1ra vez) -> retorna 1
            *   Llama `Funcion2(1)` (2da vez) -> retorna 1
            *   Retorna 1 + 1 = 2
        *   Llama `Funcion2(2)` (2da vez)
            *   Llama `Funcion2(1)` (3ra vez) -> retorna 1
            *   Llama `Funcion1(1)` (4ta vez) -> retorna 1
            *   Retorna 1 + 1 = 2
        *   Retorna 2 + 2 = 4
    *   Observa cómo `Funcion2(1)` se calcula 4 veces y `Funcion2(2)` se calcula 2 veces. El número de llamadas crece exponencialmente (árbol binario completo de altura $i-1$).

*   **Complejidad Temporal:** $T(i) \in O(2^i)$.
*   **Comparación con Funcion1:** $O(2^i)$ es mucho mayor que $O(i)$. `Funcion2` es ineficiente debido al recálculo de subproblemas idénticos (subproblemas superpuestos).

### 3. funcion

```cpp
int funcion (unsigned int x) {
    // Paso 1: Caso Base
    if (x == 0)
        return(1); // Costo constante: c1 -> O(1)
    // Paso 2: Caso Recursivo
    else
        // Paso 2a: Llamada recursiva
        // Paso 2b: Multiplicación, Llamada a F, Retorno
        return F (3 * funcion (x-1) ); // F  O(k)
}
```

*   **Análisis Paso a Paso:**
    1.  **Interpretación de `F \in O(k)`:** Como se discutió, la notación es ambigua. Para que el resultado sea $O(x)$ (como sugiere el contexto típico de estos ejercicios y la corrección indicada), debemos asumir que `F` realiza una cantidad de trabajo **constante**, independiente del valor de su argumento. Es decir, asumimos $F \in O(1)$. Si $F$ dependiera del valor `3 * funcion(x-1)`, la complejidad sería exponencial y mucho más compleja.
    2.  **Identificar Costos (asumiendo F es O(1)):**
        *   Caso Base (x == 0): Costo constante $c_1$.
        *   Caso Recursivo (x > 0): Costo de la llamada recursiva $T(x-1)$ más el costo del trabajo adicional (multiplicación, llamada a F, retorno) que es constante $c_2$.
    3.  **Ecuación de Recurrencia:**
        *   $T(x) = c_1$ si $x = 0$
        *   $T(x) = T(x-1) + c_2$ si $x > 0$
    4.  **Resolver por Expansión:** Esta es exactamente la misma recurrencia que `Funcion1`.
        *   $T(x) = T(x-1) + c_2$
        *   $T(x) = T(x-k) + k \cdot c_2$
    5.  **Llegar al Caso Base:** Ocurre cuando $k = x$.
        *   $T(x) = T(0) + x \cdot c_2$
        *   $T(x) = c_1 + x c_2$
    6.  **Determinar Orden (Big-Oh):** La expresión $c_1 + x c_2$ es lineal en $x$.
        *   $T(x) \in O(x)$.

*   **Ejemplo: `funcion(2)` (asumiendo F es O(1))**
    1.  `funcion(2)` llama a `funcion(1)` (costo $T(1) + c_2$)
    2.  `funcion(1)` llama a `funcion(0)` (costo $T(0) + c_2$)
    3.  `funcion(0)` retorna 1 (costo $c_1$)
    4.  `funcion(1)` recibe 1, calcula `3*1=3`, llama a `F(3)`, retorna el resultado de F (costo total $c_1 + c_2$)
    5.  `funcion(2)` recibe resultado de F, calcula `3 * resultado_F`, llama a `F` con ese nuevo valor, retorna el resultado de F (costo total $(c_1 + c_2) + c_2 = c_1 + 2c_2$)
    *   El número de llamadas es 3 (proporcional a $x=2$). El costo total es lineal en $x$.

*   **Complejidad Temporal (bajo suposición F es O(1)):** $T(x) \in O(x)$.

### 4. dibujarLineas

```cpp
void dibujarLineas( int i, int j, unsigned int altura) {
    // Paso 1: Condición de parada (implícita para altura == 0)
    if (altura != 0) { // Costo O(1)
        // Paso 2: Trabajo no recursivo
        int m = ( i + j ) / 2 ; // Costo O(1)
        trazar (m, altura); // Costo O(altura) según enunciado
        // Total trabajo no recursivo: O(1) + O(altura) = O(altura) = c2 * altura

        // Paso 3: Llamadas recursivas
        dibujarLineas (i, m, altura - 1); // Costo T(altura-1)
        dibujarLineas (m, j, altura - 1); // Costo T(altura-1)
    }
    // Caso base (altura == 0): Costo constante c1 -> O(1)
}
```

*   **Análisis Paso a Paso:**
    1.  **Parámetro de Tamaño:** $n = altura$.
    2.  **Identificar Costos:**
        *   Caso Base (n == 0): $c_1$.
        *   Caso Recursivo (n > 0): Costo de dos llamadas $2T(n-1)$ más el costo del trabajo no recursivo $c_2 n$.
    3.  **Ecuación de Recurrencia:**
        *   $T(n) = c_1$ si $n = 0$
        *   $T(n) = 2T(n-1) + c_2 n$ si $n > 0$
    4.  **Resolver por Expansión:**
        *   $T(n) = 2T(n-1) + c_2 n$
        *   $T(n) = 2[2T(n-2) + c_2(n-1)] + c_2 n = 4T(n-2) + 2c_2(n-1) + c_2 n$
        *   $T(n) = 4[2T(n-3) + c_2(n-2)] + 2c_2(n-1) + c_2 n = 8T(n-3) + 4c_2(n-2) + 2c_2(n-1) + c_2 n$
        *   ... (Después de $k$ pasos) ...
        *   $T(n) = 2^k T(n-k) + c_2 [2^{k-1}(n-(k-1)) + ... + 2^1(n-1) + 2^0 n]$
        *   $T(n) = 2^k T(n-k) + c_2 \sum_{j=0}^{k-1} 2^j (n-j)$
    5.  **Llegar al Caso Base:** Ocurre cuando $k = n$.
        *   $T(n) = 2^n T(0) + c_2 \sum_{j=0}^{n-1} 2^j (n-j)$
        *   $T(n) = 2^n c_1 + c_2 \sum_{j=0}^{n-1} (n 2^j - j 2^j)$
        *   $T(n) = 2^n c_1 + c_2 [n \sum_{j=0}^{n-1} 2^j - \sum_{j=0}^{n-1} j 2^j]$
        *   Sabemos que $\sum_{j=0}^{n-1} 2^j = 2^n - 1$.
        *   La suma $\sum_{j=0}^{n-1} j 2^j$ es un poco más compleja, pero se puede demostrar que es $(n-2)2^n + 2$.
        *   $T(n) = 2^n c_1 + c_2 [n(2^n - 1) - ((n-2)2^n + 2)]$
        *   $T(n) = 2^n c_1 + c_2 [n 2^n - n - n 2^n + 2 \cdot 2^n - 2]$
        *   $T(n) = 2^n c_1 + c_2 [2 \cdot 2^n - n - 2] = c_1 2^n + c_2 2^{n+1} - c_2 n - 2c_2$
    6.  **Determinar Orden (Big-Oh):** El término dominante es $2^{n+1}$ (o $2^n$), que es exponencial.
        *   $T(n) \in O(2^n)$.

*   **Ejemplo: `dibujarLineas(0, 4, 2)` (n=2)**
    1.  `dibujarLineas(0, 4, 2)`:
        *   m = 2, trazar(2, 2) (costo $c_2 * 2$)
        *   Llama `dibujarLineas(0, 2, 1)`
        *   Llama `dibujarLineas(2, 4, 1)`
    2.  `dibujarLineas(0, 2, 1)`:
        *   m = 1, trazar(1, 1) (costo $c_2 * 1$)
        *   Llama `dibujarLineas(0, 1, 0)` -> retorna (costo $c_1$)
        *   Llama `dibujarLineas(1, 2, 0)` -> retorna (costo $c_1$)
        *   Costo total: $c_2 * 1 + T(0) + T(0) = c_2 + 2c_1$
    3.  `dibujarLineas(2, 4, 1)`:
        *   m = 3, trazar(3, 1) (costo $c_2 * 1$)
        *   Llama `dibujarLineas(2, 3, 0)` -> retorna (costo $c_1$)
        *   Llama `dibujarLineas(3, 4, 0)` -> retorna (costo $c_1$)
        *   Costo total: $c_2 * 1 + T(0) + T(0) = c_2 + 2c_1$
    4.  Costo total para `dibujarLineas(0, 4, 2)`:
        *   $T(2) = (c_2 * 2) + T(1) + T(1)$
        *   $T(2) = 2c_2 + (c_2 + 2c_1) + (c_2 + 2c_1) = 4c_2 + 4c_1$
    *   Verificando la fórmula: $c_1 2^2 + c_2 2^{2+1} - c_2(2) - 2c_2 = 4c_1 + 8c_2 - 2c_2 - 2c_2 = 4c_1 + 4c_2$. Coincide. El costo crece como $O(2^n)$.

*   **Complejidad Temporal:** $T(altura) \in O(2^{altura})$.

### 5. f y f2, Mejora e Implementación

**Análisis de `f2`:** (Sin cambios)
*   **Complejidad `f2(a, b)`:** $O(a \cdot b)$.

**Análisis de `f` (Original):**

```cpp
int f (int m) {
    if (m <= 1) return m; // O(1)
    else {
        int aux = f2 (m, 80000); // Costo O(m * 80000) = O(m)
        return f (m-1) + aux + f (m-1); // Costo 2*T(m-1) + O(m)
    }
}
```

*   **Análisis Paso a Paso:**
    1.  **Identificar Costos:**
        *   Caso Base (m <= 1): $c_1$.
        *   Caso Recursivo (m > 1): Costo de `f2` ($c_2 m$) + Costo de dos llamadas $2T(m-1)$ + Costo de sumas ($c_3$).
    2.  **Ecuación de Recurrencia:**
        *   $T(m) = c_1$ si $m \le 1$
        *   $T(m) = 2T(m-1) + c_2 m + c_3 = 2T(m-1) + O(m)$ si $m > 1$
    3.  **Resolver por Expansión:** Esta es la misma forma de recurrencia que `dibujarLineas`.
        *   $T(m) = 2T(m-1) + \Theta(m)$ (Usando Theta porque O(m) es tanto cota superior como inferior aquí)
        *   La solución es $T(m) \in O(2^m)$. El término $O(m)$ es dominado por el crecimiento exponencial de las llamadas.
*   **Ejemplo: `f(3)` (Original)**
    *   `f(3)`:
        *   `f2(3, 80k)` -> $O(3)$
        *   Llama `f(2)` (1ra vez)
            *   `f2(2, 80k)` -> $O(2)$
            *   Llama `f(1)` (1ra vez) -> retorna 1
            *   Llama `f(1)` (2da vez) -> retorna 1
            *   Retorna $1 + aux_2 + 1$
        *   Llama `f(2)` (2da vez)
            *   `f2(2, 80k)` -> $O(2)$
            *   Llama `f(1)` (3ra vez) -> retorna 1
            *   Llama `f(1)` (4ta vez) -> retorna 1
            *   Retorna $1 + aux_2 + 1$
        *   Retorna $res\_f2\_1 + aux_3 + res\_f2\_2$
    *   Nuevamente, vemos el patrón de llamadas exponenciales.
*   **Complejidad Temporal `f` (Original):** $T(m) \in O(2^m)$.

**Mejora e Implementación (`f_mejorada`):**

```cpp
int f_mejorada (int m) {
    if (m <= 1) {
        return m; // O(1)
    } else {
        int aux = f2 (m, 80000); // Costo O(m)
        // Calcular f(m-1) UNA SOLA VEZ
        int resultado_recursivo = f_mejorada(m-1); // Costo T(m-1)
        // Reutilizar el resultado
        return resultado_recursivo + aux + resultado_recursivo; // Costo O(1)
    }
}
```

*   **Análisis Paso a Paso (`f_mejorada`):**
    1.  **Identificar Costos:**
        *   Caso Base (m <= 1): $c_1$.
        *   Caso Recursivo (m > 1): Costo de `f2` ($c_2 m$) + Costo de **una** llamada $T(m-1)$ + Costo de sumas ($c_3$).
    2.  **Ecuación de Recurrencia:**
        *   $T(m) = c_1$ si $m \le 1$
        *   $T(m) = T(m-1) + c_2 m + c_3 = T(m-1) + O(m)$ si $m > 1$
    3.  **Resolver por Expansión:**
        *   $T(m) = T(m-1) + c_2 m + c_3$
        *   $T(m) = [T(m-2) + c_2(m-1) + c_3] + c_2 m + c_3 = T(m-2) + c_2((m-1)+m) + 2c_3$
        *   $T(m) = [T(m-3) + c_2(m-2) + c_3] + c_2((m-1)+m) + 2c_3 = T(m-3) + c_2((m-2)+(m-1)+m) + 3c_3$
        *   ... (Después de $k$ pasos) ...
        *   $T(m) = T(m-k) + c_2 \sum_{j=0}^{k-1} (m-j) + k c_3$
    4.  **Llegar al Caso Base:** Ocurre cuando $k = m-1$.
        *   $T(m) = T(1) + c_2 \sum_{j=0}^{m-2} (m-j) + (m-1) c_3$
        *   La suma $\sum_{j=0}^{m-2} (m-j)$ es la suma de $m + (m-1) + ... + 2$.
        *   $\sum_{j=2}^{m} j = (\sum_{j=1}^{m} j) - 1 = \frac{m(m+1)}{2} - 1$.
        *   $T(m) = c_1 + c_2 (\frac{m(m+1)}{2} - 1) + (m-1) c_3$
    5.  **Determinar Orden (Big-Oh):** La expresión es dominada por el término $m^2/2$.
        *   $T(m) \in O(m^2)$.

*   **Ejemplo: `f_mejorada(3)`**
    1.  `f_mejorada(3)`:
        *   `f2(3, 80k)` -> $O(3)$
        *   Llama `f_mejorada(2)`
            *   `f2(2, 80k)` -> $O(2)$
            *   Llama `f_mejorada(1)` -> retorna 1
            *   Calcula $1 + aux_2 + 1$. Retorna este valor (llamémoslo `res2`).
        *   Calcula `res2 + aux_3 + res2`. Retorna este valor.
    *   Solo hay una cadena lineal de llamadas: 3 -> 2 -> 1. En cada llamada se hace trabajo $O(m)$.

*   **Complejidad Temporal `f_mejorada`:** $T(m) \in O(m^2)$. La mejora es significativa de $O(2^m)$ a $O(m^2)$.

---

## Parte 2: Seguimiento y Análisis de `potencia`

```cpp
// Líneas numeradas para el seguimiento
double potencia (double base, unsigned int exp) {
1.  if (exp == 0)
2.      return 1.0; // O(1)
3.  if (exp%2 == 1) // exp es impar? O(1)
4.      return base * potencia (base, exp-1); // T(exp-1) + O(1)
5.  else // exp es par
6.  {
7.      double aux = potencia (base, exp/2); // T(exp/2) + O(1)
8.      return aux * aux; // O(1)
9.  }
10. } // Fin de la función
```

### a) Seguimiento para `potencia(base = 2.0, exp = 7)` (Sin cambios, ya detallado)

| Call# | `base` | `exp` | `aux` | RetAddr | RetVal | Notas                                                              |
| :---- | :----- | :---- | :---- | :------ | :----- | :----------------------------------------------------------------- |
| 1     | 2.0    | 7     | -     | (main)  | ?      | L1: F, L3: T (7 impar). Llama `potencia(2, 6)` en L4.              |
| 2     | 2.0    | 6     | -     | L4 (#1) | ?      | L1: F, L3: F (6 par). Llama `potencia(2, 3)` en L7.                |
| 3     | 2.0    | 3     | -     | L7 (#2) | ?      | L1: F, L3: T (3 impar). Llama `potencia(2, 2)` en L4.              |
| 4     | 2.0    | 2     | -     | L4 (#3) | ?      | L1: F, L3: F (2 par). Llama `potencia(2, 1)` en L7.                |
| 5     | 2.0    | 1     | -     | L7 (#4) | ?      | L1: F, L3: T (1 impar). Llama `potencia(2, 0)` en L4.              |
| 6     | 2.0    | 0     | -     | L4 (#5) | 1.0    | L1: T. Retorna 1.0 en L2.                                          |
| 5     | 2.0    | 1     | -     | L7 (#4) | 2.0    | Recibe 1.0 de #6. Retorna `base * 1.0 = 2.0 * 1.0 = 2.0` en L4.    |
| 4     | 2.0    | 2     | 2.0   | L4 (#3) | 4.0    | Recibe 2.0 de #5. L7: `aux = 2.0`. Retorna `aux*aux = 4.0` en L8.   |
| 3     | 2.0    | 3     | -     | L7 (#2) | 8.0    | Recibe 4.0 de #4. Retorna `base * 4.0 = 2.0 * 4.0 = 8.0` en L4.    |
| 2     | 2.0    | 6     | 8.0   | L4 (#1) | 64.0   | Recibe 8.0 de #3. L7: `aux = 8.0`. Retorna `aux*aux = 64.0` en L8.  |
| 1     | 2.0    | 7     | -     | (main)  | 128.0  | Recibe 64.0 de #2. Retorna `base * 64.0 = 2.0 * 64.0 = 128.0` en L4. |

### b) Complejidad Temporal `potencia`

*   **Análisis Paso a Paso:** Sea $n = exp$.
    1.  **Identificar Costos:**
        *   Caso Base (n == 0): $O(1)$.
        *   Caso n impar: $T(n) = T(n-1) + O(1)$.
        *   Caso n par: $T(n) = T(n/2) + O(1)$.
    2.  **Observar la Reducción del Problema:**
        *   Si $n$ es par, se reduce a la mitad en un paso: $n \to n/2$.
        *   Si $n$ es impar, se reduce a $n-1$ (que es par) y luego a $(n-1)/2$. En dos pasos, se reduce aproximadamente a la mitad: $n \to n-1 \to (n-1)/2$.
        *   En cualquier caso, el exponente se reduce aproximadamente a la mitad en uno o dos pasos recursivos.
    3.  **Relación con Logaritmo:** El número de veces que podemos dividir $n$ por 2 (o reducirlo aproximadamente a la mitad) hasta llegar a 1 o 0 es $\log_2 n$.
    4.  **Costo por Paso:** Cada paso recursivo (sea par o impar) realiza una cantidad constante de trabajo $O(1)$ además de la llamada recursiva.
    5.  **Costo Total:** El número total de llamadas recursivas es proporcional a $\log n$. Como cada llamada hace trabajo $O(1)$, el costo total es $O(\log n)$.
*   **Complejidad Temporal:** $T(exp) \in O(\log exp)$.

### c) Comparación con Potencia Iterativa (Sin cambios)

*   **Potencia Iterativa Simple:** $O(exp)$.
*   **Comparación:** $O(\log exp)$ (recursiva eficiente) es mucho mejor que $O(exp)$ (iterativa simple) para `exp` grandes.

---
```