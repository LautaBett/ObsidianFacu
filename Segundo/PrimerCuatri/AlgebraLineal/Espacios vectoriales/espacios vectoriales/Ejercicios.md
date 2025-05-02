d                	Title: <a href="obsidian://open?file=Facultad%2FSegundo%2FPrimerCuatri%2FAlgebraLineal%2FRectas%2CPlanos%2CRango%2FEjercicios.md">Ejercicios</a>
Path: Facultad/Segundo/PrimerCuatri/AlgebraLineal/Rectas,Planos,Rango/Ejercicios.md

# Resolución de Ejercicios de Álgebra Lineal

---

## Ejercicio 1: Espacio Vectorial

**Método:** Verificar si el conjunto $V$ con las operaciones dadas cumple los 8 axiomas de espacio vectorial (S1-S4 y P1-P4).

**a) 𝑉 = {𝑃 ∈ 𝐾[𝑋]: 𝑔𝑟(𝑃) ≤ 𝑛} ∪ {0} con la suma de polinomios y el producto de un polinomio por un escalar.**

*   **Análisis:**
    *   El conjunto $V$ consiste en polinomios de grado menor o igual a $n$, junto con el polinomio cero.
    *   La suma de dos polinomios en $V$ resulta en otro polinomio en $V$ (el grado no aumenta).
    *   El producto de un escalar por un polinomio en $V$ también resulta en un polinomio en $V$.
    *   El polinomio cero está en $V$, actuando como el elemento neutro para la suma.
    *   El inverso aditivo de un polinomio en $V$ también está en $V$.
    *   Se cumplen las propiedades asociativa, conmutativa y distributivas.
*   **Conclusión:** $V$ es un espacio vectorial.

**b) 𝑉 = ℤ, lo números enteros. 𝐾 = ℚ, los números racionales. Con la suma y el producto usual.**

*   **Análisis:**
    *   La suma de dos enteros es un entero, por lo que la suma es cerrada en $V$.
    *   Sin embargo, el producto de un racional por un entero no siempre es un entero. Por ejemplo, $0.5 \cdot 1 = 0.5 \notin \mathbb{Z}$.
    *   Por lo tanto, no se cumple el axioma de cerradura bajo la multiplicación por escalares.
*   **Conclusión:** $V$ no es un espacio vectorial.

**c) 𝑉 = ℚ, 𝐾 = ℝ con la suma y el producto usual.**

*   **Análisis:**
    *   La suma de dos números racionales es un número racional, por lo que la suma es cerrada en $V$.
    *   Sin embargo, el producto de un número real por un número racional no siempre es un número racional. Por ejemplo, $\sqrt{2} \cdot 1 = \sqrt{2} \notin \mathbb{Q}$.
    *   Por lo tanto, no se cumple el axioma de cerradura bajo la multiplicación por escalares.
*   **Conclusión:** $V$ no es un espacio vectorial.

**d) 𝑉 = {𝐴 ∈ 𝐾
𝑛×𝑛
: 𝐴
𝑡 = 𝐴} con la suma de matrices y el producto de un escalar por una matriz.**

*   **Análisis:**
    *   $V$ es el conjunto de matrices simétricas de tamaño $n \times n$.
    *   La suma de dos matrices simétricas es simétrica: $(A+B)^t = A^t + B^t = A + B$.
    *   El producto de un escalar por una matriz simétrica es simétrica: $(\lambda A)^t = \lambda A^t = \lambda A$.
    *   La matriz cero es simétrica.
    *   El inverso aditivo de una matriz simétrica es simétrica.
    *   Se cumplen las propiedades asociativa, conmutativa y distributivas.
*   **Conclusión:** $V$ es un espacio vectorial.

---

## Ejercicio 2: Dependencia Lineal

**Método:** Formar una combinación lineal de los vectores igualada al vector cero y analizar las soluciones del sistema homogéneo resultante. Si la única solución es la trivial (todos los escalares son cero), los vectores son linealmente independientes. Si hay otras soluciones, son linealmente dependientes.

**a) 𝑉 = ℝ3
𝑣1 = (1,1,0) 𝑣2 = (0,2,3) 𝑣3 = (1,2,3) 𝑣4 = (3,6,6)**

*   **Combinación Lineal:** $\alpha_1(1,1,0) + \alpha_2(0,2,3) + \alpha_3(1,2,3) + \alpha_4(3,6,6) = (0,0,0)$
*   **Sistema:**
    *   $\alpha_1 + \alpha_3 + 3\alpha_4 = 0$
    *   $\alpha_1 + 2\alpha_2 + 2\alpha_3 + 6\alpha_4 = 0$
    *   $3\alpha_2 + 3\alpha_3 + 6\alpha_4 = 0$
*   **Matriz:**
    $A = \begin{pmatrix} 1 & 0 & 1 & 3 \\ 1 & 2 & 2 & 6 \\ 0 & 3 & 3 & 6 \end{pmatrix} \xrightarrow{F_2 - F_1} \begin{pmatrix} 1 & 0 & 1 & 3 \\ 0 & 2 & 1 & 3 \\ 0 & 3 & 3 & 6 \end{pmatrix} \xrightarrow{F_3 - \frac{3}{2}F_2} \begin{pmatrix} 1 & 0 & 1 & 3 \\ 0 & 2 & 1 & 3 \\ 0 & 0 & \frac{3}{2} & \frac{3}{2} \end{pmatrix}$
*   **Análisis:** El sistema tiene rango 3 y 4 incógnitas, por lo que es compatible indeterminado (infinitas soluciones). Los vectores son linealmente dependientes.
*   **Subconjunto L.I.:** Las primeras tres columnas tienen pivote, por lo que $\vec{v_1}, \vec{v_2}, \vec{v_3}$ son linealmente independientes.
*   **Expresar $\vec{v_4}$ como combinación lineal:** De la última fila: $\frac{3}{2}\alpha_3 + \frac{3}{2}\alpha_4 = 0 \implies \alpha_3 = -\alpha_4$. De la segunda fila: $2\alpha_2 + \alpha_3 + 3\alpha_4 = 0 \implies 2\alpha_2 - \alpha_4 + 3\alpha_4 = 0 \implies \alpha_2 = -\alpha_4$. De la primera fila: $\alpha_1 + \alpha_3 + 3\alpha_4 = 0 \implies \alpha_1 - \alpha_4 + 3\alpha_4 = 0 \implies \alpha_1 = -2\alpha_4$.
    Si $\alpha_4 = 1$, entonces $\alpha_1 = -2, \alpha_2 = -1, \alpha_3 = -1$.
    $-2\vec{v_1} - \vec{v_2} - \vec{v_3} + \vec{v_4} = \vec{0} \implies \vec{v_4} = 2\vec{v_1} + \vec{v_2} + \vec{v_3}$.

**b) 𝑉 = ℝ3
𝑣1 = (1,1,0) 𝑣2 = (3,4,2)**

*   **Combinación Lineal:** $\alpha_1(1,1,0) + \alpha_2(3,4,2) = (0,0,0)$
*   **Sistema:**
    *   $\alpha_1 + 3\alpha_2 = 0$
    *   $\alpha_1 + 4\alpha_2 = 0$
    *   $2\alpha_2 = 0$
*   **Análisis:** De la tercera ecuación, $\alpha_2 = 0$. Sustituyendo en la primera, $\alpha_1 = 0$. La única solución es la trivial.
*   **Conclusión:** Los vectores son linealmente independientes.

**c) 𝑉 = ℝ4
𝑣1 = (1,0,1,0) 𝑣2 = (0,1,0,1) 𝑣3 = (0,0,0,0) 𝑣4 = (2,2,2,2)
𝑣5 = (𝑎, −𝑏, 𝑎, −𝑏)**

*   **Análisis:** Como $\vec{v_3} = (0,0,0,0)$, el conjunto es linealmente dependiente. Cualquier conjunto que contenga el vector cero es linealmente dependiente.
*   **Subconjunto L.I.:** Podemos tomar $\vec{v_1}$ y $\vec{v_2}$ como linealmente independientes.
*   **Expresar los restantes como combinación lineal:**
    *   $\vec{v_3} = 0\vec{v_1} + 0\vec{v_2}$
    *   $\vec{v_4} = 2\vec{v_1} + 2\vec{v_2}$
    *   $\vec{v_5} = a\vec{v_1} - b\vec{v_2}$

**d) 𝑉 = ℝ2×2
𝑣1 = [
1 1
2 1
] 𝑣2 = [
1 0
0 2
] 𝑣3 = [
0 3
2 1
] 𝑣4 = [
4 6
8 6
]**

*   **Combinación Lineal:** $\alpha_1\begin{pmatrix} 1 & 1 \\ 2 & 1 \end{pmatrix} + \alpha_2\begin{pmatrix} 1 & 0 \\ 0 & 2 \end{pmatrix} + \alpha_3\begin{pmatrix} 0 & 3 \\ 2 & 1 \end{pmatrix} + \alpha_4\begin{pmatrix} 4 & 6 \\ 8 & 6 \end{pmatrix} = \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}$
*   **Sistema:**
    *   $\alpha_1 + \alpha_2 + 4\alpha_4 = 0$
    *   $\alpha_1 + 3\alpha_3 + 6\alpha_4 = 0$
    *   $2\alpha_1 + 2\alpha_3 + 8\alpha_4 = 0$
    *   $\alpha_1 + 2\alpha_2 + \alpha_3 + 6\alpha_4 = 0$
*   **Matriz:**
    $A = \begin{pmatrix} 1 & 1 & 0 & 4 \\ 1 & 0 & 3 & 6 \\ 2 & 0 & 2 & 8 \\ 1 & 2 & 1 & 6 \end{pmatrix} \xrightarrow{F_2-F_1, F_3-2F_1, F_4-F_1} \begin{pmatrix} 1 & 1 & 0 & 4 \\ 0 & -1 & 3 & 2 \\ 0 & -2 & 2 & 0 \\ 0 & 1 & 1 & 2 \end{pmatrix} \xrightarrow{F_3-2F_2, F_4+F_2} \begin{pmatrix} 1 & 1 & 0 & 4 \\ 0 & -1 & 3 & 2 \\ 0 & 0 & -4 & -4 \\ 0 & 0 & 4 & 4 \end{pmatrix} \xrightarrow{F_4+F_3} \begin{pmatrix} 1 & 1 & 0 & 4 \\ 0 & -1 & 3 & 2 \\ 0 & 0 & -4 & -4 \\ 0 & 0 & 0 & 0 \end{pmatrix}$
*   **Análisis:** El sistema tiene rango 3 y 4 incógnitas, por lo que es compatible indeterminado (infinitas soluciones). Los vectores son linealmente dependientes.
*   **Subconjunto L.I.:** Las primeras tres columnas tienen pivote, por lo que $\vec{v_1}, \vec{v_2}, \vec{v_3}$ son linealmente independientes.
*   **Expresar $\vec{v_4}$ como combinación lineal:** De la última fila: $-4\alpha_3 - 4\alpha_4 = 0 \implies \alpha_3 = -\alpha_4$. De la segunda fila: $-\alpha_2 + 3\alpha_3 + 2\alpha_4 = 0 \implies -\alpha_2 - 3\alpha_4 + 2\alpha_4 = 0 \implies \alpha_2 = -\alpha_4$. De la primera fila: $\alpha_1 + \alpha_2 + 4\alpha_4 = 0 \implies \alpha_1 - \alpha_4 + 4\alpha_4 = 0 \implies \alpha_1 = -3\alpha_4$.
    Si $\alpha_4 = 1$, entonces $\alpha_1 = -3, \alpha_2 = -1, \alpha_3 = -1$.
    $-3\vec{v_1} - \vec{v_2} - \vec{v_3} + \vec{v_4} = \vec{0} \implies \vec{v_4} = 3\vec{v_1} + \vec{v_2} + \vec{v_3}$.

**e) 𝑉 = {𝑝 ∈ 𝐾[𝑋]: 𝑝 = 0 ó 𝑔𝑟(𝑝) ≤ 2}
𝑣1 = 𝑝(𝑥) = 2𝑥
2 + 𝑥 + 1 𝑣2 = 𝑔(𝑥) = 3𝑥
2 + 𝑥 − 5 𝑣3 = ℎ(𝑥) = 𝑥 + 13**

*   **Combinación Lineal:** $\alpha_1(2x^2 + x + 1) + \alpha_2(3x^2 + x - 5) + \alpha_3(x + 13) = 0$
*   **Sistema:**
    *   $2\alpha_1 + 3\alpha_2 = 0$
    *   $\alpha_1 + \alpha_2 + \alpha_3 = 0$
    *   $\alpha_1 - 5\alpha_2 + 13\alpha_3 = 0$
*   **Matriz:**
    $A = \begin{pmatrix} 2 & 3 & 0 \\ 1 & 1 & 1 \\ 1 & -5 & 13 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & 1 & 1 \\ 2 & 3 & 0 \\ 1 & -5 & 13 \end{pmatrix} \xrightarrow{F_2-2F_1, F_3-F_1} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & -2 \\ 0 & -6 & 12 \end{pmatrix} \xrightarrow{F_3+6F_2} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & -2 \\ 0 & 0 & 0 \end{pmatrix}$
*   **Análisis:** El sistema tiene rango 2 y 3 incógnitas, por lo que es compatible indeterminado (infinitas soluciones). Los vectores son linealmente dependientes.
*   **Subconjunto L.I.:** Las primeras dos columnas tienen pivote, por lo que $p(x)$ y $g(x)$ son linealmente independientes.
*   **Expresar $h(x)$ como combinación lineal:** De la última fila: $\alpha_3$ es libre. De la segunda fila: $\alpha_2 - 2\alpha_3 = 0 \implies \alpha_2 = 2\alpha_3$. De la primera fila: $\alpha_1 + \alpha_2 + \alpha_3 = 0 \implies \alpha_1 + 2\alpha_3 + \alpha_3 = 0 \implies \alpha_1 = -3\alpha_3$.
    Si $\alpha_3 = 1$, entonces $\alpha_1 = -3, \alpha_2 = 2$.
    $-3p(x) + 2g(x) + h(x) = 0 \implies h(x) = 3p(x) - 2g(x)$.

---

## Ejercicio 3: Base y Coordenadas

**Método:** Para comprobar que los vectores $v_1, \dots, v_n$ forman una base de $V$, verificar que son linealmente independientes y que generan $V$. Para hallar las coordenadas de $v$ en esta base, resolver el sistema $v = \alpha_1 v_1 + \dots + \alpha_n v_n$ para encontrar los escalares $\alpha_i$.

**a) 𝑉 = ℝ3
𝑣1 = (1,1,1) 𝑣2 = (1,1,2) 𝑣3 = (1,2,3) 𝑣 = (𝑎, 𝑏, 𝑐)**

*   **Independencia Lineal:**
    $A = \begin{pmatrix} 1 & 1 & 1 \\ 1 & 1 & 2 \\ 1 & 2 & 3 \end{pmatrix} \xrightarrow{F_2-F_1, F_3-F_1} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 0 & 1 \\ 0 & 1 & 2 \end{pmatrix} \xrightarrow{F_2 \leftrightarrow F_3} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & 2 \\ 0 & 0 & 1 \end{pmatrix}$
    Como el rango de la matriz es 3, los vectores son linealmente independientes.
*   **Generación:** Como tenemos 3 vectores linealmente independientes en $\mathbb{R}^3$, forman una base.
*   **Coordenadas de $v$:**
    $(a, b, c) = \alpha_1(1,1,1) + \alpha_2(1,1,2) + \alpha_3(1,2,3)$
    *   $\alpha_1 + \alpha_2 + \alpha_3 = a$
    *   $\alpha_1 + \alpha_2 + 2\alpha_3 = b$
    *   $\alpha_1 + 2\alpha_2 + 3\alpha_3 = c$
    $A' = \begin{pmatrix} 1 & 1 & 1 & | & a \\ 1 & 1 & 2 & | & b \\ 1 & 2 & 3 & | & c \end{pmatrix} \xrightarrow{F_2-F_1, F_3-F_1} \begin{pmatrix} 1 & 1 & 1 & | & a \\ 0 & 0 & 1 & | & b-a \\ 0 & 1 & 2 & | & c-a \end{pmatrix} \xrightarrow{F_2 \leftrightarrow F_3} \begin{pmatrix} 1 & 1 & 1 & | & a \\ 0 & 1 & 2 & | & c-a \\ 0 & 0 & 1 & | & b-a \end{pmatrix}$
    *   $\alpha_3 = b - a$
    *   $\alpha_2 + 2\alpha_3 = c - a \implies \alpha_2 = c - a - 2(b - a) = a - 2b + c$
    *   $\alpha_1 + \alpha_2 + \alpha_3 = a \implies \alpha_1 = a - (a - 2b + c) - (b - a) = a + b - c$
*   **Coordenadas:** $(a+b-c, a-2b+c, b-a)$.

**b) 𝑉 = ℝ3
𝑣1 = (2,1, −3) 𝑣2 = (3,2, −5) 𝑣3 = (1, −1,1) 𝑣 = (𝑎, 𝑏, 𝑐)**

*   **Independencia Lineal:**
    $A = \begin{pmatrix} 2 & 3 & 1 \\ 1 & 2 & -1 \\ -3 & -5 & 1 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & 2 & -1 \\ 2 & 3 & 1 \\ -3 & -5 & 1 \end{pmatrix} \xrightarrow{F_2-2F_1, F_3+3F_1} \begin{pmatrix} 1 & 2 & -1 \\ 0 & -1 & 3 \\ 0 & 1 & -2 \end{pmatrix} \xrightarrow{F_3+F_2} \begin{pmatrix} 1 & 2 & -1 \\ 0 & -1 & 3 \\ 0 & 0 & 1 \end{pmatrix}$
    Como el rango de la matriz es 3, los vectores son linealmente independientes.
*   **Generación:** Como tenemos 3 vectores linealmente independientes en $\mathbb{R}^3$, forman una base.
*   **Coordenadas de $v$:**
    $(a, b, c) = \alpha_1(2,1,-3) + \alpha_2(3,2,-5) + \alpha_3(1,-1,1)$
    *   $2\alpha_1 + 3\alpha_2 + \alpha_3 = a$
    *   $\alpha_1 + 2\alpha_2 - \alpha_3 = b$
    *   $-3\alpha_1 - 5\alpha_2 + \alpha_3 = c$
    $A' = \begin{pmatrix} 2 & 3 & 1 & | & a \\ 1 & 2 & -1 & | & b \\ -3 & -5 & 1 & | & c \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & 2 & -1 & | & b \\ 2 & 3 & 1 & | & a \\ -3 & -5 & 1 & | & c \end{pmatrix} \xrightarrow{F_2-2F_1, F_3+3F_1} \begin{pmatrix} 1 & 2 & -1 & | & b \\ 0 & -1 & 3 & | & a-2b \\ 0 & 1 & -2 & | & c+3b \end{pmatrix} \xrightarrow{F_3+F_2} \begin{pmatrix} 1 & 2 & -1 & | & b \\ 0 & -1 & 3 & | & a-2b \\ 0 & 0 & 1 & | & a+b+c \end{pmatrix}$
    *   $\alpha_3 = a + b + c$
    *   $-\alpha_2 + 3\alpha_3 = a - 2b \implies \alpha_2 = 3(a+b+c) - (a-2b) = 2a + 5b + 3c$
    *   $\alpha_1 + 2\alpha_2 - \alpha_3 = b \implies \alpha_1 = b - 2(2a+5b+3c) + (a+b+c) = -3a - 8b - 5c$
*   **Coordenadas:** $(-3a-8b-5c, 2a+5b+3c, a+b+c)$.

**c) 𝑉 = ℝ4
𝑣1 = (1,2, −1, −2) 𝑣2 = (2,3,0, −1) 𝑣3 = (1,2,1,4) 𝑣4 = (1,3, −1,0)
𝑣 = (𝑎, 𝑏, 𝑐, 𝑑)**

*   **Independencia Lineal:**
    $A = \begin{pmatrix} 1 & 2 & 1 & 1 \\ 2 & 3 & 2 & 3 \\ -1 & 0 & 1 & -1 \\ -2 & -1 & 4 & 0 \end{pmatrix} \xrightarrow{F_2-2F_1, F_3+F_1, F_4+2F_1} \begin{pmatrix} 1 & 2 & 1 & 1 \\ 0 & -1 & 0 & 1 \\ 0 & 2 & 2 & 0 \\ 0 & 3 & 6 & 2 \end{pmatrix} \xrightarrow{F_3+2F_2, F_4+3F_2} \begin{pmatrix} 1 & 2 & 1 & 1 \\ 0 & -1 & 0 & 1 \\ 0 & 0 & 2 & 2 \\ 0 & 0 & 6 & 5 \end{pmatrix} \xrightarrow{F_4-3F_3} \begin{pmatrix} 1 & 2 & 1 & 1 \\ 0 & -1 & 0 & 1 \\ 0 & 0 & 2 & 2 \\ 0 & 0 & 0 & -1 \end{pmatrix}$
    Como el rango de la matriz es 4, los vectores son linealmente independientes.
*   **Generación:** Como tenemos 4 vectores linealmente independientes en $\mathbb{R}^4$, forman una base.
*   **Coordenadas de $v$:**
    $(a, b, c, d) = \alpha_1(1,2,-1,-2) + \alpha_2(2,3,0,-1) + \alpha_3(1,2,1,4) + \alpha_4(1,3,-1,0)$
    *   $\alpha_1 + 2\alpha_2 + \alpha_3 + \alpha_4 = a$
    *   $2\alpha_1 + 3\alpha_2 + 2\alpha_3 + 3\alpha_4 = b$
    *   $-\alpha_1 + \alpha_3 - \alpha_4 = c$
    *   $-2\alpha_1 - \alpha_2 + 4\alpha_3 = d$
    $A' = \begin{pmatrix} 1 & 2 & 1 & 1 & | & a \\ 2 & 3 & 2 & 3 & | & b \\ -1 & 0 & 1 & -1 & | & c \\ -2 & -1 & 4 & 0 & | & d \end{pmatrix} \xrightarrow{F_2-2F_1, F_3+F_1, F_4+2F_1} \begin{pmatrix} 1 & 2 & 1 & 1 & | & a \\ 0 & -1 & 0 & 1 & | & b-2a \\ 0 & 2 & 2 & 0 & | & c+a \\ 0 & 3 & 6 & 2 & | & d+2a \end{pmatrix} \xrightarrow{F_3+2F_2, F_4+3F_2} \begin{pmatrix} 1 & 2 & 1 & 1 & | & a \\ 0 & -1 & 0 & 1 & | & b-2a \\ 0 & 0 & 2 & 2 & | & c+2b-3a \\ 0 & 0 & 6 & 5 & | & d+5b-4a \end{pmatrix} \xrightarrow{F_4-3F_3} \begin{pmatrix} 1 & 2 & 1 & 1 & | & a \\ 0 & -1 & 0 & 1 & | & b-2a \\ 0 & 0 & 2 & 2 & | & c+2b-3a \\ 0 & 0 & 0 & -1 & | & d-b+5a-3c \end{pmatrix}$
    *   $-\alpha_4 = d - b + 5a - 3c \implies \alpha_4 = -d + b - 5a + 3c$
    *   $2\alpha_3 + 2\alpha_4 = c + 2b - 3a \implies 2\alpha_3 = c + 2b - 3a - 2(-d + b - 5a + 3c) = 7a - 5c + 2d \implies \alpha_3 = \frac{7}{2}a - \frac{5}{2}c + d$
    *   $-\alpha_2 + \alpha_4 = b - 2a \implies -\alpha_2 = b - 2a - (-d + b - 5a + 3c) = 3a - 3c + d \implies \alpha_2 = -3a + 3c - d$
    *   $\alpha_1 + 2\alpha_2 + \alpha_3 + \alpha_4 = a \implies \alpha_1 = a - 2(-3a+3c-d) - (\frac{7}{2}a - \frac{5}{2}c + d) - (-d+b-5a+3c) = \frac{15}{2}a - \frac{13}{2}c + 2d - b$
*   **Coordenadas:** $(\frac{15}{2}a - \frac{13}{2}c + 2d - b, -3a + 3c - d, \frac{7}{2}a - \frac{5}{2}c + d, -d + b - 5a + 3c)$.

---

## Ejercicio 4: Conjuntos Generadores

**Método:** Verificar si el span del conjunto de vectores es igual a $\mathbb{R}^3$. Esto se puede hacer comprobando si el rango de la matriz formada por los vectores es 3.

**a) {(1,1,1); (1,2,2); (1,3,3)}**

*   **Matriz:** $A = \begin{pmatrix} 1 & 1 & 1 \\ 1 & 2 & 3 \\ 1 & 2 & 3 \end{pmatrix} \xrightarrow{F_2-F_1, F_3-F_1} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & 2 \\ 0 & 1 & 2 \end{pmatrix} \xrightarrow{F_3-F_2} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & 2 \\ 0 & 0 & 0 \end{pmatrix}$
*   **Análisis:** El rango de la matriz es 2, que es menor que 3.
*   **Conclusión:** El conjunto no genera $\mathbb{R}^3$.

**b) {(1,0,1); (1, −1,1); (3,5,3); (2,3,2)}**

*   **Matriz:** $A = \begin{pmatrix} 1 & 1 & 3 & 2 \\ 0 & -1 & 5 & 3 \\ 1 & 1 & 3 & 2 \end{pmatrix} \xrightarrow{F_3-F_1} \begin{pmatrix} 1 & 1 & 3 & 2 \\ 0 & -1 & 5 & 3 \\ 0 & 0 & 0 & 0 \end{pmatrix}$
*   **Análisis:** El rango de la matriz es 2, que es menor que 3.
*   **Conclusión:** El conjunto no genera $\mathbb{R}^3$.

---

## Ejercicio 5: Transformación Lineal y Dependencia Lineal

**Método:** Probar que si $A$ es inversible y $v_1, \dots, v_k$ son L.I., entonces $Av_1, \dots, Av_k$ también son L.I.

*   **Hipótesis:** $A$ es inversible, $v_1, \dots, v_k$ son L.I.
*   **Tesis:** $Av_1, \dots, Av_k$ son L.I.
*   **Prueba:** Consideremos la combinación lineal $\alpha_1 Av_1 + \dots + \alpha_k Av_k = 0$.
    Podemos reescribir esto como $A(\alpha_1 v_1 + \dots + \alpha_k v_k) = 0$.
    Como $A$ es inversible, podemos multiplicar por $A^{-1}$ a la izquierda: $A^{-1}A(\alpha_1 v_1 + \dots + \alpha_k v_k) = A^{-1}0$.
    Esto simplifica a $\alpha_1 v_1 + \dots + \alpha_k v_k = 0$.
    Como $v_1, \dots, v_k$ son L.I., la única solución es $\alpha_1 = \dots = \alpha_k = 0$.
    Por lo tanto, $Av_1, \dots, Av_k$ son L.I.

---

## Ejercicio 6: Combinación Lineal y Dependencia Lineal

**Método:** Probar que si $u, v, w$ son L.I., entonces $u+v, v+2w, -u+v+w$ también son L.I.

*   **Hipótesis:** $u, v, w$ son L.I.
*   **Tesis:** $u+v, v+2w, -u+v+w$ son L.I.
*   **Prueba:** Consideremos la combinación lineal $\alpha(u+v) + \beta(v+2w) + \gamma(-u+v+w) = 0$.
    Reagrupando términos: $(\alpha - \gamma)u + (\alpha + \beta + \gamma)v + (2\beta + \gamma)w = 0$.
    Como $u, v, w$ son L.I., los coeficientes deben ser cero:
    *   $\alpha - \gamma = 0$
    *   $\alpha + \beta + \gamma = 0$
    *   $2\beta + \gamma = 0$
    De la primera ecuación, $\alpha = \gamma$. Sustituyendo en la segunda: $\gamma + \beta + \gamma = 0 \implies \beta = -2\gamma$. Sustituyendo en la tercera: $2(-2\gamma) + \gamma = 0 \implies -3\gamma = 0 \implies \gamma = 0$.
    Entonces, $\alpha = 0$ y $\beta = 0$.
    Por lo tanto, la única solución es $\alpha = \beta = \gamma = 0$, lo que significa que $u+v, v+2w, -u+v+w$ son L.I.

---

## Ejercicio 7: Valor de k para Combinación Lineal e Independencia Lineal

**a) El vector (1,2,0) sea combinación lineal del conjunto de vectores {(2,1, −1); (2,1 + 𝑘, 𝑘); (2,2,1)}.**

*   **Método:** Resolver el sistema $(1,2,0) = \alpha(2,1,-1) + \beta(2,1+k,k) + \gamma(2,2,1)$ y encontrar el valor de $k$ para que el sistema sea compatible.
*   **Sistema:**
    *   $2\alpha + 2\beta + 2\gamma = 1$
    *   $\alpha + (1+k)\beta + 2\gamma = 2$
    *   $-\alpha + k\beta + \gamma = 0$
*   **Matriz Ampliada:**
    
    $\begin{pmatrix} 2 & 2 & 2 & | & 1 \\ 1 & 1+k & 2 & | & 2 \\ -1 & k & 1 & | & 0 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & 1+k & 2 & | & 2 \\ 2 & 2 & 2 & | & 1 \\ -1 & k & 1 & | & 0 \end{pmatrix} \xrightarrow{F_2-2F_1, F_3+F_1} \begin{pmatrix} 1 & 1+k & 2 & | & 2 \\ 0 & -2k & -2 & | & -3 \\ 0 & 2k+1 & 3 & | & 2 \end{pmatrix} \xrightarrow{F_3 + \frac{2k+1}{2k}F_2} \begin{pmatrix} 1 & 1+k & 2 & | & 2 \\ 0 & -2k & -2 & | & -3 \\ 0 & 0 & 3 - \frac{2k+1}{k} & | & 2 - \frac{3(2k+1)}{2k} \end{pmatrix}$
    
*   **Análisis:** Para que el sistema tenga solución, la última fila no puede ser de la forma $(0 \ 0 \ 0 \ | \ c)$ con $c \neq 0$.  Por lo tanto, necesitamos que $3 - \frac{2k+1}{k} \neq 0$ o $2 - \frac{3(2k+1)}{2k} = 0$.
    *   Caso 1: $3 - \frac{2k+1}{k} = 0 \implies 3k = 2k + 1 \implies k = 1$.
    *   Caso 2: $2 - \frac{3(2k+1)}{2k} = 0 \implies 4k = 6k + 3 \implies -2k = 3 \implies k = -\frac{3}{2}$.
    Si $k=1$, la matriz es $\begin{pmatrix} 1 & 2 & 2 & | & 2 \\ 0 & -2 & -2 & | & -3 \\ 0 & 0 & 0 & | & -1/2 \end{pmatrix}$, lo cual es incompatible.
    Si $k=-\frac{3}{2}$, la matriz es $\begin{pmatrix} 1 & -1/2 & 2 & | & 2 \\ 0 & 3 & -2 & | & -3 \\ 0 & 0 & 0 & | & 0 \end{pmatrix}$, lo cual es compatible.
*   **Conclusión:** El vector (1,2,0) es combinación lineal de los otros vectores si $k = -\frac{3}{2}$.


**b) El conjunto de vectores {(0, 𝑘, 𝑘, 𝑘); (3,1,1, 𝑘); (𝑘, 0,0,2); (𝑘, 𝑘, 3, 𝑘)} sea linealmente independiente.**

*   **Método:** Calcular el determinante de la matriz formada por los vectores y encontrar los valores de $k$ para los cuales el determinante es diferente de cero.
*   **Matriz:**

    $$A = \begin{pmatrix}
    0 & 3 & k & k \\
    k & 1 & 0 & k \\
    k & 1 & 0 & 3 \\
    k & k & 2 & k
    \end{pmatrix}$$

*   **Determinante:**

    $\det(A) = -3 \begin{vmatrix} k & 0 & k \\ k & 0 & 3 \\ k & 2 & k \end{vmatrix} + k \begin{vmatrix} k & 3 & k \\ k & 1 & 3 \\ k & k & k \end{vmatrix} - k \begin{vmatrix} k & 3 & k \\ k & 1 & 0 \\ k & k & 2 \end{vmatrix}$

    $\det(A) = -3(-2k(3-k)) + k(k(k-k^2) - 3(k^2-3k) + k(k^2-k)) - k(k(2-0) - 3(2k-0) + k(k^2-k))$

    $\det(A) = 6k(3-k) + k(k^2 - 3k^2 + 9k + k^3 - k^2) - k(2k - 6k + k^3 - k^2)$

    $\det(A) = 18k - 6k^2 + k(k^3 - 4k^2 + 9k) - k(2k - 6k + k^3 - k^2)$

    $\det(A) = 18k - 6k^2 + k^4 - 4k^3 + 9k^2 - 2k^2 + 4k^2 - k^4 + k^3$

    $\det(A) = 18k - 6k^2 - 3k^3 + 11k^2 - 4k^2 + k^3$

    $\det(A) = -2k^3 + k^2 + 18k = k(-2k^2 - 3k^3 + 5k^2 + 18) = k(-2k^2 + 5k + 18)$

*   **Condición para Independencia Lineal:** $\det(A) \neq 0 \implies k(-2k^2 + 5k + 18) \neq 0$.
    *   $k \neq 0$
    *   $-2k^2 + 5k + 18 \neq 0 \implies k = \frac{-5 \pm \sqrt{25 - 4(-2)(18)}}{-4} = \frac{-5 \pm \sqrt{25 + 144}}{-4} = \frac{-5 \pm \sqrt{169}}{-4} = \frac{-5 \pm 13}{-4}$
        *   $k_1 = \frac{-5 + 13}{-4} = \frac{8}{-4} = -2$
        *   $k_2 = \frac{-5 - 13}{-4} = \frac{-18}{-4} = \frac{9}{2}$
*   **Conclusión:** El conjunto de vectores es linealmente independiente si $k \neq 0$, $k \neq -2$ y $k \neq \frac{9}{2}$.




EJERCICIO 8 

Para determinar los valores de $k$ para los cuales el conjunto $B = \{u - 2w, u + v, kw - u + v\}$ es linealmente independiente (L.I.), debemos plantear la ecuación de dependencia lineal y ver para qué valores de $k$ la única solución es la trivial (todos los escalares igPara determinar los valores de $k$ para los cuales el conjunto $B = \{u - 2w, u + v, kw - u + v\}$ es linealmente independiente (L.I.), debemos plantear la ecuación de dependencia lineal y ver para qué valores de $k$ la única solución es la trivial (todos los escalares iguales a cero).

Basándonos en la definición de independencia lineal explicada en la sección 5 de la nota [[Espacios Vectoriales]], un conjunto de vectores $\{v_1, v_2, v_3\}$ es L.I. si la única solución de la ecuación $\alpha_1 v_1 + \alpha_2 v_2 + \alpha_3 v_3 = \vec{0}$ es $\alpha_1 = \alpha_2 = \alpha_3 = 0$.

Aplicamos esto a nuestro conjunto $B$:
Buscamos escalares $\alpha_1, \alpha_2, \alpha_3$ tales que:
$\alpha_1 (u - 2w) + \alpha_2 (u + v) + \alpha_3 (kw - u + v) = \vec{0}$

Ahora, reagrupamos los términos según los vectores $u, v, w$:
$(\alpha_1 + \alpha_2 - \alpha_3) u + (\alpha_2 + \alpha_3) v + (-2\alpha_1 + k\alpha_3) w = \vec{0}$

Para que esta ecuación se cumpla, y asumiendo que los vectores originales $\{u, v, w\}$ son linealmente independientes (lo cual es una suposición estándar en este tipo de ejercicios, a menos que se indique lo contrario), los coeficientes de $u, v, w$ deben ser todos cero. Esto nos da el siguiente sistema de ecuaciones homogéneo para $\alpha_1, \alpha_2, \alpha_3$:

1.  $\alpha_1 + \alpha_2 - \alpha_3 = 0$
2.  $\alpha_2 + \alpha_3 = 0$
3.  $-2\alpha_1 + 0\alpha_2 + k\alpha_3 = 0$

El conjunto $B$ será linealmente independiente si y solo si este sistema de ecuaciones tiene como única solución la trivial ($\alpha_1 = 0, \alpha_2 = 0, \alpha_3 = 0$). Como se explica en la sección 6 de [[Espacios Vectoriales]], para un sistema homogéneo cuadrado, esto ocurre si y solo si el determinante de la matriz de coeficientes es distinto de cero.

La matriz de coeficientes del sistema es:
$A = \begin{pmatrix} 1 & 1 & -1 \\ 0 & 1 & 1 \\ -2 & 0 & k \end{pmatrix}$

Calculamos su determinante:
$\det(A) = 1 \cdot \det\begin{pmatrix} 1 & 1 \\ 0 & k \end{pmatrix} - 1 \cdot \det\begin{pmatrix} 0 & 1 \\ -2 & k \end{pmatrix} + (-1) \cdot \det\begin{pmatrix} 0 & 1 \\ -2 & 0 \end{pmatrix}$
$\det(A) = 1(1 \cdot k - 1 \cdot 0) - 1(0 \cdot k - 1 \cdot (-2)) - 1(0 \cdot 0 - 1 \cdot (-2))$
$\det(A) = 1(k) - 1(2) - 1(2)$
$\det(A) = k - 2 - 2$
$\det(A) = k - 4$

Para que el conjunto $B$ sea linealmente independiente, el determinante debe ser distinto de cero:
$\det(A) \neq 0$
$k - 4 \neq 0$
$k \neq 4$

Por lo tanto, el conjunto $B = \{u - 2w, u + v, kw - u + v\}$ es linealmente independiente para todos los valores de $k$ tales que $k \neq 4$.uales a cero).

Basándonos en la definición de independencia lineal explicada en la sección 5 de la nota [[Espacios Vectoriales]], un conjunto de vectores $\{v_1, v_2, v_3\}$ es L.I. si la única solución de la ecuación $\alpha_1 v_1 + \alpha_2 v_2 + \alpha_3 v_3 = \vec{0}$ es $\alpha_1 = \alpha_2 = \alpha_3 = 0$.

Aplicamos esto a nuestro conjunto $B$:
Buscamos escalares $\alpha_1, \alpha_2, \alpha_3$ tales que:
$\alpha_1 (u - 2w) + \alpha_2 (u + v) + \alpha_3 (kw - u + v) = \vec{0}$

Ahora, reagrupamos los términos según los vectores $u, v, w$:
$(\alpha_1 + \alpha_2 - \alpha_3) u + (\alpha_2 + \alpha_3) v + (-2\alpha_1 + k\alpha_3) w = \vec{0}$

Para que esta ecuación se cumpla, y asumiendo que los vectores originales $\{u, v, w\}$ son linealmente independientes (lo cual es una suposición estándar en este tipo de ejercicios, a menos que se indique lo contrario), los coeficientes de $u, v, w$ deben ser todos cero. Esto nos da el siguiente sistema de ecuaciones homogéneo para $\alpha_1, \alpha_2, \alpha_3$:

1.  $\alpha_1 + \alpha_2 - \alpha_3 = 0$
2.  $\alpha_2 + \alpha_3 = 0$
3.  $-2\alpha_1 + 0\alpha_2 + k\alpha_3 = 0$

El conjunto $B$ será linealmente independiente si y solo si este sistema de ecuaciones tiene como única solución la trivial ($\alpha_1 = 0, \alpha_2 = 0, \alpha_3 = 0$). Como se explica en la sección 6 de [[Espacios Vectoriales]], para un sistema homogéneo cuadrado, esto ocurre si y solo si el determinante de la matriz de coeficientes es distinto de cero.

La matriz de coeficientes del sistema es:
$A = \begin{pmatrix} 1 & 1 & -1 \\ 0 & 1 & 1 \\ -2 & 0 & k \end{pmatrix}$

Calculamos su determinante:
$\det(A) = 1 \cdot \det\begin{pmatrix} 1 & 1 \\ 0 & k \end{pmatrix} - 1 \cdot \det\begin{pmatrix} 0 & 1 \\ -2 & k \end{pmatrix} + (-1) \cdot \det\begin{pmatrix} 0 & 1 \\ -2 & 0 \end{pmatrix}$
$\det(A) = 1(1 \cdot k - 1 \cdot 0) - 1(0 \cdot k - 1 \cdot (-2)) - 1(0 \cdot 0 - 1 \cdot (-2))$
$\det(A) = 1(k) - 1(2) - 1(2)$
$\det(A) = k - 2 - 2$
$\det(A) = k - 4$

Para que el conjunto $B$ sea linealmente independiente, el determinante debe ser distinto de cero:
$\det(A) \neq 0$
$k - 4 \neq 0$
$k \neq 4$

Por lo tanto, el conjunto $B = \{u - 2w, u + v, kw - u + v\}$ es linealmente independiente para todos los valores de $k$ tales que $k \neq 4$.