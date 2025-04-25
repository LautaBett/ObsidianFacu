	¡Perfecto! Aquí tienes un resumen de la información sobre implementación, complejidad y eficiencia en C++, formateado para Obsidian y con explicaciones adicionales:

```markdown
# Resumen: Implementación y Complejidad en C++ (Basado en Material AyDA I - UNICEN)

Este resumen aborda cómo analizar la eficiencia de los algoritmos implementados en C++, centrándose en el concepto de complejidad computacional y comparando diferentes soluciones para los mismos problemas.

## 1. Recursos y Material

*   **Bibliografía Recomendada:**
    *   SAVITCH, W. A. *Resolución de problemas con C++*.
    *   CORMEN, Thomas H., et al. *Introduction to algorithms*. (Referencia clave para algoritmos y complejidad).
*   **Documentación Oficial C++:**
    *   [cppreference.com](https://en.cppreference.com/w/)
    *   [cplusplus.com](https://cplusplus.com/)
*   **Bibliografía Extra (Ejemplo GCD):**
    *   HERZ-FISCHLER, Roger. *A mathematical history of division in extreme and mean ratio*.

## 2. Análisis de Complejidad: Conceptos Básicos

*   **Objetivo:** Estimar cómo los recursos requeridos por un algoritmo (principalmente tiempo de ejecución, pero también memoria) crecen a medida que aumenta el tamaño de la entrada.
*   **Operaciones Elementales:** Instrucciones que toman un tiempo aproximadamente constante, independientemente del tamaño de la entrada (asignaciones, operaciones aritméticas simples, comparaciones, acceso a arreglos por índice). Se agrupan bajo una constante, por ejemplo, $c_0$.
*   **Bucles (Loops):** Su contribución al tiempo depende de cuántas veces se ejecutan (número de iteraciones) y qué se hace dentro de cada iteración. El número de iteraciones a menudo depende del tamaño de la entrada (ej. `n`, `m`).
*   **Análisis:** Se busca una **cota superior** del tiempo de ejecución $T(entrada)$ en función del tamaño de la entrada. Se suman los tiempos de las operaciones elementales y los bucles.
*   **Notación Big O (O):** Describe el comportamiento **asintótico** del tiempo de ejecución en el **peor caso**. Se enfoca en el término dominante de la función de tiempo y descarta constantes multiplicativas y términos de orden inferior. Por ejemplo, si $T(n) = 5n^2 + 10n + 3$, su complejidad es $O(n^2)$.

## 3. Ejemplo 1: Análisis Detallado de `Contar(n, m)`

```cpp
int Contar (int n, int m) {
    int j, contadorSentencias = 0, i = 1; // c0 (tiempo constante)
    while (i <= m) { // Bucle externo
        j = n; // c1 (tiempo constante dentro del bucle externo)
        while (j != 0){ // Bucle interno
            j = j / 2; // c2 (tiempo constante dentro del bucle interno)
            contadorSentencias ++; // c2
        }
        i++; // c1
    }
    return contadorSentencias; // c0
}
```

*   **Análisis:**
    1.  **Operaciones Constantes (fuera de bucles):** Inicializaciones (`int j, contadorSentencias = 0, i = 1;`) y el `return`. Tiempo total: $c_0$.
    2.  **Bucle Externo (`while (i <= m)`):**
        *   Se ejecuta `m` veces (desde `i=1` hasta `i=m`).
        *   Operaciones *dentro* del bucle externo pero *fuera* del interno: `j = n;` y `i++;`. Tiempo por iteración: $c_1$.
    3.  **Bucle Interno (`while (j != 0)`):**
        *   Se ejecuta dentro de cada iteración del bucle externo.
        *   La variable `j` empieza en `n` y se divide por 2 en cada paso (`j = j / 2`).
        *   El número de iteraciones es aproximadamente $log_2(n)$ (más precisamente, $\lfloor log_2 n \rfloor + 1$). *Explicación: ¿Cuántas veces puedes dividir n por 2 hasta llegar a cerca de 0? Esa es la definición del logaritmo en base 2.*
        *   Operaciones dentro del bucle interno: `j = j / 2;` y `contadorSentencias++;`. Tiempo por iteración: $c_2$.
        *   Tiempo total del bucle interno por cada ejecución: $c_2 \times (\lfloor log_2 n \rfloor + 1)$.
    4.  **Tiempo Total:** Sumamos todo. El bucle interno se ejecuta `m` veces.
        $T(m, n) \le c_0 + \sum_{i=1}^{m} (c_1 + c_2 (\lfloor log_2 n \rfloor + 1))$
        $T(m, n) \le c_0 + m \times (c_1 + c_2 (\lfloor log_2 n \rfloor + 1))$
        $T(m, n) \le c_0 + m c_1 + m c_2 \lfloor log_2 n \rfloor + m c_2$
    5.  **Orden de Complejidad (Big O):**
        *   Identificamos el término dominante: $m \times c_2 \times \lfloor log_2 n \rfloor$.
        *   Descartamos constantes ($c_0, c_1, c_2$) y términos de orden inferior ($m c_1, m c_2$).
        *   La complejidad es $O(m \log_2 n)$ o simplemente $O(m \log n)$ (la base del logaritmo no afecta la clase de complejidad en Big O).

*   **Comprobación:** Se sugiere hacer debugging o seguimiento manual contando las iteraciones para verificar que la cota calculada se ajusta al comportamiento real.

## 4. Ejemplo 2: Pruebas de Primalidad

**Problema:** Determinar si un número entero `numero` es primo (solo divisible por 1 y por sí mismo).

*   **Solución 1: Intuitiva ("A martillazos")**
    *   **Idea:** Probar todos los divisores desde 2 hasta `numero - 1`.
    *   **Código:**
        ```cpp
        bool es_primo(unsigned int numero) {
            if (numero <= 1) return false; // 0 y 1 no son primos
            bool primo = true;
            for(unsigned int divisor=2; divisor < numero; divisor++){
                if (numero % divisor == 0) {
                    primo = false;
                    // break; // Se podría añadir un break para salir antes
                }
            }
            return primo;
        }
        ```
    *   **Complejidad:** El bucle `for` se ejecuta `numero - 2` veces en el peor caso (cuando `numero` es primo). La complejidad es $O(numero)$ o $O(n)$.

*   **Solución 2: Intuitiva con Corte ("Con flag")**
    *   **Idea:** Igual que la anterior, pero detenerse tan pronto como se encuentre un divisor.
    *   **Código:**
        ```cpp
        bool es_primo(unsigned int numero, unsigned int & iteraciones) {
            iteraciones = 0; // Inicializar contador
             if (numero <= 1) return false;
             bool primo = true;
             unsigned int divisor = 2;
             while (primo && (divisor < numero)) {
                 iteraciones++; // Contar iteración del while
                 if (numero % divisor == 0) {
                     primo = false; // Encontró divisor, no es primo
                 }
                 divisor++;
             }
             return primo;
        }
        ```
    *   **Complejidad:** El **peor caso** sigue siendo cuando `numero` es primo, y el bucle se ejecuta casi `numero` veces. La complejidad sigue siendo $O(n)$. Sin embargo, en el caso promedio (para números compuestos), se detiene antes.

*   **Solución 3: Optimizada (Raíz Cuadrada)**
    *   **Idea:** Si un número `n` tiene un divisor `d > sqrt(n)`, entonces también debe tener un divisor `n/d < sqrt(n)`. Por lo tanto, solo necesitamos buscar divisores hasta la raíz cuadrada de `numero`.
    *   **Código:**
        ```cpp
        #include <cmath> // Para sqrt y ceil

        bool es_primo(unsigned int numero, unsigned int & iteraciones) {
            iteraciones = 0;
            if (numero <= 1) return false;
            if (numero <= 3) return true; // 2 y 3 son primos
            if (numero % 2 == 0 || numero % 3 == 0) return false; // Optimización rápida

            bool primo = true;
            // Empezar en 5 y probar divisores hasta sqrt(numero)
            // Solo necesitamos probar divisores de la forma 6k ± 1 (optimización adicional no mostrada en el original)
            unsigned int maximo = static_cast<unsigned int>(sqrt(numero)); 
            // unsigned int maximo = ceil(sqrt(numero)); // Como en el original

            // Bucle original adaptado:
            unsigned int divisor = 2; // O empezar en 5 si se usan optimizaciones 6k+-1
             while (primo && (divisor <= maximo)) {
                 iteraciones++;
                 if (numero % divisor == 0) {
                     primo = false;
                 }
                 divisor++; // O incrementar en pasos de 2 o 6
             }
            return primo;
        }
        ```
    *   **Complejidad:** El bucle se ejecuta hasta $\sqrt{numero}$ veces. La complejidad es $O(\sqrt{n})$.

*   **Comparación:**
    *   Los gráficos y tablas de iteraciones/tiempo muestran claramente que $O(\sqrt{n})$ es **mucho más eficiente** que $O(n)$, especialmente para números grandes. El número de operaciones crece mucho más lentamente.

## 5. Ejemplo 3: Máximo Común Divisor (GCD/MCD)

**Problema:** Encontrar el mayor número entero que divide a dos números `a` y `b` sin dejar resto.

*   **Solución 1: Intuitiva/Ingenua**
    *   **Idea:** Probar todos los números desde 1 hasta el mínimo de `a` y `b`. El último número que divida a ambos es el GCD.
    *   **Código:**
        ```cpp
        int get_gcd_naive(int a, int b) {
            int gcd = 1;
            int min_ = (a < b) ? a : b; // Operador ternario para min(a, b)
            for (int i = 1; i <= min_; i++) {
                if (a % i == 0 && b % i == 0) {
                    gcd = i; // Actualiza al último divisor común encontrado
                }
            }
            return gcd;
        }
        ```
    *   **Complejidad:** El bucle `for` se ejecuta `min(a, b)` veces. La complejidad es $O(\min(a, b))$. Es lineal respecto al menor de los dos números.

*   **Solución 2: Algoritmo de Euclides (Divisiones Sucesivas)**
    *   **Idea:** Se basa en la propiedad: $gcd(a, b) = gcd(b, a \pmod{b})$. Se aplica repetidamente hasta que el resto sea 0. El último divisor no nulo es el GCD.
    *   **Código:**
        ```cpp
        int get_gcd_euclides(int a, int b, int & operaciones) {
            operaciones = 0;
            // Asegurarse a >= b (opcional, funciona igual pero puede ahorrar una iteración)
            // if (b > a) { int aux = a; a = b; b = aux; } 
            
            while (b != 0) {
                operaciones++;
                int aux = b;
                b = a % b; // El núcleo del algoritmo
                a = aux;
            }
            return a; // Cuando b es 0, a contiene el GCD
        }
        ```
    *   **Complejidad:** El número de pasos (divisiones) es logarítmico respecto al mínimo de `a` y `b`. Cada operación de módulo reduce significativamente el tamaño de los números. La complejidad es $O(\log(\min(a, b)))$.

*   **Comparación:**
    *   El algoritmo de Euclides ($O(\log n)$) es **exponencialmente más rápido** que el método ingenuo ($O(n)$). Las tablas y gráficos comparativos muestran una diferencia drástica en el número de operaciones requeridas.

## 6. Conclusiones Clave

*   El **análisis de complejidad** es esencial para entender cómo se comportará un algoritmo con entradas grandes.
*   La **notación Big O** proporciona una forma estándar de clasificar la eficiencia (escalabilidad) de los algoritmos.
*   Un mismo problema puede tener **múltiples soluciones** con complejidades muy diferentes.
*   Elegir o diseñar un algoritmo con una **menor complejidad** (ej. $O(\log n)$ o $O(\sqrt{n})$ vs $O(n)$) puede resultar en mejoras de rendimiento enormes.
*   Las **optimizaciones matemáticas** (como usar $\sqrt{n}$ para primalidad o el algoritmo de Euclides para GCD) a menudo conducen a los algoritmos más eficientes.

