Okay, aquí tienes la nota [[Tecnica diseño de algoritmos]] reorganizada y formateada en Markdown para Obsidian, buscando una estructura clara y agradable a la vista.


# [[Tecnica diseño de algoritmos]]

El curso aborda técnicas específicas para diseñar algoritmos eficientes, complementando el análisis de eficiencia y el uso de Tipos de Datos Abstractos (TDAs). Las técnicas principales cubiertas son:

*   Divide y Conquista (D&C)
*   Algoritmos Greedy (Voraces)
*   Programación Dinámica (DP)

---

# 1. Divide y Conquista (D&C)

## Idea Central

La técnica D&C sigue tres pasos fundamentales:

1.  **Dividir (Divide):** Si el problema es complejo, se descompone en subproblemas *más pequeños* del *mismo tipo*.
2.  **Conquistar (Conquer):** Se resuelven los subproblemas recursivamente. Si un subproblema es lo suficientemente simple (caso base), se resuelve directamente.
3.  **Combinar (Combine):** Se combinan las soluciones de los subproblemas para obtener la solución del problema original.

*Nota: Es una estrategia muy natural y potente. Piensa en cómo ordenarías una pila grande de exámenes: podrías dividirla en dos, ordenar cada mitad por separado (recursivamente) y luego mezclar las dos mitades ya ordenadas.*

## Esquema Algorítmico General

```pseudocode
tipoResultado DivideyConquista (tipoDato X) {
    tipoDato x1, x2, ..., xk;
    if (simple(x)) { // Caso Base
        return soluciónDirecta(x);
    } else { // Caso Recursivo
        // 1. Dividir
        x1 = Parte1(x);
        x2 = Parte2(x);
        ...
        xk = Partek(x);

        // 2. Conquistar (llamadas recursivas) y 3. Combinar
        return Combinar(
            DivideyConquista(x1),
            DivideyConquista(x2),
            ...
            DivideyConquista(xk)
        );
    }
}
```

*   **Notas:**
    *   `simple(x)`: Verifica si la instancia `x` es un caso base.
    *   `soluciónDirecta(x)`: Resuelve el caso base.
    *   `Parte1...Partek`: Funciones que dividen el problema `x` en `k` subproblemas `x1...xk`.
    *   `Combinar`: Función que une las soluciones de los subproblemas.
    *   Si $k=1$, se llama **esquema de reducción** (el problema se reduce a un solo subproblema más pequeño).

## Consideraciones para la Eficiencia

*   **Subproblemas Disjuntos:** Idealmente, los subproblemas no se solapan o, si lo hacen, no se resuelve el mismo subproblema idéntico múltiples veces en ramas distintas de la recursión (esto es más relevante en Programación Dinámica).
*   **Reducción de Tamaño:** El tamaño de los subproblemas debe ser una fracción del tamaño original para asegurar que la recursión termine y sea eficiente.
*   **Balanceo:** Es preferible dividir en subproblemas de tamaño similar (balanceados). Dividir en uno muy grande y uno muy pequeño suele ser menos eficiente.
*   **Eficiencia de Dividir y Combinar:** Las funciones `Parte` y `Combinar` deben ser eficientes (generalmente, más rápidas que resolver el problema original directamente). Su complejidad afecta significativamente la complejidad total.

## Ejemplos Clásicos

### Torres de Hanoi
*   **Divide:** Mover $n$ discos se divide en mover $n-1$ discos, mover 1 disco, mover $n-1$ discos ($k=2$).
*   **Combina:** La secuencia de movimientos.
*   **Complejidad:** $T(n) = 2T(n-1) + O(1) \implies O(2^n)$.

### Búsqueda Binaria
*   **Divide:** Compara con el medio y reduce el problema a buscar en *una* mitad ($k=1$, reducción).
*   **Combina:** Trivial (el resultado del subproblema es el resultado final).
*   **Complejidad:** $T(m) = T(m/2) + O(1) \implies O(\log m)$.

## Ejemplo: Ordenamiento Mergesort

### Idea
1.  **Dividir:** Si la lista tiene más de un elemento, divídela en dos mitades (izquierda y derecha) de tamaño aproximadamente igual.
2.  **Conquistar:** Ordena recursivamente la mitad izquierda y la mitad derecha usando Mergesort.
3.  **Combinar:** Mezcla (merge) las dos mitades ya ordenadas para producir la lista ordenada final.

*Nota: La clave es que mezclar dos listas *ya ordenadas* es una operación eficiente.*

### Función `merge` (Combinar)
*   Toma dos sub-arreglos ordenados y los combina en un solo arreglo ordenado.
*   Utiliza índices para recorrer las listas, comparando elementos y copiando el menor.
*   **Complejidad de `merge`:** Si las dos mitades tienen un total de $m$ elementos, `merge` es $O(m)$ (lineal).

### Función `mergesort` (Recursiva)
```cpp
void mergesort (int A[], unsigned int inicio, unsigned int fin) {
    if (inicio < fin) { // Condición de parada: 0 o 1 elemento
        unsigned int mitad = (inicio + fin) / 2; // 1. Dividir
        mergesort(A, inicio, mitad); // 2. Conquistar (izquierda)
        mergesort(A, mitad + 1, fin); // 2. Conquistar (derecha)
        merge(A, inicio, mitad, fin); // 3. Combinar
    }
}
```

### Análisis de Complejidad de Mergesort
*   **Dividir:** $O(1)$.
*   **Conquistar:** $2T(n/2)$.
*   **Combinar:** $O(n)$.
*   **Ecuación de Recurrencia:** $T(n) = 2T(n/2) + O(n)$, $T(1) = O(1)$.
*   **Solución:** $T(n) \in O(n \log n)$.

*Nota: Mergesort es muy eficiente ($O(n \log n)$ en todos los casos), pero requiere espacio adicional $O(n)$ para la mezcla.*

## Ejemplo: Problema del Sub-arreglo de Suma Máxima

### Problema
Dado un arreglo $A$ de números (positivos, negativos, cero), encontrar el sub-arreglo contiguo $A[i..j]$ cuya suma sea la máxima posible.
*Aplicación: Encontrar el mejor período para comprar/vender acciones.*

### Algoritmo Ingenuo
*   Probar todos los $\approx n^2/2$ sub-arreglos $A[i..j]$.
*   Calcular la suma de cada uno.
*   **Complejidad:** $O(n^3)$ o $O(n^2)$ (con suma eficiente).

### Algoritmo Divide y Conquista

1.  **Dividir:** Dividir $A[inicio..fin]$ en $A[inicio..mitad]$ y $A[mitad+1..fin]$.
2.  **Conquistar:** Encontrar recursivamente:
    *   $S_L$: Suma máxima en la mitad izquierda.
    *   $S_R$: Suma máxima en la mitad derecha.
3.  **Combinar:** Encontrar $S_M$: Suma máxima de un sub-arreglo que *cruza* el punto medio.
    *   Se calcula encontrando la max suma que termina en `mitad` y la max suma que empieza en `mitad+1`.
    *   **Esta parte se hace en tiempo $O(n)$**.
4.  **Resultado Final:** $\max(S_L, S_R, S_M)$.

*Nota: La clave es encontrar $S_M$ eficientemente en $O(n)$ en el paso de Combinar.*

### Pseudo-código `maximoSubarreglo` (D&C)
```pseudocode
// ENTRADA: Arreglo A, índices inicio, fin
// SALIDA: Tupla (inicioSol, finSol, sumaSol)
funcion maximoSubarreglo(A, inicio, fin):
  // CASO BASE
  si inicio == fin:
    retornar (inicio, fin, A[inicio])
  // CASO RECURSIVO
  sino:
    mitad = piso((inicio + fin) / 2)
    // 2. Conquistar
    (inicioIzq, finIzq, sumaIzq) = maximoSubarreglo(A, inicio, mitad)
    (inicioDer, finDer, sumaDer) = maximoSubarreglo(A, mitad + 1, fin)
    // 3. Combinar (Encontrar solución que cruza)
    (inicioMedia, finMedia, sumaMedia) = SolucionMedia(A, inicio, mitad, fin)
    // Determinar el máximo de las tres
    si (sumaIzq >= sumaDer) y (sumaIzq >= sumaMedia):
      retornar (inicioIzq, finIzq, sumaIzq)
    sino si (sumaDer >= sumaIzq) y (sumaDer >= sumaMedia):
      retornar (inicioDer, finDer, sumaDer)
    sino:
      retornar (inicioMedia, finMedia, sumaMedia)
```

### Pseudo-código `SolucionMedia`
```pseudocode
// ENTRADA: Arreglo A, índices inicio, mitad, fin
// SALIDA: Tupla (maxIzqIdx, maxDerIdx, sumaMedia)
funcion SolucionMedia(A, inicio, mitad, fin):
  // Barrido hacia la izquierda desde 'mitad'
  sumaIzq = -infinito; suma = 0; maxIdxIzq = mitad
  para i desde mitad hasta inicio decrementando 1:
    suma = suma + A[i]
    si suma > sumaIzq:
      sumaIzq = suma; maxIdxIzq = i

  // Barrido hacia la derecha desde 'mitad + 1'
  sumaDer = -infinito; suma = 0; maxIdxDer = mitad + 1
  para j desde mitad + 1 hasta fin incrementando 1:
    suma = suma + A[j]
    si suma > sumaDer:
      sumaDer = suma; maxIdxDer = j

  sumaMedia = sumaIzq + sumaDer
  retornar (maxIdxIzq, maxIdxDer, sumaMedia)
```
*Nota: `SolucionMedia` tiene complejidad $O(n)$ donde $n$ es el tamaño del sub-arreglo actual.*

### Análisis de Complejidad (D&C para Suma Máxima)
*   **Dividir:** $O(1)$.
*   **Conquistar:** $2T(n/2)$.
*   **Combinar:** $O(n)$ (debido a `SolucionMedia`).
*   **Ecuación de Recurrencia:** $T(n) = 2T(n/2) + O(n)$, $T(1) = O(1)$.
*   **Solución:** $T(n) \in O(n \log n)$.

*Nota: Mejora significativa sobre $O(n^2)$. Existe un algoritmo $O(n)$ (Kadane) usando DP, pero este es un buen ejemplo de D&C.*

## Limitaciones de Divide y Conquista: Fibonacci

*   **Problema:** Calcular `fib(n)`.
*   **Definición Recursiva:** `fib(n) = fib(n-1) + fib(n-2)`.
*   **Implementación Recursiva Directa (D&C):**
    ```cpp
    unsigned int fibonacci(unsigned int n) {
        if (n <= 1) return n;
        else return (fibonacci(n-1) + fibonacci(n-2));
    }
    ```
*   **¡Problema Grave!:** Recalcula los mismos subproblemas muchísimas veces (subproblemas superpuestos).
*   **Complejidad:** Exponencial ($O(\phi^n)$), muy ineficiente.
*   **Solución Iterativa (o DP):**
    ```cpp
    int fib (int n) {
        int i, f[n+1]; // O solo dos variables
        f[0] = 0; f[1] = 1;
        for (i=2; i<= n; i++)
            f[i]= f[i-1] + f[i-2];
        return f[n];
    }
    ```
*   **Complejidad Iterativa:** $O(n)$ tiempo, $O(n)$ o $O(1)$ espacio.

*Nota: Fibonacci ilustra por qué D&C falla con **subproblemas superpuestos**. La solución eficiente usa la idea de **Programación Dinámica**: calcular cada subproblema una sola vez.*

---

# 2. Técnicas de Diseño: Algoritmos Greedy ("Voraces")

## Idea Central

*   Construir una solución paso a paso.
*   En cada paso, tomar la decisión que parece **localmente óptima** (la más "prometedora").
*   Esperar que estas decisiones locales conduzcan a una solución **globalmente óptima**.
*   *Advertencia: No siempre funciona.* Se necesita una **prueba de optimalidad**.

## Características Comunes

*   **Función de Selección:** Criterio para elegir el "mejor" elemento/opción.
*   **Comprobación de Factibilidad:** Asegurar que la elección mantiene la solución válida.
*   **Función Objetivo:** Cantidad a maximizar o minimizar.
*   **Pre-procesamiento:** A menudo requiere ordenar los datos.

## Ejemplo 1: Programación de Tareas (Minimizar Tiempo Total de Espera)

*   **Problema:** Atender $n$ clientes con tiempos de servicio $t_i$. Minimizar $\sum (\text{tiempo del cliente } i \text{ en el sistema})$.
*   **Estrategia Greedy:** Atender siempre al cliente con el **tiempo de servicio más corto** ($t_i$ mínimo). (SPT: Shortest Processing Time first).
*   **Ejemplo:** Tiempos {5, 3, 10}. Orden Greedy <3, 5, 10>. Tiempos en sistema: 3, (3+5), (3+5+10). Total = 3 + 8 + 18 = 29. (Este es el mínimo).
*   **Optimalidad:** Sí, SPT es óptima para este problema.
*   **Complejidad:** $O(n \log n)$ (ordenar) + $O(n)$ (construir) = $O(n \log n)$.

## Ejemplo 2: Problema de la Mochila (Versión Fraccionaria)

*   **Problema:** $n$ objetos (peso $p_i$, beneficio $b_i$). Mochila capacidad $M$. Se pueden tomar fracciones $x_i$ ($0 \le x_i \le 1$). Maximizar $\sum b_i x_i$ sujeto a $\sum p_i x_i \le M$.
*   **Estrategia Greedy:** Calcular relación beneficio/peso ($v_i = b_i / p_i$). Considerar objetos en orden **decreciente** de $v_i$. Llenar la mochila con los de mayor $v_i$.
*   **Ejemplo:** M=20, Objetos (b, p): (25, 18), (24, 15), (15, 10).
    *   Relaciones v: (1.39), (1.6), (1.5). Orden Greedy: Obj 2 (v=1.6), Obj 3 (v=1.5), Obj 1 (v=1.39).
    *   Llenado: Tomar todo Obj 2 (p=15, b=24). Resta M=5. Tomar $x_3 = 5/10 = 0.5$ de Obj 3 (p=5, b=7.5). Resta M=0.
    *   Solución: $x_1=0, x_2=1, x_3=0.5$. Beneficio = 24 + 7.5 = 31.5.
*   **Optimalidad:** Sí, para la versión *fraccionaria*.
*   **Complejidad:** $O(n \log n)$ (ordenar) + $O(n)$ (llenar) = $O(n \log n)$.

## Ejemplo 3: Ordenamiento Secuencial de Tareas con Plazos

*   **Problema:** $n$ tareas (duración 1), ganancia $g_i$, plazo $d_i$. Maximizar ganancia total de tareas completadas a tiempo.
*   **Estrategia Greedy:** Considerar tareas en orden **decreciente de ganancia** ($g_i$). Añadir tarea si el conjunto resultante sigue siendo **factible**.
*   **Comprobación de Factibilidad:** Un conjunto $J$ es factible si sus tareas se pueden ordenar $\sigma = \langle r_1, \dots, r_k \rangle$ tal que $r_q$ se completa en tiempo $q$ y $d_{r_q} \ge q$ para todo $q$.
*   **Ejemplo:** n=4; g=(100,10,15,27); d=(2,1,2,1).
    *   Orden por ganancia: T1(100,2), T4(27,1), T3(15,2), T2(10,1).
    *   1. Añadir T1. J={1}. Factible (<1>). G=100.
    *   2. Añadir T4. J={1, 4}. Factible (<4, 1>). G=127.
    *   3. Añadir T3. J={1, 4, 3}. No factible (3 tareas, plazos {2,1,2}). Descartar T3.
    *   4. Añadir T2. J={1, 4, 2}. No factible (3 tareas, plazos {2,1,1}). Descartar T2.
    *   Solución: {1, 4}. Ganancia = 127.
*   **Optimalidad:** Sí, esta estrategia es óptima.
*   **Complejidad:** $O(n \log n)$ (ordenar) + $n \times \text{CostoFactibilidad}$.
    *   Si Factibilidad es $O(n^2)$ (simple), total $O(n^3)$.
    *   Si Factibilidad es $O(n)$ (con Union-Find), total $O(n \log n)$.

---

# 3. Técnicas de Diseño: Programación Dinámica (DP)

## Idea Central

*   Técnica para resolver problemas descomponiéndolos en **subproblemas superpuestos**.
*   Resuelve cada subproblema **una sola vez** y guarda su resultado (memoization o tabla).
*   Combina soluciones de subproblemas para obtener la solución final.
*   Requiere **Subestructura Óptima:** Solución óptima global contiene soluciones óptimas a subproblemas.

## DP vs. Divide y Conquista

*   **D&C:** Eficiente si los subproblemas son *independientes*. Ineficiente si hay superposición (recalcula).
*   **DP:** Diseñada para *subproblemas superpuestos*. Evita recalcular almacenando resultados.

## Pasos Generales

1.  **Caracterizar la estructura de una solución óptima** (Identificar subestructura óptima).
2.  **Definir recursivamente el valor de una solución óptima** (Ecuación de recurrencia).
3.  **Calcular el valor de forma ascendente (bottom-up)** (Llenar tabla DP).
4.  **(Opcional) Construir la solución óptima** (Usar tabla auxiliar o rastrear decisiones).

## Ejemplo 1: Multiplicación Encadenada de Matrices

*   **Problema:** Dadas $M_1, \dots, M_n$ (dimensiones $d_{i-1} \times d_i$), minimizar multiplicaciones escalares para calcular $M_1 \times \dots \times M_n$.
*   **Subestructura Óptima:** La forma óptima de calcular $M_i \times \dots \times M_j$ implica una división óptima $(M_i \dots M_k) \times (M_{k+1} \dots M_j)$ para algún $k$.
*   **Recurrencia:** $m[i, j]$ = costo mínimo para $M_i \dots M_j$.
    *   $m[i, i] = 0$.
    *   $m[i, j] = \min_{i \le k < j} \{ m[i, k] + m[k+1, j] + d_{i-1} \cdot d_k \cdot d_j \}$ para $i < j$.
*   **Cálculo Bottom-Up:** Llenar tabla `m[n][n]` por longitud de cadena creciente ($l=2$ a $n$).
*   **Construcción Solución:** Usar tabla auxiliar `s[n][n]` que guarda el $k$ óptimo.
*   **Complejidad:** $O(n^3)$.

## Ejemplo 2: Árboles Binarios de Búsqueda Óptimos (Versión Simplificada)

*   **Problema (slides):** Dada secuencia de valores en hojas, minimizar suma de valores en nodos internos de un árbol binario donde cada nodo interno es la suma de sus hijos.
*   **Subestructura Óptima:** Similar a matrices. Árbol óptimo para $V_i \dots V_k$ se forma combinando subárboles óptimos $V_i \dots V_j$ y $V_{j+1} \dots V_k$.
*   **Recurrencia:** $C[i, k]$ = costo mínimo para $V_i \dots V_k$. $W[i, k] = \sum_{l=i}^k V_l$.
    *   $C[i, i] = 0$.
    *   $C[i, k] = \min_{i \le j < k} \{ C[i, j] + C[j+1, k] + W[i, k] \}$ para $i < k$.
*   **Cálculo y Complejidad:** Idéntico a multiplicación de matrices. $O(n^3)$.

## Ejemplo 3: Decibilidad de Lenguajes Libres del Contexto (Algoritmo CYK)

*   **Problema:** Dada gramática $G$ en FNC (reglas $A \to BC$ o $A \to a$) y cadena $x = x_1 \dots x_n$, ¿está $x \in L(G)$?
*   **DP Approach:** Tabla $M[j, i]$ = {Variables $A$ que generan subcadena $x_i \dots x_{i+j-1}$}.
*   **Recurrencia:**
    *   **Base (j=1):** $M[1, i] = \{ A \mid (A \to x_i) \in P \}$.
    *   **Paso (j>1):** $M[j, i] = \{ A \mid (A \to BC) \in P \text{ y } \exists k (1 \le k < j) \text{ t.q. } B \in M[k, i] \text{ y } C \in M[j-k, i+k] \}$.
*   **Cálculo Bottom-Up:** Llenar tabla $M$ por longitud $j$ creciente (1 a $n$).
*   **Resultado:** $x \in L(G)$ si $S \in M[n, 1]$.
*   **Complejidad:** $O(n^3 \cdot |P|)$.

## Ejemplo 4: Triangulación de un Polígono Convexo

*   **Problema:** Dado polígono convexo $v_0, \dots, v_{n-1}$, encontrar triangulación que minimice la suma de longitudes de las diagonales añadidas.
*   **Subestructura Óptima:** Triangulación óptima de $v_i \dots v_j$ usa un triángulo $(v_i, v_k, v_j)$ y triangulaciones óptimas de $(v_i \dots v_k)$ y $(v_k \dots v_j)$.
*   **Recurrencia:** $C[i, j]$ = costo mínimo para triangular polígono $v_i \dots v_j$.
    *   $C[i, i+1] = 0$.
    *   $C[i, j] = \min_{i < k < j} \{ C[i, k] + C[k, j] + \text{dist}(v_i, v_k) + \text{dist}(v_k, v_j) \}$ para $j > i+1$. *(Nota: La recurrencia puede variar ligeramente)*.
*   **Cálculo y Complejidad:** Similar a Matrix Chain. $O(n^3)$.

---
