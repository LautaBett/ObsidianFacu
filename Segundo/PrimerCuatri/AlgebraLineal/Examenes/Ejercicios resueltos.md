Para determinar si la transformación lineal $T$ es diagonalizable y, en caso afirmativo, encontrar la matriz $P$ tal que $P^{-1}AP = D$, seguiremos los siguientes pasos:

**1. Encontrar la matriz $A$ de la transformación lineal en la base canónica.**

Tenemos la matriz $[T]_{B_1, B_2}$. Necesitamos encontrar la matriz $A$ tal que $A = [T]_{C, C}$, donde $C$ es la base canónica. Para ello, necesitamos las matrices de cambio de base.

*   $B_1 = \{(0, 1, 0), (0, 0, 1), (-1, 0, 0)\}$
*   $B_2 = \{(1, 1, 0), (0, 1, 1), (1, 0, 1)\}$

La matriz de cambio de base de $B_1$ a la base canónica $C$ es:

$P_{B_1 \to C} = \begin{bmatrix} 0 & 0 & -1 \\ 1 & 0 & 0 \\ 0 & 1 & 0 \end{bmatrix}$

La matriz de cambio de base de $B_2$ a la base canónica $C$ es:

$P_{B_2 \to C} = \begin{bmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 1 & 1 \end{bmatrix}$

Entonces, podemos encontrar la matriz $A$ en la base canónica como:

$A = P_{B_2 \to C} [T]_{B_1, B_2} P_{C \to B_1}$

Donde $P_{C \to B_1} = (P_{B_1 \to C})^{-1}$. Calculamos la inversa de $P_{B_1 \to C}$:

$P_{C \to B_1} = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ -1 & 0 & 0 \end{bmatrix}$

Ahora calculamos $A$:

$A = \begin{bmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 1 & 1 \end{bmatrix} \begin{bmatrix} 0 & 1/2 & -2 \\ 2 & 1/2 & 2 \\ -1 & -1/2 & 0 \end{bmatrix} \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ -1 & 0 & 0 \end{bmatrix}$

$A = \begin{bmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 1 & 1 \end{bmatrix} \begin{bmatrix} 2 & 1/2 & -2 \\ -2 & 1/2 & 2 \\ 0 & -1/2 & 0 \end{bmatrix}$

$A = \begin{bmatrix} 2 & 0 & -2 \\ 0 & 1 & 0 \\ -2 & 0 & 2 \end{bmatrix}$

**2. Calcular los valores propios de $A$.**

Para encontrar los valores propios, resolvemos la ecuación $\det(A - \lambda I) = 0$:

$\det \begin{bmatrix} 2-\lambda & 0 & -2 \\ 0 & 1-\lambda & 0 \\ -2 & 0 & 2-\lambda \end{bmatrix} = (1-\lambda) \det \begin{bmatrix} 2-\lambda & -2 \\ -2 & 2-\lambda \end{bmatrix} = 0$

$(1-\lambda)((2-\lambda)^2 - 4) = (1-\lambda)(\lambda^2 - 4\lambda) = (1-\lambda)\lambda(\lambda - 4) = 0$

Los valores propios son $\lambda_1 = 0$, $\lambda_2 = 1$, $\lambda_3 = 4$.

**3. Calcular los vectores propios asociados a cada valor propio.**

*   Para $\lambda_1 = 0$:

$(A - 0I)v = 0 \Rightarrow \begin{bmatrix} 2 & 0 & -2 \\ 0 & 1 & 0 \\ -2 & 0 & 2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$

$2x - 2z = 0 \Rightarrow x = z$
$y = 0$

$v_1 = \begin{bmatrix} 1 \\ 0 \\ 1 \end{bmatrix}$

*   Para $\lambda_2 = 1$:

$(A - 1I)v = 0 \Rightarrow \begin{bmatrix} 1 & 0 & -2 \\ 0 & 0 & 0 \\ -2 & 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$

$x - 2z = 0 \Rightarrow x = 2z$
$-2x + z = 0 \Rightarrow z = 2x$

$x = 2z$ y $z = 2x$ implica que $x = z = 0$. Por lo tanto, $y$ es libre.

$v_2 = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$

*   Para $\lambda_3 = 4$:

$(A - 4I)v = 0 \Rightarrow \begin{bmatrix} -2 & 0 & -2 \\ 0 & -3 & 0 \\ -2 & 0 & -2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$

$-2x - 2z = 0 \Rightarrow x = -z$
$-3y = 0 \Rightarrow y = 0$

$v_3 = \begin{bmatrix} 1 \\ 0 \\ -1 \end{bmatrix}$

**4. Construir la matriz $P$ con los vectores propios como columnas.**

$P = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 0 \\ 1 & 0 & -1 \end{bmatrix}$

**5. Construir la matriz diagonal $D$ con los valores propios en la diagonal.**

$D = \begin{bmatrix} 0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 4 \end{bmatrix}$

**6. Verificar que $A = PDP^{-1}$.**

Primero, calculamos $P^{-1}$:

$P^{-1} = \begin{bmatrix} 1/2 & 0 & 1/2 \\ 0 & 1 & 0 \\ 1/2 & 0 & -1/2 \end{bmatrix}$

Ahora, calculamos $PDP^{-1}$:

$PDP^{-1} = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 0 \\ 1 & 0 & -1 \end{bmatrix} \begin{bmatrix} 0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 4 \end{bmatrix} \begin{bmatrix} 1/2 & 0 & 1/2 \\ 0 & 1 & 0 \\ 1/2 & 0 & -1/2 \end{bmatrix}$

$PDP^{-1} = \begin{bmatrix} 0 & 0 & 4 \\ 0 & 1 & 0 \\ 0 & 0 & -4 \end{bmatrix} \begin{bmatrix} 1/2 & 0 & 1/2 \\ 0 & 1 & 0 \\ 1/2 & 0 & -1/2 \end{bmatrix} = \begin{bmatrix} 2 & 0 & -2 \\ 0 & 1 & 0 \\ -2 & 0 & 2 \end{bmatrix} = A$

Como $A = PDP^{-1}$, la transformación lineal $T$ es diagonalizable.

**Respuesta:**

*   La transformación lineal $T$ es diagonalizable.
*   La matriz $P$ es: $P = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 0 \\ 1 & 0 & -1 \end{bmatrix}$
*   La matriz $D$ es: $D = \begin{bmatrix} 0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 4 \end{bmatrix}$
--------------------------------------------------------------------
--------------------------------------------------------------------
