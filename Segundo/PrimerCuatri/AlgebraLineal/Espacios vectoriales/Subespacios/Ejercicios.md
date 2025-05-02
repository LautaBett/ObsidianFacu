¡Excelente! Usemos la información de las notas [[Subespacios]], [[Espacios Vectoriales]], [[Complemento ortogonal y etc]], y [[Suma directa, subespacios fundamentales]] para abordar estos ejercicios.

**Recordatorio Clave (Definición de Subespacio):** Un subconjunto $S$ de un espacio vectorial $V$ es un subespacio si cumple:
1.  $\vec{0} \in S$ (Contiene el vector nulo).
2.  Si $\mathbf{u}, \mathbf{v} \in S$, entonces $\mathbf{u} + \mathbf{v} \in S$ (Cerrado bajo la suma).
3.  Si $\mathbf{u} \in S$ y $\lambda$ es un escalar, entonces $\lambda \mathbf{u} \in S$ (Cerrado bajo producto por escalar).

---

### Ejercicio 12: Decidir si S es un subespacio de V

**a) $S = \{p \in K[X]: gr(p) \text{ es par}\}; V = K[X]$**
*   1. $\vec{0}$ (polinomio cero) no tiene grado definido o se considera de grado $-\infty$. No cumple estrictamente "grado par". Si consideramos que $0$ debe estar, falla. Si no, tomemos $p(x)=x^2 \in S$, $q(x)=-x^2+x \in S$. $p(x)+q(x)=x$, cuyo grado es 1 (impar). No es cerrado bajo suma.
*   **No es subespacio.**

**b) $S = \{(x, y) \in \mathbb{R}^2 : x^2 = y^2\}; V = \mathbb{R}^2$**
*   1. $(0,0) \in S$ porque $0^2=0^2$.
*   2. Sea $\mathbf{u}=(1,1) \in S$ y $\mathbf{v}=(1,-1) \in S$. $\mathbf{u}+\mathbf{v} = (2,0)$. $2^2 = 4 \neq 0^2 = 0$. No es cerrado bajo suma.
*   **No es subespacio.**

**c) $S = \left\{ \begin{pmatrix} a & b \\ b & c \end{pmatrix} : b = a + c \right\}; V = K^{2\times2}$** (Asumo matrices simétricas por la notación, aunque no es estrictamente necesario para el análisis de la condición $b=a+c$).
*   1. La matriz nula $\begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}$ tiene $a=0, b=0, c=0$. Cumple $0=0+0$. Sí está.
*   2. Sean $M_1 = \begin{pmatrix} a_1 & b_1 \\ b_1 & c_1 \end{pmatrix}$ y $M_2 = \begin{pmatrix} a_2 & b_2 \\ b_2 & c_2 \end{pmatrix}$ en $S$. Entonces $b_1=a_1+c_1$ y $b_2=a_2+c_2$.
    $M_1+M_2 = \begin{pmatrix} a_1+a_2 & b_1+b_2 \\ b_1+b_2 & c_1+c_2 \end{pmatrix}$. ¿Cumple la condición? Necesitamos verificar si $(b_1+b_2) = (a_1+a_2) + (c_1+c_2)$. Usando las hipótesis: $(a_1+c_1) + (a_2+c_2) = (a_1+a_2) + (c_1+c_2)$. Sí cumple. Es cerrado bajo suma.
*   3. Sea $M = \begin{pmatrix} a & b \\ b & c \end{pmatrix} \in S$ ($b=a+c$) y $\lambda$ un escalar.
    $\lambda M = \begin{pmatrix} \lambda a & \lambda b \\ \lambda b & \lambda c \end{pmatrix}$. ¿Cumple la condición? Necesitamos verificar si $(\lambda b) = (\lambda a) + (\lambda c)$. Esto es $\lambda(b) = \lambda(a+c)$, lo cual es cierto por la hipótesis $b=a+c$. Es cerrado bajo producto por escalar.
*   **Sí es subespacio.**

**d) $S = \{A \in K^{n\times n} : a_{11} + a_{22} + \dots + a_{nn} = 0\}; V = K^{n\times n}$** (Matrices de traza cero)
*   1. La matriz nula tiene todos los elementos $a_{ii}=0$, su suma es 0. Sí está.
*   2. Sean $A, B \in S$. $tr(A)=0, tr(B)=0$. $tr(A+B) = tr(A)+tr(B) = 0+0=0$. Sí es cerrado bajo suma.
*   3. Sea $A \in S$. $tr(A)=0$. $tr(\lambda A) = \lambda tr(A) = \lambda \cdot 0 = 0$. Sí es cerrado bajo producto por escalar.
*   **Sí es subespacio.**

**e) $S = \{(a, b, 1): a, b \in K\}; V = K^3$**
*   1. El vector nulo $(0,0,0)$ no tiene 1 en la tercera componente. No está en $S$.
*   **No es subespacio.**

**f) $S = \{(a, b, 0): a, b \in K\}; V = K^3$**
*   1. $(0,0,0) \in S$ (tomando $a=0, b=0$).
*   2. $(a_1, b_1, 0) + (a_2, b_2, 0) = (a_1+a_2, b_1+b_2, 0)$. La tercera componente es 0, así que está en $S$. Sí es cerrado bajo suma.
*   3. $\lambda(a, b, 0) = (\lambda a, \lambda b, 0)$. La tercera componente es 0, así que está en $S$. Sí es cerrado bajo producto por escalar.
*   **Sí es subespacio.** (Es el plano XY en $K^3$).

**g) $S = \{(x, y, z) \in \mathbb{R}^3 : x = -2y; z = 3y\}; V = \mathbb{R}^3$**
*   Este es el conjunto de soluciones de un sistema homogéneo:
    $x + 2y = 0$
    $z - 3y = 0$
*   Como vimos en [[Suma directa, subespacios fundamentales]], el conjunto de soluciones de un sistema homogéneo ($N(A)$) siempre es un subespacio.
*   **Sí es subespacio.** (Geométricamente, es una recta por el origen).

---

### Ejercicio 13: ¿Son subespacios?

**a) $A = \{(x, y) \in \mathbb{R}^2 : x + y = 1\}$**
*   1. $(0,0) \notin A$ porque $0+0 \neq 1$.
*   **No es subespacio.** (Es una recta que no pasa por el origen).

**b) $B = \{\vec{x} \in \mathbb{R}^3 : \vec{x} = s(2,1,1) + t(1,2,1)\}$**
*   Esto es la definición del subespacio generado (span) por los vectores $(2,1,1)$ y $(1,2,1)$.
*   Como vimos en [[Espacios Vectoriales]] y [[Subespacios]], el span de cualquier conjunto de vectores es siempre un subespacio.
*   **Sí es subespacio.** (Geométricamente, es un plano que pasa por el origen).

---

### Ejercicio 14: Hallar base del subespacio S (soluciones de sistema homogéneo)

**Método:** Resolver el sistema homogéneo $A\mathbf{x}=\vec{0}$ usando Gauss-Jordan. Expresar las variables dependientes (las que tienen pivote) en función de las variables libres. Escribir el vector solución genérico y descomponerlo en una combinación lineal donde los coeficientes son las variables libres. Los vectores de esta combinación lineal forman la base de $S=N(A)$.

 #### En la A tenemos el sistema homogéneo , donde:



tenemos el sistema homogéneo $A\mathbf{x} = \vec{0}$, donde:

$A = \begin{pmatrix} 1 & 0 & 2 \\ 2 & 1 & 3 \\ 3 & 1 & 2 \end{pmatrix}$, $\mathbf{x} = \begin{pmatrix} x \\ y \\ z \end{pmatrix}$, y $\vec{0} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$.

Nuestro objetivo es encontrar el conjunto de soluciones $S = \{\mathbf{x} \in \mathbb{R}^3 : A\mathbf{x} = \vec{0}\}$, y luego expresar este conjunto como el span de una base.

**1. Resolver el sistema homogéneo:**

Formamos la matriz aumentada $[A | \vec{0}]$ y la reducimos usando operaciones elementales de fila:

$\left[ \begin{array}{ccc|c} 1 & 0 & 2 & 0 \\ 2 & 1 & 3 & 0 \\ 3 & 1 & 2 & 0 \end{array} \right]$

*   $F_2 \rightarrow F_2 - 2F_1$:
    $\left[ \begin{array}{ccc|c} 1 & 0 & 2 & 0 \\ 0 & 1 & -1 & 0 \\ 3 & 1 & 2 & 0 \end{array} \right]$
*   $F_3 \rightarrow F_3 - 3F_1$:
    $\left[ \begin{array}{ccc|c} 1 & 0 & 2 & 0 \\ 0 & 1 & -1 & 0 \\ 0 & 1 & -4 & 0 \end{array} \right]$
*   $F_3 \rightarrow F_3 - F_2$:
    $\left[ \begin{array}{ccc|c} 1 & 0 & 2 & 0 \\ 0 & 1 & -1 & 0 \\ 0 & 0 & -3 & 0 \end{array} \right]$
*   $F_3 \rightarrow -\frac{1}{3}F_3$:
    $\left[ \begin{array}{ccc|c} 1 & 0 & 2 & 0 \\ 0 & 1 & -1 & 0 \\ 0 & 0 & 1 & 0 \end{array} \right]$
*   $F_1 \rightarrow F_1 - 2F_3$:
    $\left[ \begin{array}{ccc|c} 1 & 0 & 0 & 0 \\ 0 & 1 & -1 & 0 \\ 0 & 0 & 1 & 0 \end{array} \right]$
*   $F_2 \rightarrow F_2 + F_3$:
    $\left[ \begin{array}{ccc|c} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \end{array} \right]$

La matriz está ahora en forma escalonada reducida. Esto corresponde al sistema:

$x = 0$
$y = 0$
$z = 0$

**2. Expresar el conjunto de soluciones:**

La única solución a este sistema es $x = 0, y = 0, z = 0$. Por lo tanto, el conjunto de soluciones es:

$S = \{(0, 0, 0)\}$

**3. Encontrar una base para el subespacio de soluciones:**

El conjunto de soluciones $S$ contiene solo el vector nulo. El subespacio que contiene solo el vector nulo tiene dimensión 0, y su base es el conjunto vacío $\emptyset$ o, en algunos contextos, no se considera que tenga base.

**Conclusión:**

*   El conjunto de soluciones al sistema homogéneo $A\mathbf{x} = \vec{0}$ es $S = \{(0, 0, 0)\}$.
*   La base para este subespacio (el núcleo de A) es el conjunto vacío $\emptyset$.
*   La dimensión de este subespacio es 0.

En resumen, en este caso particular, el sistema tiene una única solución (la solución trivial), lo que significa que el núcleo de la matriz $A$ es el subespacio trivial que contiene solo el vector cero.
  
#### EN LA B TENEMOS

¡Entendido! Para el ejercicio 14b de [[Ejercicios]], tenemos el sistema homogéneo $A\mathbf{x} = \vec{0}$, donde:

$A = \begin{pmatrix} 1 & 2 & 1 & 2 & 1 \\ 1 & 2 & 2 & 1 & 2 \\ 2 & 4 & 3 & 3 & 3 \\ 0 & 0 & 1 & -1 & -1 \end{pmatrix}$, $\mathbf{x} = \begin{pmatrix} x \\ y \\ z \\ t \\ u \end{pmatrix}$, y $\vec{0} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$.

Nuestro objetivo es encontrar el conjunto de soluciones $S = \{\mathbf{x} \in \mathbb{R}^5 : A\mathbf{x} = \vec{0}\}$, y luego expresar este conjunto como el span de una base.

**1. Resolver el sistema homogéneo:**

Formamos la matriz aumentada $[A | \vec{0}]$ y la reducimos usando operaciones elementales de fila:

$\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 1 & 0 \\ 1 & 2 & 2 & 1 & 2 & 0 \\ 2 & 4 & 3 & 3 & 3 & 0 \\ 0 & 0 & 1 & -1 & -1 & 0 \end{array} \right]$

*   $F_2 \rightarrow F_2 - F_1$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 1 & 0 \\ 0 & 0 & 1 & -1 & 1 & 0 \\ 2 & 4 & 3 & 3 & 3 & 0 \\ 0 & 0 & 1 & -1 & -1 & 0 \end{array} \right]$
*   $F_3 \rightarrow F_3 - 2F_1$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 1 & 0 \\ 0 & 0 & 1 & -1 & 1 & 0 \\ 0 & 0 & 1 & -1 & 1 & 0 \\ 0 & 0 & 1 & -1 & -1 & 0 \end{array} \right]$
*   $F_3 \rightarrow F_3 - F_2$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 1 & 0 \\ 0 & 0 & 1 & -1 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 1 & -1 & -1 & 0 \end{array} \right]$
*   $F_4 \rightarrow F_4 - F_2$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 1 & 0 \\ 0 & 0 & 1 & -1 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & -2 & 0 \end{array} \right]$
*   $F_4 \rightarrow -\frac{1}{2}F_4$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 1 & 0 \\ 0 & 0 & 1 & -1 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 \end{array} \right]$
*   $F_1 \rightarrow F_1 - F_4$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 0 & 0 \\ 0 & 0 & 1 & -1 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 \end{array} \right]$
*   $F_2 \rightarrow F_2 - F_4$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 1 & 2 & 0 & 0 \\ 0 & 0 & 1 & -1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 \end{array} \right]$
*   $F_1 \rightarrow F_1 - F_2$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 0 & 3 & 0 & 0 \\ 0 & 0 & 1 & -1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 \end{array} \right]$

La matriz está ahora en forma escalonada reducida. Esto corresponde al sistema:

$x + 2y + 3t = 0$
$z - t = 0$
$u = 0$

**2. Expresar el conjunto de soluciones:**

De las ecuaciones anteriores, podemos expresar las variables dependientes en términos de las variables libres:

$x = -2y - 3t$
$z = t$
$u = 0$

Las variables libres son $y$ y $t$. Por lo tanto, el vector solución general es:

$\begin{pmatrix} x \\ y \\ z \\ t \\ u \end{pmatrix} = \begin{pmatrix} -2y - 3t \\ y \\ t \\ t \\ 0 \end{pmatrix} = y \begin{pmatrix} -2 \\ 1 \\ 0 \\ 0 \\ 0 \end{pmatrix} + t \begin{pmatrix} -3 \\ 0 \\ 1 \\ 1 \\ 0 \end{pmatrix}$

Por lo tanto, el conjunto de soluciones es:

$S = \{ y \begin{pmatrix} -2 \\ 1 \\ 0 \\ 0 \\ 0 \end{pmatrix} + t \begin{pmatrix} -3 \\ 0 \\ 1 \\ 1 \\ 0 \end{pmatrix} \mid y, t \in \mathbb{R} \}$

**3. Encontrar una base para el subespacio de soluciones:**

De la expresión anterior, podemos ver que el conjunto de soluciones es el span de dos vectores:

$v_1 = \begin{pmatrix} -2 \\ 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}$ y $v_2 = \begin{pmatrix} -3 \\ 0 \\ 1 \\ 1 \\ 0 \end{pmatrix}$

Estos vectores son linealmente independientes (ninguno es múltiplo del otro). Por lo tanto, forman una base para el subespacio de soluciones.

**Conclusión:**

*   El conjunto de soluciones al sistema homogéneo $A\mathbf{x} = \vec{0}$ es $S = \{ y \begin{pmatrix} -2 \\ 1 \\ 0 \\ 0 \\ 0 \end{pmatrix} + t \begin{pmatrix} -3 \\ 0 \\ 1 \\ 1 \\ 0 \end{pmatrix} \mid y, t \in \mathbb{R} \}$.
*   Una base para este subespacio (el núcleo de A) es $B = \{ \begin{pmatrix} -2 \\ 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}, \begin{pmatrix} -3 \\ 0 \\ 1 \\ 1 \\ 0 \end{pmatrix} \}$.
*   La dimensión de este subespacio es 2.

En resumen, el núcleo de la matriz $A$ es un subespacio de dimensión 2 en $\mathbb{R}^5$, y hemos encontrado una base para este subespacio.

#### EN LA C TENEMOS


$A = \begin{pmatrix} 1 & 2 & 2 & -1 & 1 \\ 0 & 2 & 2 & -2 & -1 \\ 2 & 6 & 2 & -4 & 1 \\ 1 & 4 & 0 & -3 & 0 \end{pmatrix}$, $\mathbf{x} = \begin{pmatrix} x \\ y \\ z \\ t \\ u \end{pmatrix}$, y $\vec{0} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$.

Nuestro objetivo es encontrar el conjunto de soluciones $S = \{\mathbf{x} \in \mathbb{R}^5 : A\mathbf{x} = \vec{0}\}$, y luego expresar este conjunto como el span de una base.

**1. Resolver el sistema homogéneo:**

Formamos la matriz aumentada $[A | \vec{0}]$ y la reducimos usando operaciones elementales de fila:

$\left[ \begin{array}{ccccc|c} 1 & 2 & 2 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 2 & 6 & 2 & -4 & 1 & 0 \\ 1 & 4 & 0 & -3 & 0 & 0 \end{array} \right]$

*   $F_3 \rightarrow F_3 - 2F_1$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 2 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 0 & 2 & -2 & -2 & -1 & 0 \\ 1 & 4 & 0 & -3 & 0 & 0 \end{array} \right]$
*   $F_4 \rightarrow F_4 - F_1$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 2 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 0 & 2 & -2 & -2 & -1 & 0 \\ 0 & 2 & -2 & -2 & -1 & 0 \end{array} \right]$
*   $F_3 \rightarrow F_3 - F_2$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 2 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 0 & 0 & -4 & 0 & 0 & 0 \\ 0 & 2 & -2 & -2 & -1 & 0 \end{array} \right]$
*   $F_4 \rightarrow F_4 - F_2$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 2 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 0 & 0 & -4 & 0 & 0 & 0 \\ 0 & 0 & -4 & 0 & 0 & 0 \end{array} \right]$
*   $F_4 \rightarrow F_4 - F_3$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 2 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 0 & 0 & -4 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{array} \right]$
*   $F_3 \rightarrow -\frac{1}{4}F_3$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 2 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{array} \right]$
*   $F_1 \rightarrow F_1 - 2F_3$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 0 & -1 & 1 & 0 \\ 0 & 2 & 2 & -2 & -1 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{array} \right]$
*   $F_2 \rightarrow F_2 - 2F_3$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 0 & -1 & 1 & 0 \\ 0 & 2 & 0 & -2 & -1 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{array} \right]$
*   $F_2 \rightarrow \frac{1}{2}F_2$:
    $\left[ \begin{array}{ccccc|c} 1 & 2 & 0 & -1 & 1 & 0 \\ 0 & 1 & 0 & -1 & -1/2 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{array} \right]$
*   $F_1 \rightarrow F_1 - 2F_2$:
    $\left[ \begin{array}{ccccc|c} 1 & 0 & 0 & 1 & 2 & 0 \\ 0 & 1 & 0 & -1 & -1/2 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{array} \right]$

La matriz está ahora en forma escalonada reducida. Esto corresponde al sistema:

$x + t + 2u = 0$
$y - t - \frac{1}{2}u = 0$
$z = 0$

**2. Expresar el conjunto de soluciones:**

De las ecuaciones anteriores, podemos expresar las variables dependientes en términos de las variables libres:

$x = -t - 2u$
$y = t + \frac{1}{2}u$
$z = 0$

Las variables libres son $t$ y $u$. Por lo tanto, el vector solución general es:

$\begin{pmatrix} x \\ y \\ z \\ t \\ u \end{pmatrix} = \begin{pmatrix} -t - 2u \\ t + \frac{1}{2}u \\ 0 \\ t \\ u \end{pmatrix} = t \begin{pmatrix} -1 \\ 1 \\ 0 \\ 1 \\ 0 \end{pmatrix} + u \begin{pmatrix} -2 \\ 1/2 \\ 0 \\ 0 \\ 1 \end{pmatrix}$

Por lo tanto, el conjunto de soluciones es:

$S = \{ t \begin{pmatrix} -1 \\ 1 \\ 0 \\ 1 \\ 0 \end{pmatrix} + u \begin{pmatrix} -2 \\ 1/2 \\ 0 \\ 0 \\ 1 \end{pmatrix} \mid t, u \in \mathbb{R} \}$

**3. Encontrar una base para el subespacio de soluciones:**

De la expresión anterior, podemos ver que el conjunto de soluciones es el span de dos vectores:

$v_1 = \begin{pmatrix} -1 \\ 1 \\ 0 \\ 1 \\ 0 \end{pmatrix}$ y $v_2 = \begin{pmatrix} -2 \\ 1/2 \\ 0 \\ 0 \\ 1 \end{pmatrix}$

Estos vectores son linealmente independientes (ninguno es múltiplo del otro). Por lo tanto, forman una base para el subespacio de soluciones. Para evitar fracciones, podemos multiplicar el segundo vector por 2 sin cambiar el subespacio generado:

$v_2' = 2v_2 = \begin{pmatrix} -4 \\ 1 \\ 0 \\ 0 \\ 2 \end{pmatrix}$

**Conclusión:**

*   El conjunto de soluciones al sistema homogéneo $A\mathbf{x} = \vec{0}$ es $S = \{ t \begin{pmatrix} -1 \\ 1 \\ 0 \\ 1 \\ 0 \end{pmatrix} + u \begin{pmatrix} -2 \\ 1/2 \\ 0 \\ 0 \\ 1 \end{pmatrix} \mid t, u \in \mathbb{R} \}$.
*   Una base para este subespacio (el núcleo de A) es $B = \{ \begin{pmatrix} -1 \\ 1 \\ 0 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} -4 \\ 1 \\ 0 \\ 0 \\ 2 \end{pmatrix} \}$.
*   La dimensión de este subespacio es 2.

En resumen, el núcleo de la matriz $A$ es un subespacio de dimensión 2 en $\mathbb{R}^5$, y hemos encontrado una base para este subespacio.

### Ejercicio 15: Extender a una base

*   **Subespacio:** $S = \langle (2,0,1), (-1,0,1) \rangle$.
*   **Análisis:** Los vectores generadores no son múltiplos, son L.I. $\dim(S)=2$. Geométricamente, es un plano en $\mathbb{R}^3$. La ecuación implícita se obtiene de:
    $\begin{vmatrix} x & y & z \\ 2 & 0 & 1 \\ -1 & 0 & 1 \end{vmatrix} = 0 \implies -y(2 - (-1)) = 0 \implies -3y = 0 \implies y=0$. Así que $S$ es el plano XZ.
*   **Vector fuera de S:** Necesitamos un vector $\mathbf{v}$ tal que $y \neq 0$. Elegimos $\mathbf{v} = (0,1,0)$.
*   **Mostrar que es base:** El conjunto es $B = \{(2,0,1), (-1,0,1), (0,1,0)\}$. Verificamos independencia lineal formando la matriz y calculando el determinante:
    $$ \det \begin{pmatrix} 2 & -1 & 0 \\ 0 & 0 & 1 \\ 1 & 1 & 0 \end{pmatrix} = -1 \begin{vmatrix} 2 & -1 \\ 1 & 1 \end{vmatrix} = -1(2 - (-1)) = -3 \neq 0 $$
*   Como tenemos 3 vectores L.I. en $\mathbb{R}^3$ (que tiene dimensión 3), forman una base de $\mathbb{R}^3$.



### Ejercicio 16: Subespacios de $\mathbb{R}^3$ y Sistemas Homogéneos

*   **Subespacios:** Como se vio en [[Subespacios]], los subespacios propios de $\mathbb{R}^3$ son:
    *   Dimensión 0: El origen $\{\vec{0}\}$.
    *   Dimensión 1: Rectas que pasan por el origen.
    *   Dimensión 2: Planos que pasan por el origen.
    *   (Dimensión 3: $\mathbb{R}^3$ mismo).
*   **Conclusiones para Sistemas Homogéneos $A\mathbf{x}=\vec{0}$ en $\mathbb{R}^3$:** El conjunto de soluciones $N(A)$ es siempre un subespacio. Por lo tanto, geométricamente, el conjunto de soluciones de un sistema lineal homogéneo de 3 variables sólo puede ser: el origen, una recta por el origen, un plano por el origen, o todo $\mathbb{R}^3$.

---

### Ejercicio 17: Probar que $N(A)$ e $Im(A)$ son subespacios

*   **a) $N(A) = \{\mathbf{x} \in \mathbb{R}^n : A\mathbf{x} = \vec{0}\}$:**
    1.  $A\vec{0} = \vec{0} \implies \vec{0} \in N(A)$.
    2.  Sean $\mathbf{x}, \mathbf{y} \in N(A)$. Entonces $A\mathbf{x}=\vec{0}$ y $A\mathbf{y}=\vec{0}$. $A(\mathbf{x}+\mathbf{y}) = A\mathbf{x} + A\mathbf{y} = \vec{0} + \vec{0} = \vec{0} \implies \mathbf{x}+\mathbf{y} \in N(A)$.
    3.  Sea $\mathbf{x} \in N(A)$ y $\lambda$ escalar. $A(\lambda\mathbf{x}) = \lambda(A\mathbf{x}) = \lambda\vec{0} = \vec{0} \implies \lambda\mathbf{x} \in N(A)$.
    *   Sí es subespacio.

*   **b) $Im(A) = \{\mathbf{y} \in \mathbb{R}^m : A\mathbf{x} = \mathbf{y} \text{ para algún } \mathbf{x} \in \mathbb{R}^n\}$:** (También llamado $Co(A)$)
    1.  $A\vec{0} = \vec{0}$, así que $\vec{0} \in Im(A)$ (tomando $\mathbf{x}=\vec{0}$).
    2.  Sean $\mathbf{y}_1, \mathbf{y}_2 \in Im(A)$. Existen $\mathbf{x}_1, \mathbf{x}_2$ tales que $A\mathbf{x}_1=\mathbf{y}_1$ y $A\mathbf{x}_2=\mathbf{y}_2$. Entonces $\mathbf{y}_1+\mathbf{y}_2 = A\mathbf{x}_1 + A\mathbf{x}_2 = A(\mathbf{x}_1+\mathbf{x}_2)$. Como $\mathbf{x}_1+\mathbf{x}_2 \in \mathbb{R}^n$, $\mathbf{y}_1+\mathbf{y}_2$ es la imagen de un vector, por lo tanto $\mathbf{y}_1+\mathbf{y}_2 \in Im(A)$.
    3.  Sea $\mathbf{y} \in Im(A)$ y $\lambda$ escalar. Existe $\mathbf{x}$ tal que $A\mathbf{x}=\mathbf{y}$. Entonces $\lambda\mathbf{y} = \lambda(A\mathbf{x}) = A(\lambda\mathbf{x})$. Como $\lambda\mathbf{x} \in \mathbb{R}^n$, $\lambda\mathbf{y}$ es la imagen de un vector, por lo tanto $\lambda\mathbf{y} \in Im(A)$.
    *   Sí es subespacio.

---

### Ejercicio 18: Probar que Eigenspace es Subespacio

*   $S = \{\mathbf{x} \in \mathbb{R}^n : A\mathbf{x} = 3\mathbf{x}\}$.
*   Reescribimos la condición: $A\mathbf{x} - 3\mathbf{x} = \vec{0} \implies A\mathbf{x} - 3I\mathbf{x} = \vec{0} \implies (A-3I)\mathbf{x} = \vec{0}$.
*   $S$ es el conjunto de soluciones del sistema homogéneo $(A-3I)\mathbf{x} = \vec{0}$.
*   Por el Ejercicio 17a, el conjunto de soluciones de cualquier sistema homogéneo (el núcleo de la matriz del sistema) es un subespacio.
*   **Sí es subespacio.**
*   **Interpretación Geométrica:** Es el conjunto de vectores que, al ser transformados por $A$, no cambian de dirección (o se invierten), solo se escalan por un factor de 3. Si $\dim(S)=1$, es una recta invariante; si $\dim(S)=2$, es un plano invariante, etc.

---

### Ejercicio 19: Span, Pertenencia, Ecuaciones Implícitas

**Método:**
*   **Geometría:** Ver dimensión del espacio generado. 2 vectores L.I. en $\mathbb{R}^3$ -> Plano por origen. 3 vectores en $\mathbb{R}^4$ -> Puede ser línea, plano o subespacio 3D por origen.
*   **Pertenencia:** Resolver el sistema $A\mathbf{\alpha} = \mathbf{v}$, donde $A$ tiene los generadores como columnas. Si es compatible, $\mathbf{v}$ pertenece.
*   **Ecuaciones:** Analizar la compatibilidad del sistema $A\mathbf{\alpha} = \mathbf{x}$ para un vector genérico $\mathbf{x}$. Reducir $[A|\mathbf{x}]$ y encontrar las condiciones sobre las componentes de $\mathbf{x}$ para que $rg(A)=rg([A|\mathbf{x}])$.

**a) $A = \langle(1,2,3), (0,1,1)\rangle$, $v = (-2, -1, -3)$**
*   Geometría: Plano por el origen en $\mathbb{R}^3$.
*   Pertenencia:
    $$ \left[ \begin{array}{cc|c} 1 & 0 & -2 \\ 2 & 1 & -1 \\ 3 & 1 & -3 \end{array} \right] \xrightarrow{F_2-2F_1, F_3-3F_1} \left[ \begin{array}{cc|c} 1 & 0 & -2 \\ 0 & 1 & 3 \\ 0 & 1 & 3 \end{array} \right] \xrightarrow{F_3-F_2} \left[ \begin{array}{cc|c} 1 & 0 & -2 \\ 0 & 1 & 3 \\ 0 & 0 & 0 \end{array} \right] $$
    Sistema compatible ($\alpha_1=-2, \alpha_2=3$). **Sí pertenece.**
*   Ecuaciones:
    $$ \left[ \begin{array}{cc|c} 1 & 0 & x \\ 2 & 1 & y \\ 3 & 1 & z \end{array} \right] \xrightarrow{F_2-2F_1, F_3-3F_1} \left[ \begin{array}{cc|c} 1 & 0 & x \\ 0 & 1 & y-2x \\ 0 & 1 & z-3x \end{array} \right] \xrightarrow{F_3-F_2} \left[ \begin{array}{cc|c} 1 & 0 & x \\ 0 & 1 & y-2x \\ 0 & 0 & (z-3x)-(y-2x) \end{array} \right] $$
    Condición: $(z-3x)-(y-2x) = 0 \implies z-x-y = 0 \implies \mathbf{x-y-z=0}$.

**b) $A = \langle(1,0,1,0), (1,1,1,1), (1,-2,1,0)\rangle$, $v = (1,1,0,-1)$**
*   Geometría: Subespacio de $\mathbb{R}^4$. Hay que ver la dimensión.
    Matriz de generadores (columnas): $\begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & -2 \\ 1 & 1 & 1 \\ 0 & 1 & 0 \end{pmatrix} \xrightarrow{F_3-F_1} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & -2 \\ 0 & 0 & 0 \\ 0 & 1 & 0 \end{pmatrix} \xrightarrow{F_4-F_2} \begin{pmatrix} 1 & 1 & 1 \\ 0 & 1 & -2 \\ 0 & 0 & 0 \\ 0 & 0 & 2 \end{pmatrix}$. Rango 3. Es un subespacio 3D en $\mathbb{R}^4$. Base: $\{(1,0,1,0), (1,1,1,1), (1,-2,1,0)\}$.
*   Pertenencia:
    $$ \left[ \begin{array}{ccc|c} 1 & 1 & 1 & 1 \\ 0 & 1 & -2 & 1 \\ 1 & 1 & 1 & 0 \\ 0 & 1 & 0 & -1 \end{array} \right] \xrightarrow{F_3-F_1} \left[ \begin{array}{ccc|c} 1 & 1 & 1 & 1 \\ 0 & 1 & -2 & 1 \\ 0 & 0 & 0 & -1 \\ 0 & 1 & 0 & -1 \end{array} \right] $$
    La tercera fila $(0,0,0|-1)$ indica que el sistema es incompatible. **No pertenece.**
*   Ecuaciones:
    $$ \left[ \begin{array}{ccc|c} 1 & 1 & 1 & x \\ 0 & 1 & -2 & y \\ 1 & 1 & 1 & z \\ 0 & 1 & 0 & t \end{array} \right] \xrightarrow{F_3-F_1} \left[ \begin{array}{ccc|c} 1 & 1 & 1 & x \\ 0 & 1 & -2 & y \\ 0 & 0 & 0 & z-x \\ 0 & 1 & 0 & t \end{array} \right] $$
    Condición: $z-x=0 \implies \mathbf{x-z=0}$.

---

### Ejercicio 20: Base, Ecuaciones, Coordenadas desde Generadores

**Método:**
1.  **Base:** Poner generadores como columnas de $A$. Reducir $A$. Las columnas originales correspondientes a pivotes forman la base.
2.  **Ecuaciones:** Usar la base $B$ encontrada. Analizar compatibilidad de $B\mathbf{\alpha} = \mathbf{x}$ para $\mathbf{x}$ genérico.
3.  **Coordenadas:** Resolver $B\mathbf{\alpha} = \mathbf{v}$ para el $\mathbf{v}$ específico (si se da).


  ¡Entendido! Vamos a resolver el Ejercicio 20 para cada uno de los subespacios dados. El objetivo es encontrar:

1.  Un sistema de ecuaciones que determine el subespacio $S$.
2.  Una base de $S$.
3.  Las coordenadas de un vector $\mathbf{v}$ de $S$ en la base encontrada. (Si no se da un vector $\mathbf{v}$, elegiremos uno).

**a) $S = \langle(1,0,0), (2,1,1), (1,1,1), (1,2,3)\rangle$**

1.  **Base de S:**

    *   Formamos la matriz $A$ con los generadores como columnas:

        $A = \begin{pmatrix} 1 & 2 & 1 & 1 \\ 0 & 1 & 1 & 2 \\ 0 & 1 & 1 & 3 \end{pmatrix}$
    *   Reducimos la matriz a su forma escalonada:

        $\begin{pmatrix} 1 & 2 & 1 & 1 \\ 0 & 1 & 1 & 2 \\ 0 & 1 & 1 & 3 \end{pmatrix} \xrightarrow{F_3 - F_2} \begin{pmatrix} 1 & 2 & 1 & 1 \\ 0 & 1 & 1 & 2 \\ 0 & 0 & 0 & 1 \end{pmatrix} \xrightarrow{F_1 - 2F_2} \begin{pmatrix} 1 & 0 & -1 & -3 \\ 0 & 1 & 1 & 2 \\ 0 & 0 & 0 & 1 \end{pmatrix} \xrightarrow{F_1 + 3F_3, F_2 - 2F_3} \begin{pmatrix} 1 & 0 & -1 & 0 \\ 0 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$
    *   Las columnas originales correspondientes a los pivotes son las columnas 1, 2 y 4. Por lo tanto, una base de $S$ es:

        $B_S = \{(1,0,0), (2,1,1), (1,2,3)\}$
    *   La dimensión de $S$ es 3.
2.  **Ecuaciones de S:**

    *   Como $S$ es un subespacio de dimensión 3 en $\mathbb{R}^3$, entonces $S = \mathbb{R}^3$. Esto significa que no hay restricciones sobre las coordenadas $(x, y, z)$, y no necesitamos ecuaciones para describir $S$.
3.  **Coordenadas de un vector v en la base $B_S$:**

    *   Como $S = \mathbb{R}^3$, podemos elegir cualquier vector $\mathbf{v} \in \mathbb{R}^3$. Por ejemplo, sea $\mathbf{v} = (4,3,4)$.
    *   Necesitamos encontrar escalares $\alpha_1, \alpha_2, \alpha_3$ tales que:

        $\mathbf{v} = \alpha_1(1,0,0) + \alpha_2(2,1,1) + \alpha_3(1,2,3)$

        Esto corresponde al sistema:

        $\begin{cases} \alpha_1 + 2\alpha_2 + \alpha_3 = 4 \\ \alpha_2 + 2\alpha_3 = 3 \\ \alpha_2 + 3\alpha_3 = 4 \end{cases}$
    *   Resolviendo el sistema:

        *   De la segunda ecuación: $\alpha_2 = 3 - 2\alpha_3$
        *   Sustituyendo en la tercera ecuación: $(3 - 2\alpha_3) + 3\alpha_3 = 4 \implies \alpha_3 = 1$
        *   Entonces, $\alpha_2 = 3 - 2(1) = 1$
        *   Finalmente, $\alpha_1 = 4 - 2(1) - 1 = 1$
    *   Por lo tanto, las coordenadas de $\mathbf{v}$ en la base $B_S$ son $(1, 1, 1)$.

**b) $S = \langle(1, -1,1,0), (1,1,0,1), (2,0,1,1)\rangle$**

1.  **Base de S:**

    *   Formamos la matriz $A$ con los generadores como columnas:

        $A = \begin{pmatrix} 1 & 1 & 2 \\ -1 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 1 & 1 \end{pmatrix}$
    *   Reducimos la matriz a su forma escalonada:

        $\begin{pmatrix} 1 & 1 & 2 \\ -1 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 1 & 1 \end{pmatrix} \xrightarrow{F_2 + F_1, F_3 - F_1} \begin{pmatrix} 1 & 1 & 2 \\ 0 & 2 & 2 \\ 0 & -1 & -1 \\ 0 & 1 & 1 \end{pmatrix} \xrightarrow{F_3 + \frac{1}{2}F_2, F_4 - \frac{1}{2}F_2} \begin{pmatrix} 1 & 1 & 2 \\ 0 & 2 & 2 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix} \xrightarrow{\frac{1}{2}F_2} \begin{pmatrix} 1 & 1 & 2 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix} \xrightarrow{F_1 - F_2} \begin{pmatrix} 1 & 0 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}$
    *   Las columnas originales correspondientes a los pivotes son las columnas 1 y 2. Por lo tanto, una base de $S$ es:

        $B_S = \{(1, -1, 1, 0), (1, 1, 0, 1)\}$
    *   La dimensión de $S$ es 2.
2.  **Ecuaciones de S:**

    *   Un vector genérico $(x, y, z, t)$ pertenece a $S$ si puede expresarse como una combinación lineal de los vectores de la base:

        $\begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = \alpha_1 \begin{pmatrix} 1 \\ -1 \\ 1 \\ 0 \end{pmatrix} + \alpha_2 \begin{pmatrix} 1 \\ 1 \\ 0 \\ 1 \end{pmatrix}$

        Esto corresponde al sistema:

        $\begin{cases} x = \alpha_1 + \alpha_2 \\ y = -\alpha_1 + \alpha_2 \\ z = \alpha_1 \\ t = \alpha_2 \end{cases}$
    *   De las dos últimas ecuaciones: $\alpha_1 = z$ y $\alpha_2 = t$. Sustituyendo en las dos primeras:

        $\begin{cases} x = z + t \\ y = -z + t \end{cases}$

        Reorganizando, obtenemos el sistema de ecuaciones que define $S$:

        $\begin{cases} x - z - t = 0 \\ y + z - t = 0 \end{cases}$
3.  **Coordenadas de un vector v en la base $B_S$:**

    *   Necesitamos un vector $\mathbf{v} \in S$. Para ello, debe cumplir las ecuaciones anteriores. Por ejemplo, sea $\mathbf{v} = (2, 0, 1, 1)$. Cumple las ecuaciones: $2 - 1 - 1 = 0$ y $0 + 1 - 1 = 0$.
    *   Necesitamos encontrar escalares $\alpha_1, \alpha_2$ tales que:

        $\mathbf{v} = \alpha_1(1, -1, 1, 0) + \alpha_2(1, 1, 0, 1)$

        Esto corresponde al sistema:

        $\begin{cases} \alpha_1 + \alpha_2 = 2 \\ -\alpha_1 + \alpha_2 = 0 \\ \alpha_1 = 1 \\ \alpha_2 = 1 \end{cases}$
    *   Resolviendo el sistema: $\alpha_1 = 1$ y $\alpha_2 = 1$.
    *   Por lo tanto, las coordenadas de $\mathbf{v}$ en la base $B_S$ son $(1, 1)$.

**c) $S = \langle(1,1,1,1,0), (−1, −1,1,1,1), (2,2,0,0,1), (1,1,5,5,2), (−1,1,1,0,0)\rangle$**

1.  **Base de S:**

    *   Formamos la matriz $A$ con los generadores como columnas:

        $A = \begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 1 & -1 & 2 & 1 & 1 \\ 1 & 1 & 0 & 5 & 1 \\ 1 & 1 & 0 & 5 & 0 \\ 0 & 1 & 1 & 2 & 0 \end{pmatrix}$
    *   Reducimos la matriz a su forma escalonada:

        $\begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 1 & -1 & 2 & 1 & 1 \\ 1 & 1 & 0 & 5 & 1 \\ 1 & 1 & 0 & 5 & 0 \\ 0 & 1 & 1 & 2 & 0 \end{pmatrix} \xrightarrow{F_2-F_1, F_3-F_1, F_4-F_1} \begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 0 & 0 & 0 & 0 & 2 \\ 0 & 2 & -2 & 4 & 2 \\ 0 & 2 & -2 & 4 & 1 \\ 0 & 1 & 1 & 2 & 0 \end{pmatrix} \xrightarrow{F_2 \leftrightarrow F_5} \begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 0 & 1 & 1 & 2 & 0 \\ 0 & 2 & -2 & 4 & 2 \\ 0 & 2 & -2 & 4 & 1 \\ 0 & 0 & 0 & 0 & 2 \end{pmatrix} \xrightarrow{F_3-2F_2, F_4-2F_2} \begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 0 & 1 & 1 & 2 & 0 \\ 0 & 0 & -4 & 0 & 2 \\ 0 & 0 & -4 & 0 & 1 \\ 0 & 0 & 0 & 0 & 2 \end{pmatrix} \xrightarrow{F_4-F_3} \begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 0 & 1 & 1 & 2 & 0 \\ 0 & 0 & -4 & 0 & 2 \\ 0 & 0 & 0 & 0 & -1 \\ 0 & 0 & 0 & 0 & 2 \end{pmatrix} \xrightarrow{F_5+2F_4} \begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 0 & 1 & 1 & 2 & 0 \\ 0 & 0 & -4 & 0 & 2 \\ 0 & 0 & 0 & 0 & -1 \\ 0 & 0 & 0 & 0 & 0 \end{pmatrix}$

        $\xrightarrow{-\frac{1}{4}F_3, -F_4} \begin{pmatrix} 1 & -1 & 2 & 1 & -1 \\ 0 & 1 & 1 & 2 & 0 \\ 0 & 0 & 1 & 0 & -1/2 \\ 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 \end{pmatrix} \xrightarrow{F_1+F_4} \begin{pmatrix} 1 & -1 & 2 & 1 & 0 \\ 0 & 1 & 1 & 2 & 0 \\ 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 \end{pmatrix} \xrightarrow{F_1-2F_3, F_2-F_3} \begin{pmatrix} 1 & -1 & 0 & 1 & 0 \\ 0 & 1 & 0 & 2 & 0 \\ 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 \end{pmatrix} \xrightarrow{F_1+F_2} \begin{pmatrix} 1 & 0 & 0 & 3 & 0 \\ 0 & 1 & 0 & 2 & 0 \\ 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 \end{pmatrix}$
    *   Las columnas originales correspondientes a los pivotes son las columnas 1, 2, 3 y 5. Por lo tanto, una base de $S$ es:

        $B_S = \{(1,1,1,1,0), (−1, −1,1,1,1), (2,2,0,0,1), (-1,1,1,0,0)\}$
    *   La dimensión de $S$ es 4.
2.  **Ecuaciones de S:**

    *   Un vector genérico $(x, y, z, t, u)$ pertenece a $S$ si puede expresarse como una combinación lineal de los vectores de la base:

        $\begin{pmatrix} x \\ y \\ z \\ t \\ u \end{pmatrix} = \alpha_1 \begin{pmatrix} 1 \\ 1 \\ 1 \\ 1 \\ 0 \end{pmatrix} + \alpha_2 \begin{pmatrix} -1 \\ -1 \\ 1 \\ 1 \\ 1 \end{pmatrix} + \alpha_3 \begin{pmatrix} 2 \\ 2 \\ 0 \\ 0 \\ 1 \end{pmatrix} + \alpha_4 \begin{pmatrix} -1 \\ 1 \\ 1 \\ 0 \\ 0 \end{pmatrix}$

        Esto corresponde al sistema:

        $\begin{cases} x = \alpha_1 - \alpha_2 + 2\alpha_3 - \alpha_4 \\ y = \alpha_1 - \alpha_2 + 2\alpha_3 + \alpha_4 \\ z = \alpha_1 + \alpha_2 \\ t = \alpha_1 + \alpha_2 \\ u = \alpha_2 + \alpha_3 \end{cases}$
    *   Observamos que $z = t$, entonces $z - t = 0$ es una ecuación que debe cumplir cualquier vector en $S$.
    *   Para encontrar otra ecuación, restamos la primera ecuación a la segunda:

        $y - x = 2\alpha_4 \implies \alpha_4 = \frac{y - x}{2}$
    *   Sumamos la primera y la segunda ecuación:

        $x + y = 2\alpha_1 - 2\alpha_2 + 4\alpha_3 \implies \alpha_1 - \alpha_2 + 2\alpha_3 = \frac{x + y}{2}$
    *   De la quinta ecuación: $\alpha_2 = u - \alpha_3$. Sustituyendo en la ecuación anterior:

        $\alpha_1 - (u - \alpha_3) + 2\alpha_3 = \frac{x + y}{2} \implies \alpha_1 - u + 3\alpha_3 = \frac{x + y}{2}$
    *   Como $z = \alpha_1 + \alpha_2 = \alpha_1 + u - \alpha_3$, entonces $\alpha_1 = z - u + \alpha_3$. Sustituyendo:

        $(z - u + \alpha_3) - u + 3\alpha_3 = \frac{x + y}{2} \implies z - 2u + 4\alpha_3 = \frac{x + y}{2} \implies 4\alpha_3 = \frac{x + y}{2} - z + 2u \implies \alpha_3 = \frac{x + y - 2z + 4u}{8}$
    *   Sustituyendo $\alpha_3$ en la quinta ecuación: $\alpha_2 = u - \frac{x + y - 2z + 4u}{8} = \frac{-x - y + 2z + 4u}{8}$
    *   Sustituyendo $\alpha_1$ y $\alpha_2$ en la primera ecuación:

        $x = \alpha_1 - \alpha_2 + 2\alpha_3 - \alpha_4 = (z - u + \alpha_3) - \frac{-x - y + 2z + 4u}{8} + 2\alpha_3 - \frac{y - x}{2}$

        $x = z - u + 3\alpha_3 - \frac{-x - y + 2z + 4u}{8} - \frac{y - x}{2}$

        $8x = 8z - 8u + 2(x + y - 2z + 4u) - (-x - y + 2z + 4u) - 4(y - x)$

        $8x = 8z - 8u + 2x + 2y - 4z + 8u + x + y - 2z - 4u - 4y + 4x$

        $8x = 7x - y + 2z - 4u$

        $x + y - 2z + 4u = 0$
    *   Por lo tanto, el sistema de ecuaciones que define $S$ es:

        $\begin{cases} z - t = 0 \\ x + y - 2z + 4u = 0 \end{cases}$
2.  **Coordenadas de un vector v en la base $B_S$:**

    *   Necesitamos un vector $\mathbf{v} \in S$. Para ello, debe cumplir las ecuaciones anteriores. Por ejemplo, sea $\mathbf{v} = (1, 1, 1, 1, 0)$. Cumple las ecuaciones: $1 - 1 = 0$ y $1 + 1 - 2(1) + 4(0) = 0$.
    *   Necesitamos encontrar escalares $\alpha_1, \alpha_2, \alpha_3, \alpha_4$ tales que:

        $\begin{pmatrix} 1 \\ 1 \\ 1 \\ 1 \\ 0 \end{pmatrix} = \alpha_1 \begin{pmatrix} 1 \\ 1 \\ 1 \\ 1 \\ 0 \end{pmatrix} + \alpha_2 \begin{pmatrix} -1 \\ -1 \\ 1 \\ 1 \\ 1 \end{pmatrix} + \alpha_3 \begin{pmatrix} 2 \\ 2 \\ 0 \\ 0 \\ 1 \end{pmatrix} + \alpha_4 \begin{pmatrix} -1 \\ 1 \\ 1 \\ 0 \\ 0 \end{pmatrix}$

        Esto corresponde al sistema:

        $\begin{cases} \alpha_1 - \alpha_2 + 2\alpha_3 - \alpha_4 = 1 \\ \alpha_1 - \alpha_2 + 2\alpha_3 + \alpha_4 = 1 \\ \alpha_1 + \alpha_2 + \alpha_4 = 1 \\ \alpha_1 + \alpha_2 = 1 \\ \alpha_2 + \alpha_3 = 0 \end{cases}$
    *   Resolviendo el sistema:

        *   De la cuarta ecuación: $\alpha_1 + \alpha_2 = 1 \implies \alpha_1 = 1 - \alpha_2$
        *   De la quinta ecuación: $\alpha_3 = -\alpha_2$
        *   Sustituyendo en la tercera ecuación: $(1 - \alpha_2) + \alpha_2 + \alpha_4 = 1 \implies \alpha_4 = 0$
        *   Sustituyendo en la primera ecuación: $(1 - \alpha_2) - \alpha_2 + 2(-\alpha_2) - 0 = 1 \implies 1 - 4\alpha_2 = 1 \implies \alpha_2 = 0$
        *   Entonces, $\alpha_1 = 1 - 0 = 1$ y $\alpha_3 = -0 = 0$
    *   Por lo tanto, las coordenadas de $\mathbf{v}$ en la base $B_S$ son $(1, 0, 0, 0)$.

**Resumen:**

*   **a)**
    *   Base: $B_S = \{(1,0,0), (2,1,1), (1,2,3)\}$
    *   Ecuaciones: No hay ecuaciones (el subespacio es todo $\mathbb{R}^3$).
    *   Coordenadas de $\mathbf{v} = (4,3,4)$: $(1, 1, 1)$
*   **b)**
    *   Base: $B_S = \{(1, -1, 1, 0), (1, 1, 0, 1)\}$
    *   Ecuaciones: $\begin{cases} x - z - t = 0 \\ y + z - t = 0 \end{cases}$
    *   Coordenadas de $\mathbf{v} = (2, 0, 1, 1)$: $(1, 1)$
*   **c)**
    *   Base: $B_S = \{(1,1,1,1,0), (−1, −1,1,1,1), (2,2,0,0,1), (-1,1,1,0,0)\}$
    *   Ecuaciones: $\begin{cases} z - t = 0 \\ x + y - 2z + 4u = 0 \end{cases}$
    *   Coordenadas de $\mathbf{v} = (1, 1, 1, 1, 0)$: $(1, 0, 0, 0)$

Espero que esta explicación detallada te sea útil. Avísame si tienes más preguntas.

---

### Ejercicio 21: Complemento Ortogonal $S^\perp$

*   **Prueba de que es subespacio:** Ya realizada en el análisis del Ejercicio 17a (para $N(A)$) y 21.
*   **Complemento ortogonal del plano xy en $\mathbb{R}^3$:**
    *   Plano xy: $S = \{(x,y,0)\} = \langle (1,0,0), (0,1,0) \rangle$.
    *   Formar $A$ con generadores como filas: $A = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \end{pmatrix}$.
    *   $S^\perp = N(A)$. Resolver $A\mathbf{x}=\vec{0}$:
        $1x + 0y + 0z = 0 \implies x=0$
        $0x + 1y + 0z = 0 \implies y=0$
        $z$ es libre.
    *   Solución: $(0,0,z) = z(0,0,1)$.
    *   $S^\perp = \langle (0,0,1) \rangle$ (el eje Z).

---

### Ejercicio 22: Base para $S^\perp$

*   $S = \langle (1,1,-1,1), (1,1,2,3) \rangle \subset \mathbb{R}^4$.
*   **Método:** $S^\perp = N(A)$ donde $A$ tiene los generadores como filas.
    $A = \begin{pmatrix} 1 & 1 & -1 & 1 \\ 1 & 1 & 2 & 3 \end{pmatrix} \xrightarrow{F_2-F_1} \begin{pmatrix} 1 & 1 & -1 & 1 \\ 0 & 0 & 3 & 2 \end{pmatrix}$.
*   Resolver $A\mathbf{x}=\vec{0}$ (usando la forma escalonada):
    $x + y - z + t = 0$
    $3z + 2t = 0 \implies z = -2/3 t$
    Variables libres: $y, t$.
    $x = -y + z - t = -y - 2/3 t - t = -y - 5/3 t$.
*   Vector solución: $(x,y,z,t) = (-y - 5/3 t, y, -2/3 t, t) = y(-1, 1, 0, 0) + t(-5/3, 0, -2/3, 1)$.
*   **Base para $S^\perp$:** $\{(-1, 1, 0, 0), (-5/3, 0, -2/3, 1)\}$ (o múltiplos como $\{(-1, 1, 0, 0), (-5, 0, -2, 3)\}$).

---

### Ejercicio 23: Dimensión, Base, $S^\perp$, Base $S^\perp$, Dim $S^\perp$

**Método:**
1.  **Base S:** Si $S$ dado por ecuaciones $A\mathbf{x}=\vec{0}$, $S=N(A)$. Resolver sistema para hallar base de $N(A)$. $\dim(S) = n - rg(A)$.
2.  **Base $S^\perp$:** $S^\perp = (N(A))^\perp = Fi(A)$. Base son filas L.I. de $A$ (o su forma escalonada). $\dim(S^\perp) = rg(A)$.
3.  Verificar $\dim(S) + \dim(S^\perp) = n$.

**a) $S = \{(x, y, z) \in \mathbb{R}^3 : x + 2y - z = 0\}$**
*   $A = \begin{pmatrix} 1 & 2 & -1 \end{pmatrix}$. $n=3$. $rg(A)=1$.
*   $\dim(S) = n - rg(A) = 3 - 1 = 2$.
*   Base S: $x = -2y+z$. $(x,y,z) = (-2y+z, y, z) = y(-2,1,0) + z(1,0,1)$. Base $B_S = \{(-2,1,0), (1,0,1)\}$.
*   $\dim(S^\perp) = rg(A) = 1$.
*   Base $S^\perp$: Fila de A. $B_{S^\perp} = \{(1, 2, -1)\}$.

**b) $S = \{(x, y, z) \in \mathbb{R}^3 : x + 2y - 4z = 0; y - 4z = 0\}$**
*   $A = \begin{pmatrix} 1 & 2 & -4 \\ 0 & 1 & -4 \end{pmatrix} \xrightarrow{F_1-2F_2} \begin{pmatrix} 1 & 0 & 4 \\ 0 & 1 & -4 \end{pmatrix}$. $n=3$. $rg(A)=2$.
*   $\dim(S) = n - rg(A) = 3 - 2 = 1$.
*   Base S: $x=-4z, y=4z$. $(x,y,z) = (-4z, 4z, z) = z(-4, 4, 1)$. Base $B_S = \{(-4, 4, 1)\}$.
*   $\dim(S^\perp) = rg(A) = 2$.
*   Base $S^\perp$: Filas L.I. de A (o su forma escalonada). $B_{S^\perp} = \{(1, 0, 4), (0, 1, -4)\}$.

**c) $S = \{(x, y, z,t) \in \mathbb{R}^4 : x - y - z + t = 0; x + y + z + t = 0\}$**
*   $A = \begin{pmatrix} 1 & -1 & -1 & 1 \\ 1 & 1 & 1 & 1 \end{pmatrix} \xrightarrow{F_2-F_1} \begin{pmatrix} 1 & -1 & -1 & 1 \\ 0 & 2 & 2 & 0 \end{pmatrix} \xrightarrow{F_2/2} \begin{pmatrix} 1 & -1 & -1 & 1 \\ 0 & 1 & 1 & 0 \end{pmatrix} \xrightarrow{F_1+F_2} \begin{pmatrix} 1 & 0 & 0 & 1 \\ 0 & 1 & 1 & 0 \end{pmatrix}$. $n=4$. $rg(A)=2$.
*   $\dim(S) = n - rg(A) = 4 - 2 = 2$.
*   Base S: $x=-t, y=-z$. $(x,y,z,t) = (-t, -z, z, t) = z(0,-1,1,0) + t(-1,0,0,1)$. Base $B_S = \{(0,-1,1,0), (-1,0,0,1)\}$.
*   $\dim(S^\perp) = rg(A) = 2$.
*   Base $S^\perp$: Filas L.I. de A (o su forma escalonada). $B_{S^\perp} = \{(1, 0, 0, 1), (0, 1, 1, 0)\}$.

---

### Ejercicio 24: Intersección y Unión

*   **Intersección $S \cap T$:**
    1. $\vec{0} \in S$ y $\vec{0} \in T$ (por ser subespacios) $\implies \vec{0} \in S \cap T$.
    2. Sean $\mathbf{u}, \mathbf{v} \in S \cap T$. Entonces $\mathbf{u}, \mathbf{v} \in S$ y $\mathbf{u}, \mathbf{v} \in T$. Como $S, T$ son subespacios, $\mathbf{u}+\mathbf{v} \in S$ y $\mathbf{u}+\mathbf{v} \in T$. Por lo tanto $\mathbf{u}+\mathbf{v} \in S \cap T$.
    3. Sea $\mathbf{u} \in S \cap T$ y $\lambda$ escalar. Entonces $\mathbf{u} \in S$ y $\mathbf{u} \in T$. Como $S, T$ son subespacios, $\lambda\mathbf{u} \in S$ y $\lambda\mathbf{u} \in T$. Por lo tanto $\lambda\mathbf{u} \in S \cap T$.
    *   **Sí es subespacio.**
*   **Unión $S \cup T$:**
    *   Generalmente **no es subespacio**. Falla la clausura bajo la suma. Ejemplo: $S=$eje X, $T=$eje Y en $\mathbb{R}^2$. $(1,0) \in S \cup T$, $(0,1) \in S \cup T$, pero $(1,0)+(0,1)=(1,1) \notin S \cup T$.

---

### Ejercicio 25, 26: Suma e Intersección (Generadores/Ecuaciones)

**Método:**
1.  **Ecuaciones:** Para cada subespacio dado por generadores, encontrar sus ecuaciones implícitas.
2.  **Intersección $S \cap T$:** Juntar las ecuaciones de $S$ y $T$. Resolver el sistema homogéneo resultante para hallar una base de $S \cap T$.
3.  **Suma $S + T$:** Juntar los generadores de $S$ y $T$. Ponerlos como columnas de una matriz y reducir. Las columnas originales correspondientes a los pivotes forman una base de $S+T$. (O usar Grassmann si ya se tienen las dimensiones).


#### LA 5 A
De acuerdo, vamos a resolver el Ejercicio 25 con los siguientes subespacios de $\mathbb{R}^3$:

*   $S = \langle (1, 2, 1), (1, 1, -1), (1, 3, 3) \rangle$
*   $T = \langle (2, 3, -1), (1, 2, 2), (1, 1, -3) \rangle$

El objetivo es encontrar:

1.  Una base para $S \cap T$ (la intersección de $S$ y $T$).
2.  Una base para $S + T$ (la suma de $S$ y $T$).

**1. Simplificar los Generadores de S y T**

Primero, vamos a simplificar los conjuntos de generadores para $S$ y $T$ para encontrar bases más eficientes.

**Para S:**

Formamos la matriz con los generadores como columnas y reducimos:

$\begin{pmatrix} 1 & 1 & 1 \\ 2 & 1 & 3 \\ 1 & -1 & 3 \end{pmatrix} \xrightarrow{F_2-2F_1, F_3-F_1} \begin{pmatrix} 1 & 1 & 1 \\ 0 & -1 & 1 \\ 0 & -2 & 2 \end{pmatrix} \xrightarrow{F_3-2F_2} \begin{pmatrix} 1 & 1 & 1 \\ 0 & -1 & 1 \\ 0 & 0 & 0 \end{pmatrix}$

Como el rango es 2, solo necesitamos dos vectores para generar $S$. Podemos tomar los dos primeros vectores originales:

$S = \langle (1, 2, 1), (1, 1, -1) \rangle$

**Para T:**

Formamos la matriz con los generadores como columnas y reducimos:

$\begin{pmatrix} 2 & 1 & 1 \\ 3 & 2 & 1 \\ -1 & 2 & -3 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_3} \begin{pmatrix} -1 & 2 & -3 \\ 3 & 2 & 1 \\ 2 & 1 & 1 \end{pmatrix} \xrightarrow{F_2+3F_1, F_3+2F_1} \begin{pmatrix} -1 & 2 & -3 \\ 0 & 8 & -8 \\ 0 & 5 & -5 \end{pmatrix} \xrightarrow{\frac{1}{8}F_2} \begin{pmatrix} -1 & 2 & -3 \\ 0 & 1 & -1 \\ 0 & 5 & -5 \end{pmatrix} \xrightarrow{F_3-5F_2} \begin{pmatrix} -1 & 2 & -3 \\ 0 & 1 & -1 \\ 0 & 0 & 0 \end{pmatrix}$

Como el rango es 2, solo necesitamos dos vectores para generar $T$. Podemos tomar los dos primeros vectores originales:

$T = \langle (2, 3, -1), (1, 2, 2) \rangle$

**2. Encontrar las Ecuaciones Implícitas de S y T**

Para encontrar la intersección, necesitamos las ecuaciones implícitas de $S$ y $T$.

**Para S:**

Sea $(x, y, z)$ un vector genérico en $S$. Entonces, debe ser una combinación lineal de los generadores:

$\begin{pmatrix} x \\ y \\ z \end{pmatrix} = \alpha \begin{pmatrix} 1 \\ 2 \\ 1 \end{pmatrix} + \beta \begin{pmatrix} 1 \\ 1 \\ -1 \end{pmatrix}$

Esto nos da el sistema:

$\begin{cases} x = \alpha + \beta \\ y = 2\alpha + \beta \\ z = \alpha - \beta \end{cases}$

Restamos la tercera ecuación de la primera: $x - z = 2\beta \implies \beta = \frac{x - z}{2}$
Restamos la primera ecuación de la segunda: $y - x = \alpha \implies \alpha = y - x$

Sustituimos en la tercera ecuación: $z = (y - x) - \frac{x - z}{2} \implies 2z = 2y - 2x - x + z \implies z = 2y - 3x \implies 3x - 2y + z = 0$

Por lo tanto, la ecuación implícita de $S$ es: $3x - 2y + z = 0$

**Para T:**

Sea $(x, y, z)$ un vector genérico en $T$. Entonces, debe ser una combinación lineal de los generadores:

$\begin{pmatrix} x \\ y \\ z \end{pmatrix} = \alpha \begin{pmatrix} 2 \\ 3 \\ -1 \end{pmatrix} + \beta \begin{pmatrix} 1 \\ 2 \\ 2 \end{pmatrix}$

Esto nos da el sistema:

$\begin{cases} x = 2\alpha + \beta \\ y = 3\alpha + 2\beta \\ z = -\alpha + 2\beta \end{cases}$

Multiplicamos la primera ecuación por 2 y restamos la segunda: $2x - y = \beta \implies \beta = 2x - y$
Sustituimos en la primera ecuación: $x = 2\alpha + (2x - y) \implies -x + y = 2\alpha \implies \alpha = \frac{-x + y}{2}$

Sustituimos en la tercera ecuación: $z = -\frac{-x + y}{2} + 2(2x - y) \implies 2z = x - y + 8x - 4y \implies 2z = 9x - 5y \implies 9x - 5y - 2z = 0$

Por lo tanto, la ecuación implícita de $T$ es: $9x - 5y - 2z = 0$

**3. Encontrar la Intersección $S \cap T$**

Para encontrar $S \cap T$, juntamos las ecuaciones de $S$ y $T$:

$\begin{cases} 3x - 2y + z = 0 \\ 9x - 5y - 2z = 0 \end{cases}$

Multiplicamos la primera ecuación por 2 y sumamos a la segunda: $6x - 4y + 2z + 9x - 5y - 2z = 0 \implies 15x - 9y = 0 \implies 5x = 3y \implies x = \frac{3}{5}y$

Sustituimos en la primera ecuación: $3(\frac{3}{5}y) - 2y + z = 0 \implies \frac{9}{5}y - 2y + z = 0 \implies \frac{9y - 10y}{5} + z = 0 \implies -\frac{1}{5}y + z = 0 \implies z = \frac{1}{5}y$

Por lo tanto, el vector genérico en $S \cap T$ es:

$\begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} \frac{3}{5}y \\ y \\ \frac{1}{5}y \end{pmatrix} = y \begin{pmatrix} \frac{3}{5} \\ 1 \\ \frac{1}{5} \end{pmatrix}$

Para evitar fracciones, multiplicamos por 5:

$B_{S \cap T} = \{(3, 5, 1)\}$

La dimensión de $S \cap T$ es 1.

**4. Encontrar la Suma $S + T$**

La suma $S + T$ está generada por la unión de los generadores de $S$ y $T$:

$S + T = \langle (1, 2, 1), (1, 1, -1), (2, 3, -1), (1, 2, 2) \rangle$

Formamos la matriz con estos generadores como columnas y reducimos:

$\begin{pmatrix} 1 & 1 & 2 & 1 \\ 2 & 1 & 3 & 2 \\ 1 & -1 & -1 & 2 \end{pmatrix} \xrightarrow{F_2-2F_1, F_3-F_1} \begin{pmatrix} 1 & 1 & 2 & 1 \\ 0 & -1 & -1 & 0 \\ 0 & -2 & -3 & 1 \end{pmatrix} \xrightarrow{F_3-2F_2} \begin{pmatrix} 1 & 1 & 2 & 1 \\ 0 & -1 & -1 & 0 \\ 0 & 0 & -1 & 1 \end{pmatrix}$

Como el rango es 3, necesitamos 3 vectores para generar $S + T$. Podemos tomar los tres primeros vectores originales:

$B_{S + T} = \{(1, 2, 1), (1, 1, -1), (2, 3, -1)\}$

La dimensión de $S + T$ es 3. Como estamos en $\mathbb{R}^3$, esto significa que $S + T = \mathbb{R}^3$.

**Resumen:**

*   Base para $S \cap T$: $B_{S \cap T} = \{(3, 5, 1)\}$
*   Base para $S + T$: $B_{S + T} = \{(1, 2, 1), (1, 1, -1), (2, 3, -1)\}$

**Verificación con la fórmula de Grassmann:**

$\dim(S + T) = \dim(S) + \dim(T) - \dim(S \cap T)$
$3 = 2 + 2 - 1$
$3 = 3$ (¡Correcto!)

Espero que esta solución detallada te sea útil. Avísame si tienes más preguntas.

---

### Ejercicio 27: Dimensión de Suma

*   $S_1: x+y-z+t=0$
*   $S_2: x-y-z-t=0$
*   **Método:** Usar Grassmann: $\dim(S_1+S_2) = \dim(S_1) + \dim(S_2) - \dim(S_1 \cap S_2)$.
    *   $\dim(S_1) = n - rg(A_1) = 4 - 1 = 3$.
    *   $\dim(S_2) = n - rg(A_2) = 4 - 1 = 3$.
    *   $S_1 \cap S_2$: Sistema $\begin{cases} x+y-z+t=0 \\ x-y-z-t=0 \end{cases}$. Matriz $A = \begin{pmatrix} 1 & 1 & -1 & 1 \\ 1 & -1 & -1 & -1 \end{pmatrix} \xrightarrow{F_2-F_1} \begin{pmatrix} 1 & 1 & -1 & 1 \\ 0 & -2 & 0 & -2 \end{pmatrix} \xrightarrow{F_2/(-2)} \begin{pmatrix} 1 & 1 & -1 & 1 \\ 0 & 1 & 0 & 1 \end{pmatrix} \xrightarrow{F_1-F_2} \begin{pmatrix} 1 & 0 & -1 & 0 \\ 0 & 1 & 0 & 1 \end{pmatrix}$. $rg(A)=2$.
    *   $\dim(S_1 \cap S_2) = n - rg(A) = 4 - 2 = 2$.
    *   $\dim(S_1+S_2) = 3 + 3 - 2 = 4$. (La suma es todo $\mathbb{R}^4$).

---

### Ejercicio 28: $\dim(S) + \dim(T) > \dim(V) \implies S \cap T \neq \{\vec{0}\}$

*   **Prueba:** Por Grassmann, $\dim(S \cap T) = \dim(S) + \dim(T) - \dim(S+T)$.
*   Como $S+T$ es subespacio de $V$, $\dim(S+T) \le \dim(V)$.
*   Entonces, $-\dim(S+T) \ge -\dim(V)$.
*   Sustituyendo: $\dim(S \cap T) \ge \dim(S) + \dim(T) - \dim(V)$.
*   Dado que $\dim(S) + \dim(T) > \dim(V)$, el lado derecho es $> 0$.
*   Por lo tanto, $\dim(S \cap T) > 0$.
*   Un subespacio de dimensión mayor que cero no puede ser solo $\{\vec{0}\}$.

---

### Ejercicio 29: Suma Directa

**Método:**
1.  Calcular $S \cap T$. Si $S \cap T \neq \{\vec{0}\}$, no es suma directa.
2.  Si $S \cap T = \{\vec{0}\}$, calcular $\dim(S)$ y $\dim(T)$.
3.  Verificar si $\dim(S) + \dim(T) = \dim(V)$. Si sí, $V = S \oplus T$. Si no, $S+T$ es directa pero no es todo $V$.

**a) $V=\mathbb{R}^3$, $S: x+y+z=0$, $T=\langle(1,1,1)\rangle$**
*   $S$ es un plano, $\dim(S)=3-1=2$. $T$ es una recta, $\dim(T)=1$.
*   Intersección: ¿Pertenece $(1,1,1)$ a $S$? $1+1+1 = 3 \neq 0$. No pertenece. Como $T$ es solo múltiplos de $(1,1,1)$, el único vector de $T$ que podría estar en $S$ es $\vec{0}$ (cuando el múltiplo es 0). $S \cap T = \{\vec{0}\}$.
*   $\dim(S)+\dim(T) = 2+1=3 = \dim(\mathbb{R}^3)$.
*   **Sí es suma directa, y $V = S \oplus T$.** (De hecho, $T=S^\perp$).

**b) ¡Entendido! Vamos a resolver el Ejercicio 29b.

**Ejercicio 29b:**

$V = \mathbb{R}^4$

$S = \{(x, y, z, t) \in \mathbb{R}^4 : x + y + z + t = 0, x - y - z + t = 0\}$

$T = \{(x, y, z, t) \in \mathbb{R}^4 : x + y - z - t = 0, x - y + z - t = 0, x + 2y + z - 2t = 0\}$

**Objetivo:** Determinar si $V = S \oplus T$.

**Método:**

1.  **Hallar la dimensión de S y T:**
2.  **Hallar $S \cap T$:**
3.  **Verificar si $S \cap T = \{\vec{0}\}$:**
4.  **Verificar si $\dim(S) + \dim(T) = \dim(V)$:**

**1. Hallar la dimensión de S y T:**

*   **Para S:**
    Tenemos el sistema:
    $\begin{cases} x + y + z + t = 0 \\ x - y - z + t = 0 \end{cases}$
    La matriz de coeficientes es:
    $A_S = \begin{pmatrix} 1 & 1 & 1 & 1 \\ 1 & -1 & -1 & 1 \end{pmatrix} \xrightarrow{F_2 - F_1} \begin{pmatrix} 1 & 1 & 1 & 1 \\ 0 & -2 & -2 & 0 \end{pmatrix} \xrightarrow{-\frac{1}{2}F_2} \begin{pmatrix} 1 & 1 & 1 & 1 \\ 0 & 1 & 1 & 0 \end{pmatrix} \xrightarrow{F_1 - F_2} \begin{pmatrix} 1 & 0 & 0 & 1 \\ 0 & 1 & 1 & 0 \end{pmatrix}$
    El rango de $A_S$ es 2. Por lo tanto, $\dim(S) = n - rg(A_S) = 4 - 2 = 2$.
*   **Para T:**
    Tenemos el sistema:
    $\begin{cases} x + y - z - t = 0 \\ x - y + z - t = 0 \\ x + 2y + z - 2t = 0 \end{cases}$
    La matriz de coeficientes es:
    $A_T = \begin{pmatrix} 1 & 1 & -1 & -1 \\ 1 & -1 & 1 & -1 \\ 1 & 2 & 1 & -2 \end{pmatrix} \xrightarrow{F_2 - F_1, F_3 - F_1} \begin{pmatrix} 1 & 1 & -1 & -1 \\ 0 & -2 & 2 & 0 \\ 0 & 1 & 2 & -1 \end{pmatrix} \xrightarrow{F_2 \leftrightarrow F_3} \begin{pmatrix} 1 & 1 & -1 & -1 \\ 0 & 1 & 2 & -1 \\ 0 & -2 & 2 & 0 \end{pmatrix} \xrightarrow{F_3 + 2F_2} \begin{pmatrix} 1 & 1 & -1 & -1 \\ 0 & 1 & 2 & -1 \\ 0 & 0 & 6 & -2 \end{pmatrix}$
    El rango de $A_T$ es 3. Por lo tanto, $\dim(T) = n - rg(A_T) = 4 - 3 = 1$.

**2. Hallar $S \cap T$:**

Para encontrar $S \cap T$, combinamos las ecuaciones de $S$ y $T$:

$\begin{cases} x + y + z + t = 0 \\ x - y - z + t = 0 \\ x + y - z - t = 0 \\ x - y + z - t = 0 \\ x + 2y + z - 2t = 0 \end{cases}$

Sumamos la primera y la segunda ecuación: $2x + 2t = 0 \implies x = -t$
Sumamos la tercera y la cuarta ecuación: $2x - 2t = 0 \implies x = t$

Por lo tanto, $x = t = 0$. Sustituyendo en las ecuaciones originales:

$\begin{cases} y + z = 0 \\ -y + z = 0 \\ 2y + z = 0 \end{cases}$

Sumando la primera y la segunda ecuación: $2z = 0 \implies z = 0$. Entonces, $y = 0$.

Por lo tanto, la única solución es $x = y = z = t = 0$.

**3. Verificar si $S \cap T = \{\vec{0}\}$:**

Sí, $S \cap T = \{(0, 0, 0, 0)\}$.

**4. Verificar si $\dim(S) + \dim(T) = \dim(V)$:**

$\dim(S) + \dim(T) = 2 + 1 = 3$
$\dim(V) = \dim(\mathbb{R}^4) = 4$

Como $\dim(S) + \dim(T) \neq \dim(V)$, entonces $V \neq S \oplus T$.

**Conclusión:**

*   $S \cap T = \{\vec{0}\}$ (la intersección es trivial).
*   $\dim(S) = 2$
*   $\dim(T) = 1$
*   $\dim(S) + \dim(T) = 3 \neq 4 = \dim(V)$

Por lo tanto, **no es suma directa, y $V \neq S \oplus T$**. La suma $S+T$ es directa, pero no es todo $\mathbb{R}^4$.

---

### Ejercicio 30: Combinaciones

**a) $S = \langle(1,1,-1,2)\rangle$, $T: x+2y-t=0 \land z+t=0$. Hallar $W = S^\perp \cap T$.**
1.  $S^\perp = N(A)$ con $A=\begin{pmatrix} 1 & 1 & -1 & 2 \end{pmatrix}$. Ecuación: $x+y-z+2t=0$.
2.  $W = S^\perp \cap T$: Juntar las 3 ecuaciones:
    $x+y-z+2t=0$
    $x+2y-t=0$
    $z+t=0$
3.  Resolver este sistema homogéneo para encontrar una base de $W$.

**b) $S: x-2y+z=0$, $T: x=y \land z=0$. Hallar $W$ tal que $T \subset W$ y $S^\perp \oplus W = \mathbb{R}^3$.**
1.  $S^\perp = Fi(A)$ con $A=\begin{pmatrix} 1 & -2 & 1 \end{pmatrix}$. $S^\perp = \langle(1,-2,1)\rangle$. $\dim(S^\perp)=1$.
2.  Necesitamos $\dim(W) = 3 - \dim(S^\perp) = 3-1=2$.
3.  Base para $T$: $x=y, z=0$. $(x,y,z)=(y,y,0)=y(1,1,0)$. Base $B_T = \{(1,1,0)\}$.
4.  $T \subset W$. Necesitamos añadir un vector $\mathbf{u}$ a $B_T$ para formar una base de $W$, tal que $\mathbf{u} \notin T$ y $W \cap S^\perp = \{\vec{0}\}$.
5.  Como $W$ debe ser complemento (no necesariamente ortogonal) de $S^\perp$, la base de $W$ debe ser L.I. con la base de $S^\perp$.
6.  Base $B_W = \{(1,1,0), \mathbf{u}\}$. Necesitamos que $\{(1,1,0), \mathbf{u}, (1,-2,1)\}$ sea base de $\mathbb{R}^3$.
7.  Podemos elegir $\mathbf{u}$ tal que el determinante de la matriz formada por los 3 vectores sea no nulo. Por ejemplo, $\mathbf{u}=(0,0,1)$.
    $\det \begin{pmatrix} 1 & 0 & 1 \\ 1 & 0 & -2 \\ 0 & 1 & 1 \end{pmatrix} = -1( -2 - 1) = 3 \neq 0$.
8.  $W = \langle (1,1,0), (0,0,1) \rangle$.

---

### Ejercicio 31, 32: Parámetros $a, k$

*(Requieren resolver sistemas y analizar condiciones sobre $a$ o $k$ para que se cumplan las propiedades de inclusión o suma directa)*

---

### Ejercicio 33, 34: Subespacios Fundamentales

**Método:**
1.  Reducir $A$ a forma escalonada $R$. Rango $r$.
2.  **Base $Fi(A)$:** Filas no nulas de $R$. $\dim=r$.
3.  **Base $Co(A)$:** Columnas originales de $A$ correspondientes a pivotes en $R$. $\dim=r$.
4.  **Base $N(A)$:** Resolver $A\mathbf{x}=\vec{0}$ (o $R\mathbf{x}=\vec{0}$). $\dim=n-r$.
5.  **Base $N(A^t)$:** Reducir $A^t$. Resolver $A^t\mathbf{y}=\vec{0}$. $\dim=m-r$.
6.  **Ecuaciones:** Para $Fi(A), Co(A)$ usar método de compatibilidad. Para $N(A), N(A^t)$ usar las ecuaciones del sistema homogéneo.
7.  **Comprobar $Fi(A) = N(A)^\perp$:** Verificar que los vectores base de $Fi(A)$ son ortogonales a los vectores base de $N(A)$ y que $\dim(Fi(A)) + \dim(N(A)) = n$.

*(Cálculos específicos dependen de las matrices)*

---

### Ejercicio 35: Dimensión del Espacio Solución

**Método:**
1.  Escribir el sistema como $A\mathbf{x}=\vec{0}$.
2.  Hallar el rango $r$ de la matriz $A$ mediante reducción Gaussiana.
3.  La dimensión del espacio de soluciones $N(A)$ es $n-r$, donde $n$ es el número de variables.

**a) $n=3$.**
$A = \begin{pmatrix} 3 & 2 & -4 \\ 1 & -2 & 1 \\ 10 & 4 & -4 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & -2 & 1 \\ 3 & 2 & -4 \\ 10 & 4 & -4 \end{pmatrix} \xrightarrow{F_2-3F_1, F_3-10F_1} \begin{pmatrix} 1 & -2 & 1 \\ 0 & 8 & -7 \\ 0 & 24 & -14 \end{pmatrix} \xrightarrow{F_3-3F_2} \begin{pmatrix} 1 & -2 & 1 \\ 0 & 8 & -7 \\ 0 & 0 & 7 \end{pmatrix}$.
Rango $r=3$.
$\dim(S) = n-r = 3-3 = 0$. (Solución única: la trivial).

**b) $n=3$.**
$A = \begin{pmatrix} 2 & 1 & 0 \\ 1 & -1 & 0 \\ 4 & -1 & -1 \\ 1 & 1 & 10 \end{pmatrix} \xrightarrow{F_1 \leftrightarrow F_2} \begin{pmatrix} 1 & -1 & 0 \\ 2 & 1 & 0 \\ 4 & -1 & -1 \\ 1 & 1 & 10 \end{pmatrix} \xrightarrow{...} \begin{pmatrix} 1 & -1 & 0 \\ 0 & 3 & 0 \\ 0 & 3 & -1 \\ 0 & 2 & 10 \end{pmatrix} \xrightarrow{...} \begin{pmatrix} 1 & -1 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & -1 \\ 0 & 0 & 10 \end{pmatrix} \xrightarrow{...} \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & 0 \end{pmatrix}$.
Rango $r=3$.
$\dim(S) = n-r = 3-3 = 0$. (Solución única: la trivial).