Okay, aquí tienes un resumen del texto sobre "Análisis y Diseño de Algoritmos I" con anotaciones para facilitar la comprensión:

**Resumen y Anotaciones del Material de Análisis y Diseño de Algoritmos I**

1.  **¿Qué es un Algoritmo?**
    *   **Resumen:** Un algoritmo es una secuencia de pasos precisos, finitos y ejecutables (un *procedimiento efectivo*) para resolver una tarea. Se diferencia de un *procedimiento* general en que un algoritmo siempre debe terminar.
    *   **Anotación:** Piensa en una receta de cocina: es una secuencia de pasos (procedimiento). Si la receta está bien definida y garantiza que terminarás (incluso si el resultado es malo), es un algoritmo. "Efectivo" significa que cada paso es realizable y el proceso completo tiene un fin.

2.  **Algoritmos vs. Programas:**
    *   **Resumen:** Un programa es una forma de expresar algoritmos en un lenguaje de computadora. Sin embargo, no toda ejecución de un programa es un algoritmo (por ejemplo, un programa podría entrar en un bucle infinito, violando la condición de finitud).
    *   **Anotación:** El algoritmo es la *idea* o la *lógica* para resolver el problema. El programa es la *implementación* concreta de esa idea en un lenguaje como C++, Java, Python, etc. Un programa puede implementar varios algoritmos.

3.  **Problema Algorítmico:**
    *   **Resumen:** Se define por: 1) Una descripción de las entradas válidas y 2) Una especificación de la salida deseada en función de la entrada.
    *   **Anotación:** Es la definición formal de *qué* queremos resolver. Ejemplo: Para el problema de ordenamiento, la entrada válida es una secuencia de números, y la salida deseada es la misma secuencia pero ordenada.

4.  **Clasificación de Problemas:**
    *   **Resumen:**
        *   **Decisión vs. Salida General:** Los de decisión responden "sí/no" (ej: ¿este número es primo?). Los de salida general producen un resultado más complejo (ej: ordena esta lista).
        *   **Decidibles/Solubles vs. Indecidibles/Insolubles:** Los decidibles/solubles tienen *al menos un* algoritmo que los resuelve. Los indecidibles/insolubles *no* tienen ningún algoritmo que los pueda resolver siempre (ej: Problema del Halting - determinar si un programa cualquiera terminará).
        *   **Tratables vs. Intratables:** Dentro de los solubles, los tratables tienen algoritmos *eficientes* (razonables en tiempo/espacio). Los intratables tienen algoritmos, pero son tan lentos que no son prácticos para entradas grandes.
    *   **Anotación:** "Tratable" usualmente se asocia con algoritmos cuyo tiempo de ejecución crece polinomialmente (como $n^2$, $n^3$) con el tamaño de la entrada $n$. "Intratable" suele asociarse con crecimiento exponencial (como $2^n$, $n!$), que se vuelve prohibitivo muy rápidamente.

5.  **Enfoque del Curso (Análisis y Diseño I):**
    *   **Resumen:** Se centra en problemas *solubles y tratables computacionalmente*. Enseña una metodología para construir algoritmos usando abstracción (de datos y procedural), Tipos de Datos Abstractos (TDA), análisis de eficiencia y técnicas de diseño (Divide y Conquista, Greedy, Programación Dinámica). Se usa C++.
    *   **Anotación:** Este curso te dará las herramientas para crear soluciones *buenas y eficientes* para problemas que *sí se pueden* resolver de forma práctica. El curso "Análisis y Diseño II" probablemente aborda los problemas "intratables".

6.  **Eficiencia de Algoritmos (Unidad 1):**
    *   **Resumen:** La eficiencia mide cuántos recursos (tiempo, espacio/memoria) usa un algoritmo. Es un concepto *relativo*: un algoritmo es más eficiente *que otro* si usa menos recursos para la misma tarea.
    *   **Anotación:** No se puede decir que un algoritmo es "eficiente" en el vacío. Siempre es en comparación con otras soluciones o con un límite teórico.

7.  **¿Cómo Medir la Eficiencia (Tiempo)?**
    *   **Resumen:**
        *   **No:** Medir el tiempo exacto de ejecución en un ordenador específico. Esto depende demasiado de la máquina, el compilador, el sistema operativo, etc. (es un *análisis empírico*).
        *   **Sí:** Usar un *análisis teórico*. Se independiza de la implementación y se enfoca en cómo varía el tiempo con el *tamaño de la entrada* ($n$). Se cuentan las *operaciones elementales* (pasos básicos cuyo tiempo se considera constante).
    *   **Anotación:** El análisis teórico busca entender la *naturaleza* del algoritmo, no el rendimiento en una máquina particular. Una operación elemental puede ser una asignación, una comparación, una operación aritmética simple.

8.  **Análisis del Tiempo de Ejecución (T(n)):**
    *   **Resumen:** Se busca una función $T(n)$ que describa el tiempo en función del tamaño de entrada $n$. Se analiza el crecimiento de esta función. El análisis muestra que un algoritmo con mejor tasa de crecimiento (ej: $n \log n$) será mucho más rápido que uno con peor tasa (ej: $n^2$ o $n!$) para entradas grandes, independientemente de la velocidad del hardware.
    *   **Anotación:** La tabla del material ilustra esto potentemente: una mejora en hardware ayuda, pero un mal algoritmo (ej: $N!$) sigue siendo inutilizable rápidamente, mientras que un buen algoritmo escala mucho mejor. ¡La eficiencia algorítmica es clave!

9.  **Tipos de Análisis Teórico:**
    *   **Resumen:**
        *   **Peor Caso:** Cota superior del tiempo para cualquier entrada de tamaño $n$. Es el más común (pesimista pero garantiza un límite).
        *   **Mejor Caso:** Cota inferior. Poco útil en la práctica (demasiado optimista).
        *   **Caso Promedio:** Tiempo esperado sobre todas las posibles entradas de tamaño $n$. Más realista pero matemáticamente complejo y depende de la distribución de las entradas.
    *   **Anotación:** Este curso se centrará principalmente en el *peor caso* porque ofrece una garantía de rendimiento y suele ser más fácil de analizar que el caso promedio.

10. **Notación Asintótica (O, Ω, θ):**
    *   **Resumen:** Son herramientas matemáticas para clasificar funciones según su *orden de magnitud* o *tasa de crecimiento* a medida que $n$ se hace grande. Ignoran constantes multiplicativas y términos de menor orden.
        *   **Big-O (O): Cota Superior.** $T(n) \in O(g(n))$ si $T(n)$ no crece más rápido que $g(n)$ (salvo por una constante) para $n$ suficientemente grande. Formalmente: $\exists c > 0, n_0 > 0$ tal que $T(n) \leq c \cdot g(n)$ para todo $n \geq n_0$.
        *   **Big-Omega (Ω): Cota Inferior.** $T(n) \in \Omega(g(n))$ si $T(n)$ no crece más lento que $g(n)$ (salvo por una constante) para $n$ suficientemente grande. Formalmente: $\exists c > 0, n_0 > 0$ tal que $T(n) \geq c \cdot g(n)$ para todo $n \geq n_0$.
        *   **Big-Theta (θ): Cota Ajustada.** $T(n) \in \theta(g(n))$ si $T(n)$ crece al mismo ritmo que $g(n)$ (salvo por constantes) para $n$ suficientemente grande. Es decir, $T(n) \in O(g(n))$ y $T(n) \in \Omega(g(n))$. Formalmente: $\exists c_1, c_2 > 0, n_0 > 0$ tal que $c_1 \cdot g(n) \leq T(n) \leq c_2 \cdot g(n)$ para todo $n \geq n_0$.
    *   **Anotación:** Estas notaciones nos permiten decir cosas como "Este algoritmo es $O(n^2)$" (su tiempo en el peor caso no crece más rápido que $n^2$) o "Este algoritmo es $\theta(n \log n)$" (su tiempo crece exactamente como $n \log n$). Son el lenguaje estándar para hablar de eficiencia algorítmica.

11. **Uso y Pruebas de las Notaciones:**
    *   **Resumen:** Se muestran ejemplos de cómo demostrar algebraicamente que una función $f(n)$ pertenece a $O(g(n))$, $\Omega(g(n))$ o $\theta(g(n))$ encontrando las constantes $c, c_1, c_2$ y el umbral $n_0$. También se muestra un ejemplo de cómo probar que una función *no* pertenece a una clase (ej: $5^n \notin O(2^n)$).
    *   **Anotación:** La clave es encontrar *un* par $(c, n_0)$ o una terna $(c_1, c_2, n_0)$ que funcione. No tiene que ser el "mejor" o el más ajustado, solo tiene que cumplir la definición.

12. **Funciones Inconmensurables:**
    *   **Resumen:** Existen pares de funciones donde ninguna es $O$ de la otra, porque su relación de crecimiento varía (a veces una es mayor, a veces la otra).
    *   **Anotación:** Esto es menos común con las funciones típicas que describen tiempos de ejecución (como $\log n, n, n^2, 2^n$), pero es teóricamente posible.

# Resumen y Anotaciones: Análisis de Eficiencia de Algoritmos (Continuación)

## Factores que Determinan el Tiempo de Ejecución

*   **Dependientes de la Implementación:**
    *   Computadora (velocidad del hardware).
    *   Compilador, Sistema Operativo (eficiencia del código generado, gestión de recursos).
*   **Independientes de la Implementación:**
    *   **Algoritmo:** La lógica y secuencia de pasos elegida. ¡Este es nuestro foco!
    *   **Datos de Entrada:** Principalmente el **tamaño** de los datos ($n$), pero a veces también la naturaleza específica de los datos (ej: si están ordenados o no).

*   *Anotación:* El análisis teórico se centra en los factores independientes (algoritmo y tamaño de entrada) para obtener medidas objetivas y comparables.

## Métodos de Análisis de Eficiencia Temporal

1.  **Análisis Empírico:**
    *   Requiere implementar y ejecutar el código.
    *   Mide el tiempo real (segundos, milisegundos).
    *   Depende totalmente de la implementación (hardware, SO, compilador).
    *   Solo se prueba con un conjunto limitado de entradas.
    *   *Anotación:* Útil para comparar rendimientos *finales* en un entorno específico, pero no ideal para el *diseño* y análisis *general* de algoritmos.

2.  **Análisis Teórico:**
    *   Predictivo, se integra en el diseño.
    *   Independiente de la implementación.
    *   Establece **cotas** (límites) para el tiempo de ejecución:
        *   **Peor Caso:** Límite superior para *cualquier* entrada de tamaño $n$. (Más común).
        *   **Mejor Caso:** Límite inferior. (Menos útil, a menudo irreal).
        *   **Caso Promedio:** Comportamiento esperado sobre *todas* las posibles entradas. (Más realista pero matemáticamente complejo y requiere supuestos sobre la distribución de datos).
    *   *Anotación:* Nos enfocaremos en el análisis teórico, principalmente del peor caso, usando notación asintótica.

## Función de Tiempo T(n) y Notación Big-O

*   $T(n)$: Función que expresa el tiempo de ejecución en función del tamaño de la entrada $n$.
*   Asumimos: $n \ge 0$ (entero no negativo), $T(n) \ge 0$.
*   **Objetivo:** Acotar $T(n)$ usando una función más simple $g(n)$.
*   **Notación Big-O (Cota Superior):** $T(n) \in O(g(n))$ si existen constantes positivas $c_0$ y $n_0$ tales que $T(n) \le c_0 g(n)$ para todo $n \ge n_0$.
    *   $c_0$: Constante de proporcionalidad (relacionada con factores de implementación).
    *   $g(n)$: **Complejidad Temporal** (relacionada con el algoritmo y el tamaño de entrada).
*   **Análisis de Peor Caso:** Usamos $O(g(n))$ para dar una cota superior del tiempo en el peor escenario posible para una entrada de tamaño $n$.
    *   Definición formal: $O(g(n)) = \{ f: \mathbb{N}^+ \to \mathbb{R}^+ \mid \exists c \in \mathbb{R}^+, n_0 \in \mathbb{N}^+ : \forall n \ge n_0, f(n) \le c \cdot g(n) \}$

## Características de la Función $f(n)$ en $O(f(n))$

Cuando decimos que la complejidad es $O(f(n))$, buscamos que $f(n)$ sea:

1.  **Simple:** Un término simple, usualmente con coeficiente 1 (ej: $n^2$, $n \log n$, $1$).
2.  **La Cota "Más Cercana" (Tightest Bound):** Si $T(n) \in O(f(n))$, entonces para cualquier otra cota $g(n)$ tal que $T(n) \in O(g(n))$, debe cumplirse que $f(n) \in O(g(n))$.
    *   *Anotación:* Queremos la cota superior más descriptiva posible. Si un algoritmo es $O(n^2)$, también es $O(n^3)$, $O(n^4)$, etc., pero $O(n^2)$ es la cota más ajustada y útil.

## Reglas para Acotar el Tiempo de Ejecución (Código Estructurado)

*   **Regla 1: Instrucciones Simples:** $O(1)$ (tiempo constante).
    *   Operaciones aritméticas (+, -, *, /).
    *   Operaciones lógicas (&&, ||, !).
    *   Comparaciones (<, >, ==, <=, >=).
    *   Acceso a estructuras (ej: `A[i]`).
    *   Asignaciones simples (`x = y`).
    *   Llamadas a funciones de biblioteca estándar con tiempo constante (ej: `cout`, `cin` para tipos básicos).
    *   Un bloque secuencial de instrucciones $O(1)$ sigue siendo $O(1)$.

*   **Regla 2: Concatenación (Secuencia):** (Regla de la Suma)
    *   Si el bloque P1 tiene tiempo $T_1(n) \in O(f_1(n))$ y el bloque P2 tiene tiempo $T_2(n) \in O(f_2(n))$, entonces la secuencia `P1; P2;` tiene tiempo $T_1(n) + T_2(n) \in O(\max(f_1(n), f_2(n)))$.
    *   *Anotación:* La complejidad total está dominada por la parte más lenta. Ej: $O(n) + O(n^2) = O(n^2)$.

*   **Regla 3: Selección (if-else):**
    *   `if (<condición>) <parte-if> else <parte-else>`
    *   Tiempo $\approx$ Tiempo(condición) + $\max($Tiempo(parte-if), Tiempo(parte-else)$)$
    *   Si Tiempo(condición) $\in O(f_3(n))$, Tiempo(parte-if) $\in O(f_1(n))$, Tiempo(parte-else) $\in O(f_2(n))$, entonces el tiempo total es $O(f_3(n) + \max(f_1(n), f_2(n)))$.
    *   Si la condición es $O(1)$, el total es $O(\max(f_1(n), f_2(n)))$.
    *   *Anotación:* Se considera el tiempo de la rama más costosa (peor caso) más el tiempo de evaluar la condición.

*   **Regla 4: Iteración (Loops - for, while):**
    *   El tiempo total es la suma de los tiempos de cada iteración (incluyendo la evaluación de la condición del bucle y la actualización del contador/variable de control).
    *   **Forma común:** `for (i=0; i < n; i++) { <cuerpo> }`
        *   Si el cuerpo es $O(f(n))$, y el bucle se ejecuta $n$ veces, el tiempo total es a menudo $O(n \cdot f(n))$.
        *   Si el cuerpo es $O(1)$, el tiempo total es $O(n)$.
    *   **Análisis con Sumatorias:** A menudo útil para bucles anidados.
        *   $\sum_{i=1}^{n} c = c \cdot n \in O(n)$
        *   $\sum_{i=1}^{n} i = \frac{n(n+1)}{2} \in O(n^2)$
        *   $\sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6} \in O(n^3)$
        *   $\sum_{i=0}^{n} a^i = \frac{a^{n+1}-1}{a-1} \in O(a^n)$ (Suma geométrica, $a \ne 1$)
    *   **Ejemplos de Bucles Anidados:**
        *   Doble bucle `for i=0..n-1`, `for j=0..n-1` con cuerpo $O(1)$ $\implies O(n^2)$.
        *   Doble bucle `for i=0..n-1`, `for j=0..i-1` con cuerpo $O(1)$ $\implies O(n^2)$ (porque $\sum_{i=0}^{n-1} i = O(n^2)$).
        *   Triple bucle `for i=0..n-1`, `for j=0..n-1`, `for k=0..n-1` con cuerpo $O(1)$ $\implies O(n^3)$.

*   **Regla 5: Complejidad Logarítmica:**
    *   Surge cuando el tamaño del problema se reduce en un factor constante en cada paso (generalmente división).
    *   Ejemplo: `k=N; while (k > 0) k /= 2;`
        *   El bucle se ejecuta $\approx \log_2 N$ veces.
        *   Si el cuerpo es $O(1)$, el tiempo total es $O(\log N)$.
    *   *Anotación:* La base del logaritmo no importa en la notación Big-O, ya que $\log_a n = \log_b n \cdot \log_a b$, y $\log_a b$ es una constante. Se escribe $O(\log n)$.

## Acotar Tiempo con Llamadas a Funciones (No Recursivas)

*   **Estrategia:** Analizar "bottom-up" en el grafo de llamadas.
    1.  Analiza las funciones que no llaman a ninguna otra función.
    2.  Analiza las funciones que solo llaman a funciones ya analizadas.
    3.  Continúa hasta analizar la función principal (`main`).
*   El costo de una llamada a función `foo()` dentro de `bar()` se suma al costo de `bar()`.
*   **Ejemplo `main` -> `foo` -> `bar`:**
    1.  Calcular $T_{bar}(n)$.
    2.  Calcular $T_{foo}(n)$ (incluirá el costo de las llamadas a `bar`).
    3.  Calcular $T_{main}(n)$ (incluirá el costo de las llamadas a `foo`).

## Acotar Tiempo de Funciones Recursivas

1.  **Identificar Parámetro de Tamaño:** Determina qué mide el "tamaño" del problema ($n$).
2.  **Establecer Ecuación de Recurrencia:** Expresa $T(n)$ en términos de $T$ para tamaños más pequeños.
    *   **Caso Base:** El costo cuando la recursión termina (ej: $T(1) = c_1$).
    *   **Caso Recursivo:** El costo del trabajo no recursivo en el paso actual + el costo de las llamadas recursivas.
        *   Ej: $T(n) = \text{CostoPasoActual} + \sum T(\text{tamaño_subproblema})$
3.  **Resolver la Ecuación de Recurrencia:** Encontrar una forma cerrada (no recursiva) para $T(n)$, usualmente expresada en notación $O$, $\Omega$ o $\theta$.
    *   **Método de Sustitución (o Expansión Iterativa):**
        *   Expandir la recurrencia sustituyéndola en sí misma repetidamente.
        *   Buscar un patrón en la expansión.
        *   Sumar los costos en cada nivel de recursión.
        *   Llevar la expansión hasta el caso base.
        *   Simplificar para obtener la forma cerrada.

*   **Ejemplos de Recurrencias Comunes:**
    *   **Factorial:** $T(n) = T(n-1) + c_2 \implies T(n) \in O(n)$
    *   **Torres de Hanoi:** $T(n) = 2T(n-1) + c_2 \implies T(n) \in O(2^n)$
    *   **Búsqueda Binaria:** $T(m) = T(m/2) + c_2 \implies T(m) \in O(\log m)$
    *   **Ejemplo $T(n) = 3T(n/3) + c_2$:** (Asumiendo $n=3^k$)
        *   $T(n) = 3T(n/3) + c_2$
        *   $= 3(3T(n/9) + c_2) + c_2 = 9T(n/9) + 3c_2 + c_2$
        *   $= 9(3T(n/27) + c_2) + 3c_2 + c_2 = 27T(n/27) + 9c_2 + 3c_2 + c_2$
        *   ... (tras $k = \log_3 n$ pasos) ...
        *   $= 3^k T(1) + c_2 \sum_{i=0}^{k-1} 3^i = n \cdot c_1 + c_2 \frac{3^k - 1}{3-1}$
        *   $= n c_1 + c_2 \frac{n-1}{2} \in O(n)$
    *   **Ejemplo $T(n) = T(n/3) + c_2$:** (Asumiendo $n=3^k$)
        *   $T(n) = T(n/3) + c_2$
        *   $= (T(n/9) + c_2) + c_2 = T(n/9) + 2c_2$
        *   ... (tras $k = \log_3 n$ pasos) ...
        *   $= T(1) + k \cdot c_2 = c_1 + (\log_3 n) c_2 \in O(\log n)$

## Material Matemático de Apoyo

*   Se mencionan propiedades de funciones parte entera (floor $\lfloor x \rfloor$, ceiling $\lceil x \rceil$).
*   Fórmulas de sumatorias.
*   Propiedades de logaritmos (importante: cambio de base).

*(Los ejemplos específicos de código al final del documento sirven como ejercicios prácticos para aplicar estas reglas y técnicas).*