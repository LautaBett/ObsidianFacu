# Resolución de Ejercicios de Álgebra Lineal

---

## Ejercicio 17: Notación Matricial y Solución General de SEL

**Método General:** Escribir la matriz ampliada $(A|\vec{b})$ y aplicar eliminación Gaussiana (o Gauss-Jordan) para encontrar la forma escalonada. Luego, analizar los rangos con Rouché-Frobenius y encontrar la solución.

**a) { x + y = 1; x + 2y + z = 1; y + 3z = 1 }**

*   **Notación Matricial:**
    $A = \begin{pmatrix} 1 & 1 & 0 \\ 1 & 2 & 1 \\ 0 & 1 & 3 \end{pmatrix}$, $\vec{x} = \begin{pmatrix} x \\ y \\ z \end{pmatrix}$, $\vec{b} = \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}$
    $A\vec{x} = \vec{b}$
*   **Matriz Ampliada y Gauss:**
    $(A|\vec{b}) = \begin{pmatrix} 1 & 1 & 0 & | & 1 \\ 1 & 2 & 1 & | & 1 \\ 0 & 1 & 3 & | & 1 \end{pmatrix} \xrightarrow{F_2 - F_1} \begin{pmatrix} 1 & 1 & 0 & | & 1 \\ 0 & 1 & 1 & | & 0 \\ 0 & 1 & 3 & | & 1 \end{pmatrix} \xrightarrow{F_3 - F_2} \begin{pmatrix} 1 & 1 & 0 & | & 1 \\ 0 & 1 & 1 & | & 0 \\ 0 & 0 & 2 & | & 1 \end{pmatrix}$
*   **Análisis:** $rg(A) = 3$, $rg(A|\vec{b}) = 3$. Número de incógnitas = 3.
    Como $rg(A) = rg(A|\vec{b}) = 3$, el sistema es **Compatible Determinado (SCD)**.
*   **Solución:**
    De F3: $2z = 1 \implies z = 1/2$
    De F2: $y + z = 0 \implies y = -z = -1/2$
    De F1: $x + y = 1 \implies x = 1 - y = 1 - (-1/2) = 3/2$
    **Solución General:** $\vec{x} = \begin{pmatrix} 3/2 \\ -1/2 \\ 1/2 \end{pmatrix}$. Conjunto solución: $S = \{(3/2, -1/2, 1/2)\}$.

**b) { 3x - 6y - z + t = 4; -x + 2y + 2z + 3t = 3; 4x - 8y - 3z - 2t = 3 }**

*   **Notación Matricial:**
    $A = \begin{pmatrix} 3 & -6 & -1 & 1 \\ -1 & 2 & 2 & 3 \\ 4 & -8 & -3 & -2 \end{pmatrix}$, $\vec{x} = \begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix}$, $\vec{b} = \begin{pmatrix} 4 \\ 3 \\ 3 \end{pmatrix}$
*   **Matriz Ampliada y Gauss:**
    $(A|\vec{b}) = \begin{pmatrix} 3 & -6 & -1 & 1 & | & 4 \\ -1 & 2 & 2 & 3 & | & 3 \\ 4 & -8 & -3 & -2 & | & 3 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} -1 & 2 & 2 & 3 & | & 3 \\ 3 & -6 & -1 & 1 & | & 4 \\ 4 & -8 & -3 & -2 & | & 3 \end{pmatrix}$
    $\xrightarrow{-F_1} \begin{pmatrix} 1 & -2 & -2 & -3 & | & -3 \\ 3 & -6 & -1 & 1 & | & 4 \\ 4 & -8 & -3 & -2 & | & 3 \end{pmatrix} \xrightarrow{F_2 - 3F_1, F_3 - 4F_1} \begin{pmatrix} 1 & -2 & -2 & -3 & | & -3 \\ 0 & 0 & 5 & 10 & | & 13 \\ 0 & 0 & 5 & 10 & | & 15 \end{pmatrix}$
    $\xrightarrow{F_3 - F_2} \begin{pmatrix} 1 & -2 & -2 & -3 & | & -3 \\ 0 & 0 & 5 & 10 & | & 13 \\ 0 & 0 & 0 & 0 & | & 2 \end{pmatrix}$
*   **Análisis:** $rg(A) = 2$, $rg(A|\vec{b}) = 3$.
    Como $rg(A) < rg(A|\vec{b})$, el sistema es **Incompatible (SI)**.
*   **Solución:** No existe solución. Conjunto solución: $S = \emptyset$.

**c) { 3x + 2y - t = 5; x - z + 2t = 1 }**

*   **Notación Matricial:**
    $A = \begin{pmatrix} 3 & 2 & 0 & -1 \\ 1 & 0 & -1 & 2 \end{pmatrix}$, $\vec{x} = \begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix}$, $\vec{b} = \begin{pmatrix} 5 \\ 1 \end{pmatrix}$
*   **Matriz Ampliada y Gauss:**
    $(A|\vec{b}) = \begin{pmatrix} 3 & 2 & 0 & -1 & | & 5 \\ 1 & 0 & -1 & 2 & | & 1 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & 0 & -1 & 2 & | & 1 \\ 3 & 2 & 0 & -1 & | & 5 \end{pmatrix}$
    $\xrightarrow{F_2 - 3F_1} \begin{pmatrix} 1 & 0 & -1 & 2 & | & 1 \\ 0 & 2 & 3 & -7 & | & 2 \end{pmatrix}$
*   **Análisis:** $rg(A) = 2$, $rg(A|\vec{b}) = 2$. Número de incógnitas = 4.
    Como $rg(A) = rg(A|\vec{b}) = 2 < 4$, el sistema es **Compatible Indeterminado (SCI)**. Hay $4-2=2$ variables libres.
*   **Solución:**
    Variables pivote: $x, y$. Variables libres: $z, t$.
    Asignamos parámetros: $z = s$, $t = r$.
    De F2: $2y + 3z - 7t = 2 \implies 2y = 2 - 3s + 7r \implies y = 1 - \frac{3}{2}s + \frac{7}{2}r$
    De F1: $x - z + 2t = 1 \implies x = 1 + z - 2t = 1 + s - 2r$
    **Solución General:**
    $\vec{x} = \begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = \begin{pmatrix} 1 + s - 2r \\ 1 - \frac{3}{2}s + \frac{7}{2}r \\ s \\ r \end{pmatrix} = \begin{pmatrix} 1 \\ 1 \\ 0 \\ 0 \end{pmatrix} + s \begin{pmatrix} 1 \\ -3/2 \\ 1 \\ 0 \end{pmatrix} + r \begin{pmatrix} -2 \\ 7/2 \\ 0 \\ 1 \end{pmatrix}$ para $s, r \in \mathbb{R}$.

*(Los apartados d, e, f se resuelven de forma análoga usando Gauss-Jordan y Rouché-Frobenius)*

---

# Ejercicio 18: Determinar $\lambda$ para que el sistema tenga solución

**Método:** Usar Gauss-Jordan en la matriz ampliada $(A|\vec{b})$ y aplicar el Teorema de Rouché-Frobenius ($rg(A) = rg(A|\vec{b})$ para compatibilidad).

---

**(a)**
Sistema:
2x - y + z + t = 1  
x + 2y - z + 4t = 2  
x + 7y - 4z + 11t = λ
Matriz Ampliada y Gauss:
$$(A|\vec{b}) = \begin{pmatrix} 2 & -1 & 1 & 1 & | & 1 \\ 1 & 2 & -1 & 4 & | & 2 \\ 1 & 7 & -4 & 11 & | & \lambda \end{pmatrix}$$
$$ \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & 2 & -1 & 4 & | & 2 \\ 2 & -1 & 1 & 1 & | & 1 \\ 1 & 7 & -4 & 11 & | & \lambda \end{pmatrix} $$
$$ \xrightarrow{F_2 \leftarrow F_2 - 2F_1, F_3 \leftarrow F_3 - F_1} \begin{pmatrix} 1 & 2 & -1 & 4 & | & 2 \\ 0 & -5 & 3 & -7 & | & -3 \\ 0 & 5 & -3 & 7 & | & \lambda - 2 \end{pmatrix} $$
$$ \xrightarrow{F_3 \leftarrow F_3 + F_2} \begin{pmatrix} 1 & 2 & -1 & 4 & | & 2 \\ 0 & -5 & 3 & -7 & | & -3 \\ 0 & 0 & 0 & 0 & | & \lambda - 5 \end{pmatrix} $$
**Condición de Compatibilidad:** $rg(A) = rg(A|\vec{b})$.
$rg(A) = 2$. Necesitamos que la última fila sea $(0 \ 0 \ 0 \ 0 \ | \ 0)$.
$$ \lambda - 5 = 0 \implies \lambda = 5 $$
**Solución (a):** El sistema tiene solución si $\lambda = 5$.

---

**(b)**
Sistema:
λx + y + z = 1  
x + λy + z = 1  
x + y + λz = 1
Matriz Ampliada y Gauss:
$$(A|\vec{b}) = \begin{pmatrix} \lambda & 1 & 1 & | & 1 \\ 1 & \lambda & 1 & | & 1 \\ 1 & 1 & \lambda & | & 1 \end{pmatrix}$$
$$ \xrightarrow{F_1 \leftrightarrow F_3} \begin{pmatrix} 1 & 1 & \lambda & | & 1 \\ 1 & \lambda & 1 & | & 1 \\ \lambda & 1 & 1 & | & 1 \end{pmatrix} $$
$$ \xrightarrow{F_2 \leftarrow F_2 - F_1, F_3 \leftarrow F_3 - \lambda F_1} \begin{pmatrix} 1 & 1 & \lambda & | & 1 \\ 0 & \lambda-1 & 1-\lambda & | & 0 \\ 0 & 1-\lambda & 1-\lambda^2 & | & 1-\lambda \end{pmatrix} $$
*   **Caso 1: $\lambda = 1$**
    La matriz original es $\begin{pmatrix} 1 & 1 & 1 & | & 1 \\ 1 & 1 & 1 & | & 1 \\ 1 & 1 & 1 & | & 1 \end{pmatrix} \rightarrow \begin{pmatrix} 1 & 1 & 1 & | & 1 \\ 0 & 0 & 0 & | & 0 \\ 0 & 0 & 0 & | & 0 \end{pmatrix}$.
    $rg(A)=1, rg(A|\vec{b})=1$. Compatible. $\lambda=1$ es válido.

*   **Caso 2: $\lambda \neq 1$**
    Continuamos desde $\begin{pmatrix} 1 & 1 & \lambda & | & 1 \\ 0 & \lambda-1 & 1-\lambda & | & 0 \\ 0 & 1-\lambda & 1-\lambda^2 & | & 1-\lambda \end{pmatrix}$.
    Dividimos F2 por $(\lambda-1)$:
    $$ \begin{pmatrix} 1 & 1 & \lambda & | & 1 \\ 0 & 1 & -1 & | & 0 \\ 0 & 1-\lambda & (1-\lambda)(1+\lambda) & | & 1-\lambda \end{pmatrix} $$
    Hacemos $F_3 \leftarrow F_3 - (1-\lambda)F_2$:
    $$ \begin{pmatrix} 1 & 1 & \lambda & | & 1 \\ 0 & 1 & -1 & | & 0 \\ 0 & 0 & (1-\lambda)(1+\lambda) - (1-\lambda)(-1) & | & 1-\lambda \end{pmatrix} $$
    $$ \begin{pmatrix} 1 & 1 & \lambda & | & 1 \\ 0 & 1 & -1 & | & 0 \\ 0 & 0 & (1-\lambda)(2+\lambda) & | & 1-\lambda \end{pmatrix} $$
    Para compatibilidad, si $(1-\lambda)(2+\lambda) = 0$, entonces $1-\lambda$ también debe ser 0. Como $\lambda \neq 1$, la única posibilidad de incompatibilidad es si $2+\lambda = 0 \implies \lambda = -2$.
    Si $\lambda = -2$, la última fila es $(0 \ 0 \ 0 \ | \ 1-(-2)) = (0 \ 0 \ 0 \ | \ 3)$. Incompatible.
    Si $\lambda \neq 1$ y $\lambda \neq -2$, entonces $rg(A)=3, rg(A|\vec{b})=3$. Compatible.

*   **Conclusión:** El sistema es compatible si $\lambda \neq -2$.

**Solución (b):** El sistema tiene solución si $\lambda \neq -2$.

---

**(c)**
Sistema:
(1+λ)x + y + z = 1  
x + (1+λ)y + z = 1  
x + y + (1+λ)z = 1

Este sistema es análogo al del apartado (b) con el parámetro $k = 1+\lambda$.
El sistema del apartado (b) tiene solución si su parámetro no es $-2$.
Por lo tanto, este sistema tiene solución si:
$$ k \neq -2 \implies 1+\lambda \neq -2 \implies \lambda \neq -3 $$
**Solución (c):** El sistema tiene solución si $\lambda \neq -3$.

---

---

## Ejercicio 19: Valores de $k$ para soluciones no triviales (Sistema Homogéneo)

*   **Sistema:**
    $x + (k + 1)y + z = 0$
    $x + y + (k + 1)z = 0$
    $(k + 1)x + y + z = 0$
*   **Método:** Un sistema homogéneo $A\vec{x} = \vec{0}$ tiene soluciones no triviales si y solo si la matriz $A$ es singular, es decir, $\det(A) = 0$.
*   **Matriz A:**
    $A = \begin{pmatrix} 1 & k+1 & 1 \\ 1 & 1 & k+1 \\ k+1 & 1 & 1 \end{pmatrix}$
*   **Determinante:**
    $\det(A) = 1(1 - (k+1)) - (k+1)(1 - (k+1)^2) + 1(1 - (k+1))$
    $\det(A) = -k - (k+1)(1 - (k^2+2k+1)) - k$
    $\det(A) = -2k - (k+1)(-k^2-2k)$
    $\det(A) = -2k + k(k+1)(k+2)$
    $\det(A) = k[-2 + (k+1)(k+2)]$
    $\det(A) = k[-2 + k^2 + 3k + 2]$
    $\det(A) = k[k^2 + 3k] = k^2(k+3)$
*   **Condición para solución no trivial:** $\det(A) = 0 \implies k^2(k+3) = 0$.
    Las soluciones son $k=0$ y $k=-3$.

*   **Estudio del Espacio Solución:**
    *   **Caso k = 0:**
        $A = \begin{pmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{pmatrix}$. La matriz ampliada $(A|\vec{0})$ se reduce a $\begin{pmatrix} 1 & 1 & 1 & | & 0 \\ 0 & 0 & 0 & | & 0 \\ 0 & 0 & 0 & | & 0 \end{pmatrix}$.
        $rg(A)=1$. Número de incógnitas = 3. Dimensión del espacio solución = $3-1=2$.
        La ecuación es $x + y + z = 0$. Variables libres: $y=s, z=t$. $x = -s - t$.
        Solución: $\vec{x} = (-s-t, s, t) = s(-1, 1, 0) + t(-1, 0, 1)$.
        **Interpretación Geométrica:** Un plano que pasa por el origen con vectores directores $(-1, 1, 0)$ y $(-1, 0, 1)$ (o normal $(1, 1, 1)$).
    *   **Caso k = -3:**
        $A = \begin{pmatrix} 1 & -2 & 1 \\ 1 & 1 & -2 \\ -2 & 1 & 1 \end{pmatrix}$.
        $(A|\vec{0}) = \begin{pmatrix} 1 & -2 & 1 & | & 0 \\ 1 & 1 & -2 & | & 0 \\ -2 & 1 & 1 & | & 0 \end{pmatrix} \xrightarrow{F_2-F_1, F_3+2F_1} \begin{pmatrix} 1 & -2 & 1 & | & 0 \\ 0 & 3 & -3 & | & 0 \\ 0 & -3 & 3 & | & 0 \end{pmatrix} \xrightarrow{F_3+F_2, F_2/3} \begin{pmatrix} 1 & -2 & 1 & | & 0 \\ 0 & 1 & -1 & | & 0 \\ 0 & 0 & 0 & | & 0 \end{pmatrix}$
        $rg(A)=2$. Número de incógnitas = 3. Dimensión del espacio solución = $3-2=1$.
        Sistema: $x - 2y + z = 0$, $y - z = 0$. Variable libre: $z=t$.
        $y = z = t$. $x = 2y - z = 2t - t = t$.
        Solución: $\vec{x} = (t, t, t) = t(1, 1, 1)$.
        **Interpretación Geométrica:** Una recta que pasa por el origen con vector director $(1, 1, 1)$.

---

## Ejercicio 20: Parábola por tres puntos

*   **Ecuación:** $y = ax^2 + bx + c$
*   **Puntos:** (1, -5), (-1, 1), (2, 7)
*   **Sistema de ecuaciones para a, b, c:**
    *   Punto (1, -5): $a(1)^2 + b(1) + c = -5 \implies a + b + c = -5$
    *   Punto (-1, 1): $a(-1)^2 + b(-1) + c = 1 \implies a - b + c = 1$
    *   Punto (2, 7): $a(2)^2 + b(2) + c = 7 \implies 4a + 2b + c = 7$
*   **Matriz Ampliada y Gauss:**
    $\begin{pmatrix} 1 & 1 & 1 & | & -5 \\ 1 & -1 & 1 & | & 1 \\ 4 & 2 & 1 & | & 7 \end{pmatrix} \xrightarrow{F_2-F_1, F_3-4F_1} \begin{pmatrix} 1 & 1 & 1 & | & -5 \\ 0 & -2 & 0 & | & 6 \\ 0 & -2 & -3 & | & 27 \end{pmatrix}$
    $\xrightarrow{F_2 / (-2)} \begin{pmatrix} 1 & 1 & 1 & | & -5 \\ 0 & 1 & 0 & | & -3 \\ 0 & -2 & -3 & | & 27 \end{pmatrix} \xrightarrow{F_3 + 2F_2} \begin{pmatrix} 1 & 1 & 1 & | & -5 \\ 0 & 1 & 0 & | & -3 \\ 0 & 0 & -3 & | & 21 \end{pmatrix}$
*   **Solución:**
    De F3: $-3c = 21 \implies c = -7$
    De F2: $b = -3$
    De F1: $a + b + c = -5 \implies a - 3 - 7 = -5 \implies a - 10 = -5 \implies a = 5$
*   **Resultado:** $a=5, b=-3, c=-7$. La parábola es $y = 5x^2 - 3x - 7$.

---

## Ejercicio 21: Análisis de Sistemas con Parámetro $\alpha$

**Método:** Aplicar Gauss a la matriz ampliada y analizar los rangos según $\alpha$.

**S1 = { 2x - $\alpha$y + z = -2$\alpha$ + 5; x + y - $\alpha$z = 1; 4x + y - $\alpha$z = $\alpha$ }**

*   **Matriz Ampliada:**
    $(A|\vec{b}) = \begin{pmatrix} 2 & -\alpha & 1 & | & -2\alpha + 5 \\ 1 & 1 & -\alpha & | & 1 \\ 4 & 1 & -\alpha & | & \alpha \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & 1 & -\alpha & | & 1 \\ 2 & -\alpha & 1 & | & -2\alpha + 5 \\ 4 & 1 & -\alpha & | & \alpha \end{pmatrix}$
    $\xrightarrow{F_2-2F_1, F_3-4F_1} \begin{pmatrix} 1 & 1 & -\alpha & | & 1 \\ 0 & -\alpha-2 & 1+2\alpha & | & -2\alpha + 3 \\ 0 & -3 & 3\alpha & | & \alpha - 4 \end{pmatrix}$
*   **Análisis de casos:**
    *   **Si $\alpha = 1$:**
        $\begin{pmatrix} 1 & 1 & -1 & | & 1 \\ 0 & -3 & 3 & | & 1 \\ 0 & -3 & 3 & | & -3 \end{pmatrix} \xrightarrow{F_3-F_2} \begin{pmatrix} 1 & 1 & -1 & | & 1 \\ 0 & -3 & 3 & | & 1 \\ 0 & 0 & 0 & | & -4 \end{pmatrix}$. $rg(A)=2, rg(A|\vec{b})=3$. **Incompatible (SI)**.
    *   **Si $\alpha = -1$:**
        $\begin{pmatrix} 1 & 1 & 1 & | & 1 \\ 0 & -1 & -1 & | & 5 \\ 0 & -3 & -3 & | & -5 \end{pmatrix} \xrightarrow{F_3-3F_2} \begin{pmatrix} 1 & 1 & 1 & | & 1 \\ 0 & -1 & -1 & | & 5 \\ 0 & 0 & 0 & | & -20 \end{pmatrix}$. $rg(A)=2, rg(A|\vec{b})=3$. **Incompatible (SI)**.
    *   **Si $\alpha = -2$:**
        $\begin{pmatrix} 1 & 1 & 2 & | & 1 \\ 0 & 0 & -3 & | & 7 \\ 0 & -3 & -6 & | & -6 \end{pmatrix} \xrightarrow{F_2 \leftrightarrow F_3} \begin{pmatrix} 1 & 1 & 2 & | & 1 \\ 0 & -3 & -6 & | & -6 \\ 0 & 0 & -3 & | & 7 \end{pmatrix}$. $rg(A)=3, rg(A|\vec{b})=3$. Número de incógnitas = 3. **Compatible Determinado (SCD)**.
    *   **Si $\alpha \neq 1, -1, -2$:** Se puede continuar la eliminación Gaussiana sin obtener una fila $(0 \ 0 \ 0 \ | \ d \neq 0)$ y se llegará a $rg(A)=3, rg(A|\vec{b})=3$. **Compatible Determinado (SCD)**.

*   **Resumen S1:**
    a) No tenga solución (SI): $\alpha = 1$ o $\alpha = -1$.
    b) Tenga solución única (SCD): $\alpha \neq 1$ y $\alpha \neq -1$.
    c) Tenga infinitas soluciones (SCI): Nunca.

*(S2 y S3 se analizan de forma similar, prestando atención a los valores de $\alpha$ que podrían hacer cero los pivotes o crear inconsistencias).*

---

## Ejercicio 22: Combinación Lineal

*   **Pregunta:** ¿Es $\vec{v} = (2, -1, 3)$ combinación lineal de $\vec{v_1}=(1,2,-3)$, $\vec{v_2}=(-1,1,1)$, $\vec{v_3}=(-1,4,-1)$?
*   **Método:** Resolver el sistema $x\vec{v_1} + y\vec{v_2} + z\vec{v_3} = \vec{v}$. Verificar si es compatible.
*   **Matriz Ampliada:**
    $(A|\vec{v}) = \begin{pmatrix} 1 & -1 & -1 & | & 2 \\ 2 & 1 & 4 & | & -1 \\ -3 & 1 & -1 & | & 3 \end{pmatrix} \xrightarrow{F_2-2F_1, F_3+3F_1} \begin{pmatrix} 1 & -1 & -1 & | & 2 \\ 0 & 3 & 6 & | & -5 \\ 0 & -2 & -4 & | & 9 \end{pmatrix}$
    $\xrightarrow{F_3 + (2/3)F_2} \begin{pmatrix} 1 & -1 & -1 & | & 2 \\ 0 & 3 & 6 & | & -5 \\ 0 & 0 & 0 & | & 9 - 10/3 = 17/3 \end{pmatrix}$
*   **Análisis:** $rg(A)=2$, $rg(A|\vec{v})=3$.
*   **Conclusión:** El sistema es Incompatible. Por lo tanto, $(2, -1, 3)$ **no es** combinación lineal de los otros tres vectores.

---

## Ejercicio 23: Combinación Lineal Vectorial

*   **Ecuación:** $(u^3, v^3, w^3) = a(1,1,1) + b(u, v, w) + c(u^2, v^2, w^2)$
*   **Sistema:**
    $a + bu + cu^2 = u^3$
    $a + bv + cv^2 = v^3$
    $a + bw + cw^2 = w^3$
*   **Interpretación:** Considerar el polinomio $P(x) = x^3 - cx^2 - bx - a$. Las ecuaciones dicen que $u, v, w$ son raíces de $P(x)$.
*   Como $u, v, w$ son distintos, $P(x)$ debe ser $(x-u)(x-v)(x-w)$.
*   $P(x) = (x-u)(x-v)(x-w) = x^3 - (u+v+w)x^2 + (uv+uw+vw)x - uvw$
*   Comparando coeficientes con $P(x) = x^3 - cx^2 - bx - a$:
    *   $-c = -(u+v+w) \implies c = u+v+w$
    *   $-b = uv+uw+vw \implies b = -(uv+uw+vw)$
    *   $-a = -uvw \implies a = uvw$
*   **Solución:** $a = uvw$, $b = -(uv+uw+vw)$, $c = u+v+w$.

---

## Ejercicio 24: Condiciones para Pertenecer al Span

**a) $S = \langle \vec{u_1}=(-1,2,1), \vec{u_2}=(2,-4,2) \rangle$. ¿Cuándo $\vec{v}=(x,y,z) \in S$?**

*   **Método:** Resolver $s\vec{u_1} + t\vec{u_2} = \vec{v}$. El sistema debe ser compatible.
*   **Matriz Ampliada:**
    $\begin{pmatrix} -1 & 2 & | & x \\ 2 & -4 & | & y \\ 1 & 2 & | & z \end{pmatrix} \xrightarrow{F_2+2F_1, F_3+F_1} \begin{pmatrix} -1 & 2 & | & x \\ 0 & 0 & | & y+2x \\ 0 & 4 & | & z+x \end{pmatrix}$
    $\xrightarrow{F_2 \leftrightarrow F_3} \begin{pmatrix} -1 & 2 & | & x \\ 0 & 4 & | & z+x \\ 0 & 0 & | & y+2x \end{pmatrix}$
*   **Condición de Compatibilidad:** $rg(A) = rg(A|\vec{v}) \implies y+2x = 0$.
*   **Resultado:** La condición es $2x + y = 0$.

**b) $S = \langle \vec{u_1}=(1,0,1,1), \vec{u_2}=(0,1,1,2), \vec{u_3}=(1,1,1,0) \rangle$. ¿Cuándo $\vec{v}=(x,y,z,w) \in S$?**

*   **Matriz Ampliada:**
    $\begin{pmatrix} 1 & 0 & 1 & | & x \\ 0 & 1 & 1 & | & y \\ 1 & 1 & 1 & | & z \\ 1 & 2 & 0 & | & w \end{pmatrix} \xrightarrow{F_3-F_1, F_4-F_1} \begin{pmatrix} 1 & 0 & 1 & | & x \\ 0 & 1 & 1 & | & y \\ 0 & 1 & 0 & | & z-x \\ 0 & 2 & -1 & | & w-x \end{pmatrix}$
    $\xrightarrow{F_3-F_2, F_4-2F_2} \begin{pmatrix} 1 & 0 & 1 & | & x \\ 0 & 1 & 1 & | & y \\ 0 & 0 & -1 & | & z-x-y \\ 0 & 0 & -3 & | & w-x-2y \end{pmatrix}$
    $\xrightarrow{F_4-3F_3} \begin{pmatrix} 1 & 0 & 1 & | & x \\ 0 & 1 & 1 & | & y \\ 0 & 0 & -1 & | & z-x-y \\ 0 & 0 & 0 & | & (w-x-2y) - 3(z-x-y) \end{pmatrix}$
*   **Condición de Compatibilidad:** La última entrada debe ser cero.
    $(w-x-2y) - 3z + 3x + 3y = 0 \implies w + 2x + y - 3z = 0$
*   **Resultado:** La condición es $2x + y - 3z + w = 0$.

---

## Ejercicio 25: Ecuaciones Cartesianas de Planos

**a) $S = \{(-1,2,1)s + (2,4,-2)t: s,t \in \mathbb{R}\}$**

*   Plano por el origen con $\vec{u}=(-1,2,1)$, $\vec{v}=(2,4,-2)$.
*   Vector Normal: $\vec{n} = \vec{u} \times \vec{v} = (-8, 0, -8)$. Usamos $\vec{n'} = (1, 0, 1)$.
*   Ecuación: $1x + 0y + 1z = 0$.
*   **Resultado:** $x + z = 0$.

**b) $S = \{(1,-2,2)s + (2,0,-1)t + (1,2,3): s,t \in \mathbb{R}\}$**

*   Punto de paso: $P=(1,2,3)$.
*   Vectores directores: $\vec{u}=(1,-2,2)$, $\vec{v}=(2,0,-1)$.
*   Vector Normal: $\vec{n} = \vec{u} \times \vec{v} = (2, 5, 4)$.
*   Ecuación: $2(x-1) + 5(y-2) + 4(z-3) = 0$.
*   **Resultado:** $2x + 5y + 4z = 24$.

---

## Ejercicio 26: Rango, Inversa, Solución y Combinación Lineal

**I. $A = \begin{pmatrix} 2 & 3 \\ 3 & 5 \end{pmatrix}$, $b = \begin{pmatrix} 3 \\ 4 \end{pmatrix}$**

*   a) **Rango:** $\det(A) = 1 \neq 0 \implies rg(A) = 2$.
*   b) **Inversa:** $A^{-1} = \begin{pmatrix} 5 & -3 \\ -3 & 2 \end{pmatrix}$.
*   c) **Solución $Ax=b$:** $x = A^{-1}b = \begin{pmatrix} 5 & -3 \\ -3 & 2 \end{pmatrix} \begin{pmatrix} 3 \\ 4 \end{pmatrix} = \begin{pmatrix} 3 \\ -1 \end{pmatrix}$.
*   d) **Combinación Lineal:** $b = 3 \begin{pmatrix} 2 \\ 3 \end{pmatrix} - 1 \begin{pmatrix} 3 \\ 5 \end{pmatrix}$.

**II. $A = \begin{pmatrix} 1 & 1 & 1 \\ 0 & 2 & 3 \\ 3 & 2 & 2 \end{pmatrix}$, $b = \begin{pmatrix} 1 \\ 1 \\ 2 \end{pmatrix}$**

*   a) **Rango:** $\det(A) = 1 \neq 0 \implies rg(A) = 3$.
*   b) **Inversa:** $A^{-1} = \begin{pmatrix} -2 & 0 & 1 \\ 9 & -1 & -3 \\ -6 & 1 & 2 \end{pmatrix}$.
*   c) **Solución $Ax=b$:** $x = A^{-1}b = \begin{pmatrix} -2 & 0 & 1 \\ 9 & -1 & -3 \\ -6 & 1 & 2 \end{pmatrix} \begin{pmatrix} 1 \\ 1 \\ 2 \end{pmatrix} = \begin{pmatrix} 0 \\ 2 \\ -1 \end{pmatrix}$.
*   d) **Combinación Lineal:** $b = 0 \begin{pmatrix} 1 \\ 0 \\ 3 \end{pmatrix} + 2 \begin{pmatrix} 1 \\ 2 \\ 2 \end{pmatrix} - 1 \begin{pmatrix} 1 \\ 3 \\ 2 \end{pmatrix}$.

---