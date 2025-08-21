¡Absolutamente! Con la información que te proporcioné y los apuntes que me has dado, puedo ayudarte a resolver los ejercicios.

**Estrategia:**

1.  **Identificar los ejercicios más importantes:** Dada la limitación de tiempo, te indicaré cuáles ejercicios son fundamentales para comprender los conceptos clave.
2.  **Resolver los ejercicios seleccionados:** Resolveré estos ejercicios paso a paso, explicando cada paso y el razonamiento detrás de él.
3.  **Ofrecer orientación para los ejercicios restantes:** Te daré indicaciones y sugerencias para que puedas abordar los ejercicios restantes por tu cuenta, consolidando así tu aprendizaje.

**Ejercicios Más Importantes:**

Considerando la información que me proporcionaste, los ejercicios más importantes para que te enfoques son:

*   **Ejercicio 3:** Hallar bases ortogonales y ortonormales. Este ejercicio te ayudará a comprender la diferencia entre ambos tipos de bases y cómo construirlas.
*   **Ejercicio 5:** Usar el hecho que 𝑆 es un hiperplano, determinar la proyección sobre 𝑆 de los vectores 𝑣 ∈ ℝ𝑛 hallando primero su proyección sobre 𝑆⊥. Este ejercicio es clave para entender cómo descomponer un vector en sus componentes ortogonales y cómo usar el complemento ortogonal para simplificar los cálculos.
*   **Ejercicio 6:** En los siguientes casos hallar la matriz de proyección 𝑃𝑆 = 𝐴(𝐴𝑡𝐴)−1𝐴𝑡 y calcular la proyección del vector 𝑣 sobre el subespacio 𝑆, respectivamente. Este ejercicio te permitirá aplicar la fórmula de la matriz de proyección y entender cómo se utiliza para proyectar vectores sobre subespacios.
*   **Ejercicio 13:** Se define el determinante de una TL 𝑡 como el determinante de [𝑡]𝐵 para cualquier base 𝐵. Análogamente puede definirse la traza de 𝑡. Sea 𝐵 = {𝑣1, 𝑣2, 𝑣3} una base ortonormal de ℝ3. Este ejercicio te ayudará a comprender las propiedades de las transformaciones ortogonales y cómo se relacionan con las reflexiones y rotaciones.

**Resolución de los Ejercicios Seleccionados:**

**Ejercicio 3: Hallar bases ortogonales y ortonormales de los siguientes subespacios.**

**a) 𝑆 = {(𝑥, 𝑦, 𝑧) ∈ ℝ³ : 𝑥 + 3𝑦 − 𝑧 = 0}**

1.  **Encontrar una base para S:**
    *   La ecuación $x + 3y - z = 0$ define un plano en $ℝ³$. Podemos expresar $z$ en términos de $x$ e $y$: $z = x + 3y$.
    *   Entonces, los vectores en $S$ son de la forma $(x, y, x + 3y) = x(1, 0, 1) + y(0, 1, 3)$.
    *   Una base para $S$ es $B = \{(1, 0, 1), (0, 1, 3)\}$.

2.  **Ortogonalizar la base (Gram-Schmidt):**
    *   $w_1 = v_1 = (1, 0, 1)$
    *   $w_2 = v_2 - Proy_{⟨w_1⟩}(v_2) = (0, 1, 3) - \frac{(0, 1, 3) \cdot (1, 0, 1)}{||(1, 0, 1)||^2}(1, 0, 1) = (0, 1, 3) - \frac{3}{2}(1, 0, 1) = (-\frac{3}{2}, 1, \frac{3}{2})$
    *   Una base ortogonal para $S$ es $B_o = \{(1, 0, 1), (-\frac{3}{2}, 1, \frac{3}{2})\}$. Para simplificar, podemos multiplicar el segundo vector por 2: $B_o = \{(1, 0, 1), (-3, 2, 3)\}$.

3.  **Ortonormalizar la base:**
    *   Normalizar $w_1$: $||w_1|| = \sqrt{1^2 + 0^2 + 1^2} = \sqrt{2}$. Entonces, $u_1 = \frac{w_1}{||w_1||} = (\frac{1}{\sqrt{2}}, 0, \frac{1}{\sqrt{2}})$.
    *   Normalizar $w_2$: $||w_2|| = \sqrt{(-3)^2 + 2^2 + 3^2} = \sqrt{22}$. Entonces, $u_2 = \frac{w_2}{||w_2||} = (-\frac{3}{\sqrt{22}}, \frac{2}{\sqrt{22}}, \frac{3}{\sqrt{22}})$.
    *   Una base ortonormal para $S$ es $B_{on} = \{(\frac{1}{\sqrt{2}}, 0, \frac{1}{\sqrt{2}}), (-\frac{3}{\sqrt{22}}, \frac{2}{\sqrt{22}}, \frac{3}{\sqrt{22}})\}$.

**b) 𝑆 = {(𝑥, 𝑦, 𝑧) ∈ ℝ³ : 𝑥 = 𝛼, 𝑦 = −𝛼, 𝑧 = 3𝛼}**

1.  **Encontrar una base para S:**
    *   Los vectores en $S$ son de la forma $(α, -α, 3α) = α(1, -1, 3)$.
    *   Una base para $S$ es $B = \{(1, -1, 3)\}$.

2.  **Ortogonalizar la base:**
    *   Como la base solo tiene un vector, ya es ortogonal.

3.  **Ortonormalizar la base:**
    *   Normalizar $v_1 = (1, -1, 3)$: $||v_1|| = \sqrt{1^2 + (-1)^2 + 3^2} = \sqrt{11}$. Entonces, $u_1 = \frac{v_1}{||v_1||} = (\frac{1}{\sqrt{11}}, -\frac{1}{\sqrt{11}}, \frac{3}{\sqrt{11}})$.
    *   Una base ortonormal para $S$ es $B_{on} = \{(\frac{1}{\sqrt{11}}, -\frac{1}{\sqrt{11}}, \frac{3}{\sqrt{11}})\}$.

**Ejercicio 5: Usando el hecho que 𝑆 es un hiperplano, determinar la proyección sobre 𝑆 de los vectores 𝑣 ∈ ℝ𝑛 hallando primero su proyección sobre 𝑆⊥.**

**a) 𝑆 = {(𝑥, 𝑦, 𝑧) ∈ ℝ³ : 𝑥 + 𝑦 + 𝑧 = 0}, 𝑣 = (2,1,1)**

1.  **Encontrar una base para S^⊥:**
    *   $S$ es el plano definido por $x + y + z = 0$. El vector normal a este plano es $(1, 1, 1)$.
    *   Por lo tanto, $S^⊥ = \langle (1, 1, 1) \rangle$.

2.  **Proyectar v sobre S^⊥:**
    *   $Proy_{S^⊥}(v) = \frac{v \cdot (1, 1, 1)}{||(1, 1, 1)||^2}(1, 1, 1) = \frac{(2, 1, 1) \cdot (1, 1, 1)}{1^2 + 1^2 + 1^2}(1, 1, 1) = \frac{4}{3}(1, 1, 1) = (\frac{4}{3}, \frac{4}{3}, \frac{4}{3})$

3.  **Proyectar v sobre S:**
    *   $Proy_S(v) = v - Proy_{S^⊥}(v) = (2, 1, 1) - (\frac{4}{3}, \frac{4}{3}, \frac{4}{3}) = (\frac{2}{3}, -\frac{1}{3}, -\frac{1}{3})$

**b) 𝑆 = {(𝑥, 𝑦, 𝑧,𝑡) ∈ ℝ⁴ : 𝑥 + 𝑦 + 𝑧 + 𝑡 = 0}, 𝑣 = (1,1,1,1)**

1.  **Encontrar una base para S^⊥:**
    *   $S$ es el hiperplano definido por $x + y + z + t = 0$. El vector normal a este hiperplano es $(1, 1, 1, 1)$.
    *   Por lo tanto, $S^⊥ = \langle (1, 1, 1, 1) \rangle$.

2.  **Proyectar v sobre S^⊥:**
    *   $Proy_{S^⊥}(v) = \frac{v \cdot (1, 1, 1, 1)}{||(1, 1, 1, 1)||^2}(1, 1, 1, 1) = \frac{(1, 1, 1, 1) \cdot (1, 1, 1, 1)}{1^2 + 1^2 + 1^2 + 1^2}(1, 1, 1, 1) = \frac{4}{4}(1, 1, 1, 1) = (1, 1, 1, 1)$

3.  **Proyectar v sobre S:**
    *   $Proy_S(v) = v - Proy_{S^⊥}(v) = (1, 1, 1, 1) - (1, 1, 1, 1) = (0, 0, 0, 0)$

**c) 𝑆 = {(𝑥, 𝑦, 𝑧) ∈ ℝ³ : 𝑥 − 𝑦 + 2𝑧 = 0}, 𝑣 = (3, −1,2)**

1.  **Encontrar una base para S^⊥:**
    *   $S$ es el plano definido por $x - y + 2z = 0$. El vector normal a este plano es $(1, -1, 2)$.
    *   Por lo tanto, $S^⊥ = \langle (1, -1, 2) \rangle$.

2.  **Proyectar v sobre S^⊥:**
    *   $Proy_{S^⊥}(v) = \frac{v \cdot (1, -1, 2)}{||(1, -1, 2)||^2}(1, -1, 2) = \frac{(3, -1, 2) \cdot (1, -1, 2)}{1^2 + (-1)^2 + 2^2}(1, -1, 2) = \frac{8}{6}(1, -1, 2) = (\frac{4}{3}, -\frac{4}{3}, \frac{8}{3})$

3.  **Proyectar v sobre S:**
    *   $Proy_S(v) = v - Proy_{S^⊥}(v) = (3, -1, 2) - (\frac{4}{3}, -\frac{4}{3}, \frac{8}{3}) = (\frac{5}{3}, \frac{1}{3}, -\frac{2}{3})$

*¡Disculpa la interrupción! Continuemos con el ejercicio 6b y luego abordaremos los siguientes ejercicios en bloques de 5.

**Ejercicio 6: En los siguientes casos hallar la matriz de proyección 𝑃𝑆 = 𝐴(𝐴𝑡𝐴)−1𝐴𝑡 y calcular la proyección del vector 𝑣 sobre el subespacio 𝑆, respectivamente:**

**b) 𝑣 = (1,2,1), 𝑆 = {(𝑥, 𝑦, 𝑧) ∈ ℝ³ : 𝑥 − 𝑦 − 𝑧 = 0} (Continuación)**

Ya habíamos calculado:

*   $A = \begin{pmatrix} 1 & 1 \\ 1 & 0 \\ 0 & 1 \end{pmatrix}$
*   $(A^T A)^{-1} = \begin{pmatrix} \frac{2}{3} & -\frac{1}{3} \\ -\frac{1}{3} & \frac{2}{3} \end{pmatrix}$
*   $A^T = \begin{pmatrix} 1 & 1 & 0 \\ 1 & 0 & 1 \end{pmatrix}$

5.  **Calcular la matriz de proyección P_S:**
    *   $P_S = A(A^T A)^{-1}A^T = \begin{pmatrix} 1 & 1 \\ 1 & 0 \\ 0 & 1 \end{pmatrix} \begin{pmatrix} \frac{2}{3} & -\frac{1}{3} \\ -\frac{1}{3} & \frac{2}{3} \end{pmatrix} \begin{pmatrix} 1 & 1 & 0 \\ 1 & 0 & 1 \end{pmatrix} = \begin{pmatrix} \frac{1}{3} & \frac{1}{3} & \frac{-1}{3} \\ \frac{2}{3} & -\frac{1}{3} & -\frac{2}{3} \\ -\frac{1}{3} & \frac{2}{3} & \frac{2}{3} \end{pmatrix}$

6.  **Calcular la proyección de v sobre S:**
    *   $Proy_S(v) = P_S v = \begin{pmatrix} \frac{1}{3} & \frac{1}{3} & \frac{-1}{3} \\ \frac{2}{3} & -\frac{1}{3} & -\frac{2}{3} \\ -\frac{1}{3} & \frac{2}{3} & \frac{2}{3} \end{pmatrix} \begin{pmatrix} 1 \\ 2 \\ 1 \end{pmatrix} = \begin{pmatrix} \frac{2}{3} \\ 0 \\ 1 \end{pmatrix}$

**c) 𝑣 = (4, −1, −3,4), 𝑆 = 〈(1,1,1,1), (1,1, −1, −1), (1, −1, −1,1)〉**

1.  **Formar la matriz A:**
    *   $A = \begin{pmatrix} 1 & 1 & 1 \\ 1 & 1 & -1 \\ 1 & -1 & -1 \\ 1 & -1 & 1 \end{pmatrix}$

2.  **Calcular A^T A:**
    *   $A^T = \begin{pmatrix} 1 & 1 & 1 & 1 \\ 1 & 1 & -1 & -1 \\ 1 & -1 & -1 & 1 \end{pmatrix}$
    *   $A^T A = \begin{pmatrix} 1 & 1 & 1 & 1 \\ 1 & 1 & -1 & -1 \\ 1 & -1 & -1 & 1 \end{pmatrix} \begin{pmatrix} 1 & 1 & 1 \\ 1 & 1 & -1 \\ 1 & -1 & -1 \\ 1 & -1 & 1 \end{pmatrix} = \begin{pmatrix} 4 & 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & 4 \end{pmatrix}$

3.  **Calcular (A^T A)^-1:**
    *   $(A^T A)^{-1} = \begin{pmatrix} 4 & 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & 4 \end{pmatrix}^{-1} = \begin{pmatrix} \frac{1}{4} & 0 & 0 \\ 0 & \frac{1}{4} & 0 \\ 0 & 0 & \frac{1}{4} \end{pmatrix}$

4.  **Calcular la matriz de proyección P_S:**
    *   $P_S = A(A^T A)^{-1}A^T = \begin{pmatrix} 1 & 1 & 1 \\ 1 & 1 & -1 \\ 1 & -1 & -1 \\ 1 & -1 & 1 \end{pmatrix} \begin{pmatrix} \frac{1}{4} & 0 & 0 \\ 0 & \frac{1}{4} & 0 \\ 0 & 0 & \frac{1}{4} \end{pmatrix} \begin{pmatrix} 1 & 1 & 1 & 1 \\ 1 & 1 & -1 & -1 \\ 1 & -1 & -1 & 1 \end{pmatrix} = \begin{pmatrix} \frac{3}{4} & \frac{1}{4} & \frac{1}{4} & \frac{1}{4} \\ \frac{1}{4} & \frac{3}{4} & -\frac{1}{4} & -\frac{1}{4} \\ \frac{1}{4} & -\frac{1}{4} & \frac{3}{4} & -\frac{1}{4} \\ \frac{1}{4} & -\frac{1}{4} & -\frac{1}{4} & \frac{3}{4} \end{pmatrix}$

5.  **Calcular la proyección de v sobre S:**
    *   $Proy_S(v) = P_S v = \begin{pmatrix} \frac{3}{4} & \frac{1}{4} & \frac{1}{4} & \frac{1}{4} \\ \frac{1}{4} & \frac{3}{4} & -\frac{1}{4} & -\frac{1}{4} \\ \frac{1}{4} & -\frac{1}{4} & \frac{3}{4} & -\frac{1}{4} \\ \frac{1}{4} & -\frac{1}{4} & -\frac{1}{4} & \frac{3}{4} \end{pmatrix} \begin{pmatrix} 4 \\ -1 \\ -3 \\ 4 \end{pmatrix} = \begin{pmatrix} 2 \\ -2 \\ -4 \\ 3 \end{pmatrix}$

**Ejercicio 7: Mostrar que, en plano, la proyección sobre un vector 𝑎 fijo 𝑝𝑟𝑜𝑦𝑎(𝑥) = (𝑥⋅𝑎/‖𝑎‖2)𝑎 es una TL. Graficar. Hallar su matriz estándar.**

1.  **Mostrar que es una Transformación Lineal (TL):**
    Para que $proy_a(x)$ sea una TL, debe cumplir:
    *   $proy_a(u + v) = proy_a(u) + proy_a(v)$ para todos los vectores $u, v$.
    *   $proy_a(λu) = λ proy_a(u)$ para todo vector $u$ y escalar $λ$.

    Vamos a demostrarlo:
    *   $proy_a(u + v) = \frac{(u + v) \cdot a}{||a||^2} a = \frac{u \cdot a + v \cdot a}{||a||^2} a = \frac{u \cdot a}{||a||^2} a + \frac{v \cdot a}{||a||^2} a = proy_a(u) + proy_a(v)$
    *   $proy_a(λu) = \frac{(λu) \cdot a}{||a||^2} a = λ \frac{u \cdot a}{||a||^2} a = λ proy_a(u)$
    Como cumple ambas condiciones, $proy_a(x)$ es una TL.

2.  **Hallar la matriz estándar:**
    Sea $a = (a_1, a_2)$. La base canónica de $ℝ²$ es $\{(1, 0), (0, 1)\}$. Aplicamos la transformación a los vectores de la base canónica:
    *   $proy_a(1, 0) = \frac{(1, 0) \cdot (a_1, a_2)}{||(a_1, a_2)||^2}(a_1, a_2) = \frac{a_1}{a_1^2 + a_2^2}(a_1, a_2) = (\frac{a_1^2}{a_1^2 + a_2^2}, \frac{a_1 a_2}{a_1^2 + a_2^2})$
    *   $proy_a(0, 1) = \frac{(0, 1) \cdot (a_1, a_2)}{||(a_1, a_2)||^2}(a_1, a_2) = \frac{a_2}{a_1^2 + a_2^2}(a_1, a_2) = (\frac{a_1 a_2}{a_1^2 + a_2^2}, \frac{a_2^2}{a_1^2 + a_2^2})$

    La matriz estándar es:
    $[proy_a]_C = \begin{pmatrix} \frac{a_1^2}{a_1^2 + a_2^2} & \frac{a_1 a_2}{a_1^2 + a_2^2} \\ \frac{a_1 a_2}{a_1^2 + a_2^2} & \frac{a_2^2}{a_1^2 + a_2^2} \end{pmatrix}$

**Ejercicio 8: Determinar las proyecciones de los siguientes vectores en las direcciones dadas:**

**a) El vector 𝑢 = (2,3) en la dirección de 𝑣 = (1,4)**

*   $Proy_v(u) = \frac{u \cdot v}{||v||^2} v = \frac{(2, 3) \cdot (1, 4)}{1^2 + 4^2}(1, 4) = \frac{14}{17}(1, 4) = (\frac{14}{17}, \frac{56}{17})$

**b) El vector 𝑢 = (1,2,3) en la dirección de 𝑣 = (1,1, −1)**

*   $Proy_v(u) = \frac{u \cdot v}{||v||^2} v = \frac{(1, 2, 3) \cdot (1, 1, -1)}{1^2 + 1^2 + (-1)^2}(1, 1, -1) = \frac{0}{3}(1, 1, -1) = (0, 0, 0)$

**c) El vector 𝑢 = (−1,1,2) en la dirección de la recta 𝑙:{ 2𝑥 − 𝑦 + 3𝑧 = 0, 𝑥 + 𝑦 + 𝑧 = 0}**

1.  **Encontrar un vector director de la recta l:**
    *   Resolvemos el sistema de ecuaciones:
        $\begin{cases} 2x - y + 3z = 0 \\ x + y + z = 0 \end{cases}$
        Sumando las ecuaciones: $3x + 4z = 0 \implies x = -\frac{4}{3}z$.
        Sustituyendo en la segunda ecuación: $-\frac{4}{3}z + y + z = 0 \implies y = \frac{1}{3}z$.
        Entonces, los vectores en la recta son de la forma $(-\frac{4}{3}z, \frac{1}{3}z, z) = z(-\frac{4}{3}, \frac{1}{3}, 1)$.
        Un vector director de la recta es $v = (-4, 1, 3)$.

2.  **Proyectar u sobre v:**
    *   $Proy_v(u) = \frac{u \cdot v}{||v||^2} v = \frac{(-1, 1, 2) \cdot (-4, 1, 3)}{(-4)^2 + 1^2 + 3^2}(-4, 1, 3) = \frac{4 + 1 + 6}{16 + 1 + 9}(-4, 1, 3) = \frac{11}{26}(-4, 1, 3) = (-\frac{44}{26}, \frac{11}{26}, \frac{33}{26}) = (-\frac{22}{13}, \frac{11}{26}, \frac{33}{26})$

**Ejercicio 9: Mostrar matrices 𝐴, 3 × 3 tales que 𝐴𝑥 produzca las siguientes transformaciones:**

**a) Proyección sobre el plano 𝑥𝑦**

*   La proyección sobre el plano $xy$ transforma un vector $(x, y, z)$ en $(x, y, 0)$.
*   La matriz que realiza esta transformación es:
    $A = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0 \end{pmatrix}$

**b) Reflexión sobre el plano 𝑥𝑦**

*   La reflexión sobre el plano $xy$ transforma un vector $(x, y, z)$ en $(x, y, -z)$.
*   La matriz que realiza esta transformación es:
    $A = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & -1 \end{pmatrix}$

**c) Rotación de 90° en el plano 𝑥𝑦 dejando fijo el eje 𝑧**

*   La rotación de 90° en el plano $xy$ transforma un vector $(x, y, z)$ en $(-y, x, z)$.
*   La matriz que realiza esta transformación es:
    $A = \begin{pmatrix} 0 & -1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{pmatrix}$

**d) Todas las transformaciones anteriores, cambiando el plano 𝑥𝑦 por el plano 𝑦𝑧**

*   **Proyección sobre el plano 𝑦𝑧:** Transforma $(x, y, z)$ en $(0, y, z)$.
    $A = \begin{pmatrix} 0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}$
*   **Reflexión sobre el plano 𝑦𝑧:** Transforma $(x, y, z)$ en $(-x, y, z)$.
    $A = \begin{pmatrix} -1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}$
*   **Rotación de 90° en el plano 𝑦𝑧 dejando fijo el eje 𝑥:** Transforma $(x, y, z)$ en $(x, -z, y)$.
    $A = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 0 & -1 \\ 0 & 1 & 0 \end{pmatrix}$

**Ejercicio 10: Indicar cuales de las siguientes matrices son ortogonales:**

Para determinar si una matriz es ortogonal, debemos verificar si $AA^T = A^T A = I$. Como no me has proporcionado las matrices, no puedo resolver este ejercicio. Sin embargo, te doy el método:

1.  **Calcular la transpuesta de la matriz:** $A^T$.
2.  **Multiplicar la matriz por su transpuesta:** Calcular $AA^T$ y $A^T A$.
3.  **Verificar si el resultado es la matriz identidad:** Si $AA^T = A^T A = I$, entonces la matriz es ortogonal.

**Próximos Pasos**

Ahora que hemos resuelto los primeros 5 ejercicios (y te he dado la metodología para el 10), puedes enfocarte en estudiarlos y comprenderlos a fondo. Luego, puedes intentar resolver los ejercicios restantes, aplicando los conceptos y técnicas que hemos cubierto.

Cuando estés listo, envíame los siguientes 5 ejercicios (11-15), y te ayudaré de la misma manera. ¡Mucho éxito en tu estudio!
¡Perfecto! Continuemos con los siguientes ejercicios.

**Ejercicio 11: Sea 𝜃 una rotación de ℝ³ tal que: 𝜃(1,2,1) = (2,1,1) y 𝜃(2,1,1) = (1,1,2) Calcular 𝜃(1,1, −3), 𝜃(2,0,1), 𝜃(1,2,3)**

1.  **Verificar la ortogonalidad de la transformación:**
    Dado que $𝜃$ es una rotación, es una transformación ortogonal. Esto significa que preserva productos internos (y, por lo tanto, normas y ángulos).

2.  **Expresar los vectores en términos de una base:**
    Necesitamos expresar los vectores $(1, 1, -3)$, $(2, 0, 1)$, y $(1, 2, 3)$ como combinaciones lineales de los vectores $(1, 2, 1)$ y $(2, 1, 1)$. Sin embargo, como estos dos vectores no son linealmente independientes (no forman una base de $ℝ³$), necesitamos un tercer vector para formar una base.

3.  **Encontrar un tercer vector para la base:**
    Para encontrar un tercer vector que sea linealmente independiente con los dos dados, podemos usar el producto cruz:
    $(1, 2, 1) \times (2, 1, 1) = \begin{pmatrix} i & j & k \\ 1 & 2 & 1 \\ 2 & 1 & 1 \end{pmatrix} = (1, 1, -3)$
    Ahora tenemos una base $B = \{(1, 2, 1), (2, 1, 1), (1, 1, -3)\}$.

4.  **Expresar los vectores a transformar en la base B:**
    *   **𝜃(1,1, −3):** Ya sabemos que $(1, 1, -3)$ es el tercer vector de la base $B$.
        $(1, 1, -3) = 0(1, 2, 1) + 0(2, 1, 1) + 1(1, 1, -3)$
    *   **𝜃(2,0,1):** Necesitamos encontrar escalares $α, β, γ$ tales que:
        $(2, 0, 1) = α(1, 2, 1) + β(2, 1, 1) + γ(1, 1, -3)$
        Esto nos da el sistema:
        $\begin{cases} α + 2β + γ = 2 \\ 2α + β + γ = 0 \\ α + β - 3γ = 1 \end{cases}$
        Resolviendo el sistema, obtenemos: $α = -\frac{2}{3}, β = \frac{5}{3}, γ = 1$
        Entonces, $(2, 0, 1) = -\frac{2}{3}(1, 2, 1) + \frac{5}{3}(2, 1, 1) + 1(1, 1, -3)$
    *   **𝜃(1,2,3):** Necesitamos encontrar escalares $α, β, γ$ tales que:
        $(1, 2, 3) = α(1, 2, 1) + β(2, 1, 1) + γ(1, 1, -3)$
        Esto nos da el sistema:
        $\begin{cases} α + 2β + γ = 1 \\ 2α + β + γ = 2 \\ α + β - 3γ = 3 \end{cases}$
        Resolviendo el sistema, obtenemos: $α = 1, β = 1, γ = -2$
        Entonces, $(1, 2, 3) = 1(1, 2, 1) + 1(2, 1, 1) - 2(1, 1, -3)$

5.  **Aplicar la transformación 𝜃:**
    *   $θ(1, 1, -3) = θ(0(1, 2, 1) + 0(2, 1, 1) + 1(1, 1, -3)) = 0 \cdot θ(1, 2, 1) + 0 \cdot θ(2, 1, 1) + 1 \cdot θ(1, 1, -3)$
        Como $θ$ es una rotación, es ortogonal y preserva el producto cruz: $θ(1, 2, 1) \times θ(2, 1, 1) = θ((1, 2, 1) \times (2, 1, 1)) = θ(1, 1, -3)$.
        Calculamos $(2, 1, 1) \times (1, 1, 2) = (1, -3, 1)$. Entonces, $θ(1, 1, -3) = (1, -3, 1)$.
    *   $θ(2, 0, 1) = θ(-\frac{2}{3}(1, 2, 1) + \frac{5}{3}(2, 1, 1) + 1(1, 1, -3)) = -\frac{2}{3}θ(1, 2, 1) + \frac{5}{3}θ(2, 1, 1) + θ(1, 1, -3) = -\frac{2}{3}(2, 1, 1) + \frac{5}{3}(1, 1, 2) + (1, -3, 1) = (\frac{2}{3}, 0, \frac{11}{3})$
    *   $θ(1, 2, 3) = θ(1(1, 2, 1) + 1(2, 1, 1) - 2(1, 1, -3)) = 1 \cdot θ(1, 2, 1) + 1 \cdot θ(2, 1, 1) - 2 \cdot θ(1, 1, -3) = (2, 1, 1) + (1, 1, 2) - 2(1, -3, 1) = (1, 8, 1)$

**Ejercicio 12: Sea 𝜃 una rotación de ℝ³ tal que: 𝜃(2,1,0) = (1,0,2) y 𝜃(2,0,1) = (0,1,2) Calcular [𝜃]𝐵. Eligiendo 𝐵 una base conveniente.**

1.  **Elegir una base conveniente:**
    Dado que $𝜃$ es una rotación, una base ortonormal que incluya el eje de rotación simplificará la matriz. Sin embargo, no conocemos el eje de rotación. En su lugar, podemos usar los vectores dados y construir una base ortogonal.
    *   $v_1 = (2, 1, 0)$
    *   $v_2 = (2, 0, 1)$
    *   $v_3 = v_1 \times v_2 = (1, -2, -2)$

2.  **Ortogonalizar la base (Gram-Schmidt):**
    *   $w_1 = v_1 = (2, 1, 0)$
    *   $w_2 = v_2 - Proy_{⟨w_1⟩}(v_2) = (2, 0, 1) - \frac{(2, 0, 1) \cdot (2, 1, 0)}{||(2, 1, 0)||^2}(2, 1, 0) = (2, 0, 1) - \frac{4}{5}(2, 1, 0) = (\frac{2}{5}, -\frac{4}{5}, 1)$
    *   $w_3 = v_3 - Proy_{⟨w_1⟩}(v_3) - Proy_{⟨w_2⟩}(v_3) = (1, -2, -2) - \frac{(1, -2, -2) \cdot (2, 1, 0)}{||(2, 1, 0)||^2}(2, 1, 0) - \frac{(1, -2, -2) \cdot (\frac{2}{5}, -\frac{4}{5}, 1)}{||(\frac{2}{5}, -\frac{4}{5}, 1)||^2}(\frac{2}{5}, -\frac{4}{5}, 1) = (1, -2, -2) - 0 - 0 = (1, -2, -2)$
    *   La base ortogonal es $B_o = \{(2, 1, 0), (\frac{2}{5}, -\frac{4}{5}, 1), (1, -2, -2)\}$

3.  **Ortonormalizar la base:**
    *   $u_1 = \frac{(2, 1, 0)}{||(2, 1, 0)||} = (\frac{2}{\sqrt{5}}, \frac{1}{\sqrt{5}}, 0)$
    *   $u_2 = \frac{(\frac{2}{5}, -\frac{4}{5}, 1)}{||(\frac{2}{5}, -\frac{4}{5}, 1)||} = (\frac{2}{\sqrt{45}}, -\frac{4}{\sqrt{45}}, \frac{5}{\sqrt{45}})$
    *   $u_3 = \frac{(1, -2, -2)}{||(1, -2, -2)||} = (\frac{1}{3}, -\frac{2}{3}, -\frac{2}{3})$
    *   La base ortonormal es $B = \{(\frac{2}{\sqrt{5}}, \frac{1}{\sqrt{5}}, 0), (\frac{2}{\sqrt{45}}, -\frac{4}{\sqrt{45}}, \frac{5}{\sqrt{45}}), (\frac{1}{3}, -\frac{2}{3}, -\frac{2}{3})\}$

4.  **Calcular la matriz de la transformación en la base B:**
    *   $θ(2, 1, 0) = (1, 0, 2)$
    *   $θ(2, 0, 1) = (0, 1, 2)$
    *   $θ(1, -2, -2)$ es ortogonal a $(1,0,2)$ y $(0,1,2)$ y tiene norma 3, entonces $θ(1, -2, -2) = (2, 2, -1)$
    *   Expresamos los vectores transformados en la base B:
        *   $(1, 0, 2) = a(\frac{2}{\sqrt{5}}, \frac{1}{\sqrt{5}}, 0) + b(\frac{2}{\sqrt{45}}, -\frac{4}{\sqrt{45}}, \frac{5}{\sqrt{45}}) + c(\frac{1}{3}, -\frac{2}{3}, -\frac{2}{3})$
        *   $(0, 1, 2) = d(\frac{2}{\sqrt{5}}, \frac{1}{\sqrt{5}}, 0) + e(\frac{2}{\sqrt{45}}, -\frac{4}{\sqrt{45}}, \frac{5}{\sqrt{45}}) + f(\frac{1}{3}, -\frac{2}{3}, -\frac{2}{3})$
        *   $(2, 2, -1) = g(\frac{2}{\sqrt{5}}, \frac{1}{\sqrt{5}}, 0) + h(\frac{2}{\sqrt{45}}, -\frac{4}{\sqrt{45}}, \frac{5}{\sqrt{45}}) + i(\frac{1}{3}, -\frac{2}{3}, -\frac{2}{3})$

5.  **Matriz de la transformación:**
    $[θ]_B = \begin{pmatrix} a & d & g \\ b & e & h \\ c & f & i \end{pmatrix}$

**Ejercicio 13: Se define el determinante de una TL 𝑡 como el determinante de [𝑡]𝐵 para cualquier base 𝐵. Análogamente puede definirse la traza de 𝑡. Sea 𝐵 = {𝑣1, 𝑣2, 𝑣3} una base ortonormal de ℝ3.

a) Si {𝑣1, 𝑣2} es una base del plano de reflexión y {𝑣3} una base de la recta ortogonal al plano, hallar los autovalores, el determinante y la traza de la reflexión 𝑡, calculándolos en [𝑡]𝐵.
(Notar que el plano de reflexión es el complemento ortogonal de 𝑆𝜆=−1)**

1.  **Matriz de la reflexión en la base B:**
    *   En esta base, la reflexión transforma $v_1$ en $v_1$, $v_2$ en $v_2$ y $v_3$ en $-v_3$.
    *   Por lo tanto, la matriz de la reflexión en la base $B$ es:
        $[t]_B = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & -1 \end{pmatrix}$

2.  **Autovalores:**
    *   Los autovalores son las entradas diagonales de la matriz, que son 1, 1, y -1.

3.  **Determinante:**
    *   El determinante es el producto de los autovalores: $det(t) = (1)(1)(-1) = -1$.

4.  **Traza:**
    *   La traza es la suma de los autovalores: $tr(t) = 1 + 1 + (-1) = 1$.

**b) Si {𝑣1, 𝑣2} es una base del plano de proyección y {𝑣3} una base de la recta ortogonal al plano, hallar los autovalores, el determinante y la traza de la proyección 𝑝, calculándolos en [𝑝]𝐵.
(Notar que el plano de proyección es 𝑆𝜆=1)**

1.  **Matriz de la proyección en la base B:**
    *   En esta base, la proyección transforma $v_1$ en $v_1$, $v_2$ en $v_2$ y $v_3$ en $0$.
    *   Por lo tanto, la matriz de la proyección en la base $B$ es:
        $[p]_B = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0 \end{pmatrix}$

2.  **Autovalores:**
    *   Los autovalores son las entradas diagonales de la matriz, que son 1, 1, y 0.

3.  **Determinante:**
    *   El determinante es el producto de los autovalores: $det(p) = (1)(1)(0) = 0$.

4.  **Traza:**
    *   La traza es la suma de los autovalores: $tr(p) = 1 + 1 + 0 = 2$.

**c) Hallar [𝑝]𝐵si ahora 𝑝 es la proyección sobre la recta generada por 𝑣1. ¿qué cambia respecto al ejercicio anterior, cuando la dimensión del subespacio que se proyecta es otra?
(Por ejemplo, el plano ortogonal a la recta generada por 𝑣1 es 𝑆𝜆=0)**

1.  **Matriz de la proyección en la base B:**
    *   En esta base, la proyección transforma $v_1$ en $v_1$, y $v_2$ y $v_3$ en $0$.
    *   Por lo tanto, la matriz de la proyección en la base $B$ es:
        $[p]_B = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}$

2.  **Autovalores:**
    *   Los autovalores son las entradas diagonales de la matriz, que son 1, 0, y 0.

3.  **Determinante:**
    *   El determinante es el producto de los autovalores: $det(p) = (1)(0)(0) = 0$.

4.  **Traza:**
    *   La traza es la suma de los autovalores: $tr(p) = 1 + 0 + 0 = 1$.

**¿Qué cambia respecto al ejercicio anterior?**

*   La dimensión del subespacio sobre el que se proyecta afecta la matriz de proyección y, por lo tanto, sus autovalores y traza. En este caso, al proyectar sobre una recta (dimensión 1) en lugar de un plano (dimensión 2), la matriz tiene un solo 1 en la diagonal y el resto son ceros.

**d) Si {𝑣3} es una base del eje de rotación y Si {𝑣1, 𝑣2} es una base del plano de rotación, para una rotación 𝜏, mostrar que:
[𝜏]𝐵 = [
cos 𝜃 −𝑠𝑒𝑛𝜃 0
𝑠𝑒𝑛𝜃 𝑐𝑜𝑠𝜃 0
0 0 1
]
Hallar el determinante y la traza de la rotación 𝜏. ¿Cuántos autovalores reales tiene con seguridad 𝜏, y cuáles son?
Notar que el ángulo de rotación esta siempre en la traza de 𝜏. ¿Cómo se obtiene?
Notar además que el plano de rotación es el complemento ortogonal de 𝑆𝜆=1.**

1.  **Matriz de la rotación en la base B:**
    *   En esta base, la rotación deja fijo el eje $v_3$ y rota el plano generado por $v_1$ y $v_2$ un ángulo $θ$.
    *   Por lo tanto, la matriz de la rotación en la base $B$ es:
        $[τ]_B = \begin{pmatrix} cos θ & -sen θ & 0 \\ sen θ & cos θ & 0 \\ 0 & 0 & 1 \end{pmatrix}$

2.  **Determinante:**
    *   El determinante es el producto de los autovalores: $det(τ) = (cos^2 θ + sen^2 θ)(1) = 1$.

3.  **Traza:**
    *   La traza es la suma de los autovalores: $tr(τ) = cos θ + cos θ + 1 = 1 + 2cos θ$.

4.  **Autovalores reales:**
    *   La matriz tiene al menos un autovalor real, que es 1. Los otros dos autovalores son complejos conjugados (a menos que $θ = 0$ o $θ = π$).

5.  **Ángulo de rotación:**
    *   El ángulo de rotación se puede obtener de la traza: $tr(τ) = 1 + 2cos θ \implies cos θ = \frac{tr(τ) - 1}{2} \implies θ = arccos(\frac{tr(τ) - 1}{2})$.

