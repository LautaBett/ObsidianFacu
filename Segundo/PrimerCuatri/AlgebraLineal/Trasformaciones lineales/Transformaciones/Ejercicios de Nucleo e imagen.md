¡Entendido! Con la información proporcionada, vamos a resolver los ejercicios 15 al 21.

**Ejercicio 15: En cada uno de los siguientes casos, para la transformación lineal 𝑇 encontrar bases y sistemas de ecuaciones de los subespacios 𝑁𝑢(𝑇) e 𝐼𝑚(𝑇).**

a) 𝑇: ℝ4 → ℝ5 dada por:
𝑇(𝑥, 𝑦, 𝑧,𝑡) = (𝑥 + 𝑦 + 𝑡, 𝑥 + 𝑧, 𝑦 − 𝑧 + 𝑡, 𝑥 + 𝑦, 𝑦 − 𝑧)

1.  **Matriz estándar de T:**
    $T(1,0,0,0) = (1,1,0,1,0)$
    $T(0,1,0,0) = (1,0,1,1,1)$
    $T(0,0,1,0) = (0,1,-1,0,-1)$
    $T(0,0,0,1) = (1,0,1,0,1)$
    $[T] = \begin{pmatrix} 1 & 1 & 0 & 1 \\ 1 & 0 & 1 & 0 \\ 0 & 1 & -1 & 1 \\ 1 & 1 & 0 & 0 \\ 0 & 1 & -1 & 0 \end{pmatrix}$

2.  **Núcleo (Nu(T)):**
    Buscamos $(x, y, z, t)$ tal que $T(x, y, z, t) = (0, 0, 0, 0, 0)$. Esto equivale a resolver el sistema homogéneo $[T] \begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$.
    El sistema es:
    *   $x + y + t = 0$
    *   $x + z = 0$
    *   $y - z + t = 0$
    *   $x + y = 0$
    *   $y - z = 0$
    De la ecuación (4): $x = -y$. De la ecuación (5): $y = z$. Sustituyendo en (1): $-y + y + t = 0 \Rightarrow t = 0$. Sustituyendo en (2): $-y + z = 0 \Rightarrow z = y$.
    Por lo tanto, $Nu(T) = \{( -y, y, y, 0) : y \in \mathbb{R} \} = \{ y(-1, 1, 1, 0) : y \in \mathbb{R} \}$.
    *   **Base de Nu(T):** $\{(-1, 1, 1, 0)\}$
    *   **Sistema de ecuaciones de Nu(T):**
        *   $x + y = 0$
        *   $x + z = 0$
        *   $t = 0$

3.  **Imagen (Im(T)):**
    La imagen es el subespacio generado por las columnas de la matriz $[T]$.
    $Im(T) = \langle (1, 1, 0, 1, 0), (1, 0, 1, 1, 1), (0, 1, -1, 0, -1), (1, 0, 1, 0, 1) \rangle$
    Podemos simplificar esta base eliminando vectores linealmente dependientes. Observamos que la cuarta columna es igual a la segunda.
    $Im(T) = \langle (1, 1, 0, 1, 0), (1, 0, 1, 1, 1), (0, 1, -1, 0, -1) \rangle$
    Estos tres vectores son linealmente independientes (se puede verificar calculando el rango de la matriz formada por ellos).
    *   **Base de Im(T):** $\{(1, 1, 0, 1, 0), (1, 0, 1, 1, 1), (0, 1, -1, 0, -1)\}$
    *   **Sistema de ecuaciones de Im(T):** Para encontrar el sistema de ecuaciones, necesitamos encontrar las condiciones que deben cumplir los vectores $(a, b, c, d, e)$ para estar en la imagen. Esto implica resolver el sistema:
        $\begin{pmatrix} 1 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 1 & -1 \\ 1 & 1 & 0 \\ 0 & 1 & -1 \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \\ \gamma \end{pmatrix} = \begin{pmatrix} a \\ b \\ c \\ d \\ e \end{pmatrix}$
        El sistema es:
        *   $\alpha + \beta = a$
        *   $\alpha + \gamma = b$
        *   $\beta - \gamma = c$
        *   $\alpha + \beta = d$
        *   $\beta - \gamma = e$
        De (1) y (4): $a = d$. De (3) y (5): $c = e$.
        El sistema de ecuaciones de Im(T) es:
        *   $a - d = 0$
        *   $c - e = 0$

b) 𝑇: ℝ4 → ℝ3 dada por:
𝑇(𝑥, 𝑦, 𝑧,𝑡) = (𝑥 + 𝑦, 𝑦 + 𝑧, 𝑧 + 𝑡)

1.  **Matriz estándar de T:**
    $T(1,0,0,0) = (1,0,0)$
    $T(0,1,0,0) = (1,1,0)$
    $T(0,0,1,0) = (0,1,1)$
    $T(0,0,0,1) = (0,0,1)$
    $[T] = \begin{pmatrix} 1 & 1 & 0 & 0 \\ 0 & 1 & 1 & 0 \\ 0 & 0 & 1 & 1 \end{pmatrix}$

2.  **Núcleo (Nu(T)):**
    Buscamos $(x, y, z, t)$ tal que $T(x, y, z, t) = (0, 0, 0)$. Esto equivale a resolver el sistema homogéneo $[T] \begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$.
    El sistema es:
    *   $x + y = 0$
    *   $y + z = 0$
    *   $z + t = 0$
    De la ecuación (1): $y = -x$. De la ecuación (2): $z = -y = x$. De la ecuación (3): $t = -z = -x$.
    Por lo tanto, $Nu(T) = \{(x, -x, x, -x) : x \in \mathbb{R} \} = \{ x(1, -1, 1, -1) : x \in \mathbb{R} \}$.
    *   **Base de Nu(T):** $\{(1, -1, 1, -1)\}$
    *   **Sistema de ecuaciones de Nu(T):**
        *   $x + y = 0$
        *   $y + z = 0$
        *   $z + t = 0$

3.  **Imagen (Im(T)):**
    La imagen es el subespacio generado por las columnas de la matriz $[T]$.
    $Im(T) = \langle (1, 0, 0), (1, 1, 0), (0, 1, 1), (0, 0, 1) \rangle$
    Podemos simplificar esta base eliminando vectores linealmente dependientes. Observamos que $(1,1,0) = (1,0,0) + (0,1,0)$ y $(0,1,1) = (0,1,0) + (0,0,1)$.
    $Im(T) = \langle (1, 0, 0), (0, 1, 0), (0, 0, 1) \rangle$
    Estos tres vectores son linealmente independientes y forman una base de $\mathbb{R}^3$.
    Por lo tanto, $Im(T) = \mathbb{R}^3$.
    *   **Base de Im(T):** $\{(1, 0, 0), (0, 1, 0), (0, 0, 1)\}$
    *   **Sistema de ecuaciones de Im(T):** No hay ecuaciones, ya que la imagen es todo $\mathbb{R}^3$.

c) 𝑇: ℝ3 → ℝ3 dada por:
𝑇(𝑥, 𝑦, 𝑧) = (𝑥 + 𝑦, 𝑥 + 𝑧, 𝑦 − 𝑧 − 𝑥)

1.  **Matriz estándar de T:**
    $T(1,0,0) = (1,1,-1)$
    $T(0,1,0) = (1,0,1)$
    $T(0,0,1) = (0,1,-1)$
    $[T] = \begin{pmatrix} 1 & 1 & 0 \\ 1 & 0 & 1 \\ -1 & 1 & -1 \end{pmatrix}$

2.  **Núcleo (Nu(T)):**
    Buscamos $(x, y, z)$ tal que $T(x, y, z) = (0, 0, 0)$. Esto equivale a resolver el sistema homogéneo $[T] \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$.
    El sistema es:
    *   $x + y = 0$
    *   $x + z = 0$
    *   $-x + y - z = 0$
    De la ecuación (1): $y = -x$. De la ecuación (2): $z = -x$. Sustituyendo en (3): $-x - x - (-x) = 0 \Rightarrow -x = 0 \Rightarrow x = 0$.
    Por lo tanto, $y = 0$ y $z = 0$.
    $Nu(T) = \{(0, 0, 0)\}$.
    *   **Base de Nu(T):** $\emptyset$ (solo el vector cero)
    *   **Sistema de ecuaciones de Nu(T):**
        *   $x = 0$
        *   $y = 0$
        *   $z = 0$

3.  **Imagen (Im(T)):**
    La imagen es el subespacio generado por las columnas de la matriz $[T]$.
    $Im(T) = \langle (1, 1, -1), (1, 0, 1), (0, 1, -1) \rangle$
    Estos tres vectores son linealmente independientes (se puede verificar calculando el determinante de la matriz formada por ellos).
    $\det \begin{pmatrix} 1 & 1 & 0 \\ 1 & 0 & 1 \\ -1 & 1 & -1 \end{pmatrix} = 1(0-1) - 1(-1+1) + 0 = -1 \neq 0$
    Por lo tanto, $Im(T) = \mathbb{R}^3$.
    *   **Base de Im(T):** $\{(1, 1, -1), (1, 0, 1), (0, 1, -1)\}$
    *   **Sistema de ecuaciones de Im(T):** No hay ecuaciones, ya que la imagen es todo $\mathbb{R}^3$.

d) 𝑇: ℝ4 → ℝ4 dada por:
𝑇(𝑥, 𝑦, 𝑧,𝑡) = (𝑥 − 𝑦, 𝑦 − 𝑧, 𝑧 − 𝑡,𝑡 − 𝑥)

1.  **Matriz estándar de T:**
    $T(1,0,0,0) = (1,0,0,-1)$
    $T(0,1,0,0) = (-1,1,0,0)$
    $T(0,0,1,0) = (0,-1,1,0)$
    $T(0,0,0,1) = (0,0,-1,1)$
    $[T] = \begin{pmatrix} 1 & -1 & 0 & 0 \\ 0 & 1 & -1 & 0 \\ 0 & 0 & 1 & -1 \\ -1 & 0 & 0 & 1 \end{pmatrix}$

2.  **Núcleo (Nu(T)):**
    Buscamos $(x, y, z, t)$ tal que $T(x, y, z, t) = (0, 0, 0, 0)$. Esto equivale a resolver el sistema homogéneo $[T] \begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$.
    El sistema es:
    *   $x - y = 0$
    *   $y - z = 0$
    *   $z - t = 0$
    *   $-x + t = 0$
    De la ecuación (1): $x = y$. De la ecuación (2): $y = z$. De la ecuación (3): $z = t$. De la ecuación (4): $t = x$.
    Por lo tanto, $Nu(T) = \{(x, x, x, x) : x \in \mathbb{R} \} = \{ x(1, 1, 1, 1) : x \in \mathbb{R} \}$.
    *   **Base de Nu(T):** $\{(1, 1, 1, 1)\}$
    *   **Sistema de ecuaciones de Nu(T):**
        *   $x - y = 0$
        *   $y - z = 0$
        *   $z - t = 0$

3.  **Imagen (Im(T)):**
    La imagen es el subespacio generado por las columnas de la matriz $[T]$.
    $Im(T) = \langle (1, 0, 0, -1), (-1, 1, 0, 0), (0, -1, 1, 0), (0, 0, -1, 1) \rangle$
    Estos cuatro vectores son linealmente dependientes. De hecho, $(1, 0, 0, -1) + (-1, 1, 0, 0) + (0, -1, 1, 0) + (0, 0, -1, 1) = (0,0,0,0)$.
    Podemos eliminar uno de ellos, por ejemplo, $(1, 0, 0, -1)$.
    $Im(T) = \langle (-1, 1, 0, 0), (0, -1, 1, 0), (0, 0, -1, 1) \rangle$
    Estos tres vectores son linealmente independientes.
    *   **Base de Im(T):** $\{(-1, 1, 0, 0), (0, -1, 1, 0), (0, 0, -1, 1)\}$
    *   **Sistema de ecuaciones de Im(T):** Para encontrar el sistema de ecuaciones, necesitamos encontrar las condiciones que deben cumplir los vectores $(a, b, c, d)$ para estar en la imagen. Esto implica resolver el sistema:
        $\begin{pmatrix} -1 & 0 & 0 \\ 1 & -1 & 0 \\ 0 & 1 & -1 \\ 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \\ \gamma \end{pmatrix} = \begin{pmatrix} a \\ b \\ c \\ d \end{pmatrix}$
        El sistema es:
        *   $-\alpha = a$
        *   $\alpha - \beta = b$
        *   $\beta - \gamma = c$
        *   $\gamma = d$
        De (1): $\alpha = -a$. De (4): $\gamma = d$. Sustituyendo en (2): $-a - \beta = b \Rightarrow \beta = -a - b$. Sustituyendo en (3): $-a - b - d = c \Rightarrow a + b + c + d = 0$.
        El sistema de ecuaciones de Im(T) es:
        *   $a + b + c + d = 0$

**Ejercicio 16: Definir una transformación lineal 𝑇: ℝ4 → ℝ3 de modo que:**
𝑁𝑢 (𝑇) = {(𝑥, 𝑦, 𝑧,𝑡) ∈ ℝ4
: 𝑥 + 𝑦 = 0, 𝑥 − 𝑡 = 0, 𝑦 + 𝑧 + 𝑡 = 0}
Obtener luego una base y la dimensión del núcleo.

1.  **Encontrar una base para Nu(T):**
    El núcleo está definido por el sistema de ecuaciones:
    *   $x + y = 0$
    *   $x - t = 0$
    *   $y + z + t = 0$
    De (1): $y = -x$. De (2): $t = x$. Sustituyendo en (3): $-x + z + x = 0 \Rightarrow z = 0$.
    Por lo tanto, $Nu(T) = \{(x, -x, 0, x) : x \in \mathbb{R} \} = \{ x(1, -1, 0, 1) : x \in \mathbb{R} \}$.
    *   **Base de Nu(T):** $\{(1, -1, 0, 1)\}$
    *   **Dimensión de Nu(T):** 1

2.  **Definir la transformación lineal T:**
    Necesitamos encontrar una TL $T: \mathbb{R}^4 \rightarrow \mathbb{R}^3$ tal que $Nu(T) = \langle (1, -1, 0, 1) \rangle$.
    Completamos una base de $\mathbb{R}^4$ con vectores que no estén en el núcleo. Por ejemplo:
    $v_1 = (1, -1, 0, 1)$ (ya en el núcleo)
    $v_2 = (1, 0, 0, 0)$
    $v_3 = (0, 1, 0, 0)$
    $v_4 = (0, 0, 1, 0)$
    Definimos $T$ de la siguiente manera:
    *   $T(1, -1, 0, 1) = (0, 0, 0)$ (para que este vector esté en el núcleo)
    *   $T(1, 0, 0, 0) = (1, 0, 0)$
    *   $T(0, 1, 0, 0) = (0, 1, 0)$
    *   $T(0, 0, 1, 0) = (0, 0, 1)$
    Ahora, expresamos un vector genérico $(x, y, z, t)$ como combinación lineal de estos vectores:
    $(x, y, z, t) = \alpha_1 (1, -1, 0, 1) + \alpha_2 (1, 0, 0, 0) + \alpha_3 (0, 1, 0, 0) + \alpha_4 (0, 0, 1, 0)$
    $(x, y, z, t) = (\alpha_1 + \alpha_2, -\alpha_1 + \alpha_3, \alpha_4, \alpha_1)$
    Entonces:
    *   $x = \alpha_1 + \alpha_2$
    *   $y = -\alpha_1 + \alpha_3$
    *   $z = \alpha_4$
    *   $t = \alpha_1$
    De aquí: $\alpha_1 = t$, $\alpha_2 = x - t$, $\alpha_3 = y + t$, $\alpha_4 = z$.
    Aplicamos $T$:
    $T(x, y, z, t) = \alpha_1 T(1, -1, 0, 1) + \alpha_2 T(1, 0, 0, 0) + \alpha_3 T(0, 1, 0, 0) + \alpha_4 T(0, 0, 1, 0)$
    $T(x, y, z, t) = t(0, 0, 0) + (x - t)(1, 0, 0) + (y + t)(0, 1, 0) + z(0, 0, 1)$
    $T(x, y, z, t) = (x - t, y + t, z)$

**Ejercicio 17: Dada la transformación lineal 𝑇: ℝ3 → ℝ3 dada por su matriz estándar:**
[𝑇]𝐶 = [
1 1 −1
3 −3 −3
−2 4 2
]
Determinar 𝑁𝑢 (𝑇),𝐼𝑚(𝑇), 𝑁𝑢 (𝑇)
⊥ 𝑒 𝐼𝑚 (𝑇)
⊥ y sus respectivas dimensiones.

1.  **Núcleo (Nu(T)):**
    Buscamos $(x, y, z)$ tal que $T(x, y, z) = (0, 0, 0)$. Esto equivale a resolver el sistema homogéneo $[T] \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$.
    El sistema es:
    *   $x + y - z = 0$
    *   $3x - 3y - 3z = 0 \Rightarrow x - y - z = 0$
    *   $-2x + 4y + 2z = 0 \Rightarrow -x + 2y + z = 0$
    Sumando (1) y (3): $3y = 0 \Rightarrow y = 0$. Sustituyendo en (1): $x - z = 0 \Rightarrow x = z$.
    Por lo tanto, $Nu(T) = \{(x, 0, x) : x \in \mathbb{R} \} = \{ x(1, 0, 1) : x \in \mathbb{R} \}$.
    *   **Base de Nu(T):** $\{(1, 0, 1)\}$
    *   **Dimensión de Nu(T):** 1

2.  **Imagen (Im(T)):**
    La imagen es el subespacio generado por las columnas de la matriz $[T]$.
    $Im(T) = \langle (1, 3, -2), (1, -3, 4), (-1, -3, 2) \rangle$
    Observamos que la tercera columna es igual a la primera columna multiplicada por -1.
    $Im(T) = \langle (1, 3, -2), (1, -3, 4) \rangle$
    Estos dos vectores son linealmente independientes.
    *   **Base de Im(T):** $\{(1, 3, -2), (1, -3, 4)\}$
    *   **Dimensión de Im(T):** 2

3.  **Nu(T)⊥:**
    Buscamos $(a, b, c)$ tal que $(a, b, c) \cdot (1, 0, 1) = 0$.
    $a + c = 0 \Rightarrow c = -a$.
    $Nu(T)^\perp = \{(a, b, -a) : a, b \in \mathbb{R} \} = \{ a(1, 0, -1) + b(0, 1, 0) : a, b \in \mathbb{R} \}$.
    *   **Base de Nu(T)⊥:** $\{(1, 0, -1), (0, 1, 0)\}$
    *   **Dimensión de Nu(T)⊥:** 2

4.  **Im(T)⊥:**
    Buscamos $(a, b, c)$ tal que $(a, b, c) \cdot (1, 3, -2) = 0$ y $(a, b, c) \cdot (1, -3, 4) = 0$.
    *   $a + 3b - 2c = 0$
    *   $a - 3b + 4c = 0$
    Sumando las ecuaciones: $2a + 2c = 0 \Rightarrow a = -c$. Sustituyendo en la primera: $-c + 3b - 2c = 0 \Rightarrow 3b = 3c \Rightarrow b = c$.
    $Im(T)^\perp = \{(-c, c, c) : c \in \mathbb{R} \} = \{ c(-1, 1, 1) : c \in \mathbb{R} \}$.
    *   **Base de Im(T)⊥:** $\{(-1, 1, 1)\}$
    *   **Dimensión de Im(T)⊥:** 1

**Ejercicio 18: Dada la transformación lineal 𝑇: ℝ3 → ℝ3 dada por su matriz estándar:**
[𝑇]𝐶 = [
−1 2 1
2 1 1
−5 0 −1
]
a) Determinar 𝑁𝑢 (𝑇),𝐼𝑚(𝑇), 𝑁𝑢 (𝑇)
⊥ 𝑒 𝐼𝑚 (𝑇)
⊥ y sus respectivas dimensiones.

1.  **Núcleo (Nu(T)):**
    Buscamos $(x, y, z)$ tal que $T(x, y, z) = (0, 0, 0)$. Esto equivale a resolver el sistema homogéneo $[T] \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$.
    El sistema es:
    *   $-x + 2y + z = 0$
    *   $2x + y + z = 0$
    *   $-5x - z = 0$
    De (3): $z = -5x$. Sustituyendo en (1): $-x + 2y - 5x = 0 \Rightarrow 2y = 6x \Rightarrow y = 3x$.
    Sustituyendo en (2): $2x + 3x - 5x = 0 \Rightarrow 0 = 0$.
    Por lo tanto, $Nu(T) = \{(x, 3x, -5x) : x \in \mathbb{R} \} = \{ x(1, 3, -5) : x \in \mathbb{R} \}$.
    *   **Base de Nu(T):** $\{(1, 3, -5)\}$
    *   **Dimensión de Nu(T):** 1

2.  **Imagen (Im(T)):**
    La imagen es el subespacio generado por las columnas de la matriz $[T]$.
    $Im(T) = \langle (-1, 2, -5), (2, 1, 0), (1, 1, -1) \rangle$
    Estos tres vectores son linealmente dependientes.
    Podemos verificar que $(1,1,-1) = \alpha(-1,2,-5) + \beta(2,1,0)$.
    $1 = -\alpha + 2\beta$
    $1 = 2\alpha + \beta$
    $-1 = -5\alpha$
    $\alpha = 1/5$.
    $1 = 2(1/5) + \beta \Rightarrow \beta = 3/5$.
    $Im(T) = \langle (-1, 2, -5), (2, 1, 0) \rangle$
    Estos dos vectores son linealmente independientes.
    *   **Base de Im(T):** $\{(-1, 2, -5), (2, 1, 0)\}$
    *   **Dimensión de Im(T):** 2

3.  **Nu(T)⊥:**
    Buscamos $(a, b, c)$ tal que $(a, b, c) \cdot (1, 3, -5) = 0$.
    $a + 3b - 5c = 0 \Rightarrow a = -3b + 5c$.
    $Nu(T)^\perp = \{(-3b + 5c, b, c) : b, c \in \mathbb{R} \} = \{ b(-3, 1, 0) + c(5, 0, 1) : b, c \in \mathbb{R} \}$.
    *   **Base de Nu(T)⊥:** $\{(-3, 1, 0), (5, 0, 1)\}$
    *   **Dimensión de Nu(T)⊥:** 2

4.  **Im(T)⊥:**
    Buscamos $(a, b, c)$ tal que $(a, b, c) \cdot (-1, 2, -5) = 0$ y $(a, b, c) \cdot (2, 1, 0) = 0$.
    *   $-a + 2b - 5c = 0$
    *   $2a + b = 0 \Rightarrow b = -2a$
    Sustituyendo en la primera: $-a + 2(-2a) - 5c = 0 \Rightarrow -5a - 5c = 0 \Rightarrow a = -c$.
    $Im(T)^\perp = \{(-c, 2c, c) : c \in \mathbb{R} \} = \{ c(-1, 2, 1) : c \in \mathbb{R} \}$.
    *   **Base de Im(T)⊥:** $\{(-1, 2, 1)\}$
    *   **Dimensión de Im(T)⊥:** 1

b) Determinar, cuando sea posible 𝑇
−1
(1, −2,3) y 𝑇
−1
(1,2,3)

1.  **𝑇−1(1, −2,3):**
    Resolvemos $T(x,y,z) = (1,-2,3)$.
    *   $-x + 2y + z = 1$
    *   $2x + y + z = -2$
    *   $-5x - z = 3$
    De (3): $z = -5x - 3$. Sustituyendo en (1): $-x + 2y - 5x - 3 = 1 \Rightarrow 2y = 6x + 4 \Rightarrow y = 3x + 2$.
    Sustituyendo en (2): $2x + (3x + 2) + (-5x - 3) = -2 \Rightarrow 0 = -1$.
    El sistema es incompatible. No existe $T^{-1}(1,-2,3)$.

2.  **𝑇−1(1, 2,3):**
    Resolvemos $T(x,y,z) = (1,2,3)$.
    *   $-x + 2y + z = 1$
    *   $2x + y + z = 2$
    *   $-5x - z = 3$
    De (3): $z = -5x - 3$. Sustituyendo en (1): $-x + 2y - 5x - 3 = 1 \Rightarrow 2y = 6x + 4 \Rightarrow y = 3x + 2$.
    Sustituyendo en (2): $2x + (3x + 2) + (-5x - 3) = 2 \Rightarrow 0 = 3$.
    El sistema es incompatible. No existe $T^{-1}(1,2,3)$.

**Ejercicio 19: Dada la transformación lineal 𝑇: ℝ4 → ℝ4 dada por:**
𝑇(𝑥, 𝑦, 𝑧,𝑡) = (𝑥 − 𝑧 − 𝑡, 𝑥 + 𝑦 − 𝑧 − 𝑡, 0, −𝑥 + 2𝑦 + 𝑧 + 𝑡)
Hallar generadores y sistemas de ecuaciones para los subespacios
𝑁𝑢 (𝑇),𝐼𝑚(𝑇), 𝑁𝑢 (𝑇)
⊥ 𝑒 𝐼𝑚 (𝑇)
⊥.

1.  **Matriz estándar de T:**
    $T(1,0,0,0) = (1,1,0,-1)$
    $T(0,1,0,0) = (0,1,0,2)$
    $T(0,0,1,0) = (-1,-1,0,1)$
    $T(0,0,0,1) = (-1,-1,0,1)$
    $[T] = \begin{pmatrix} 1 & 0 & -1 & -1 \\ 1 & 1 & -1 & -1 \\ 0 & 0 & 0 & 0 \\ -1 & 2 & 1 & 1 \end{pmatrix}$

2.  **Núcleo (Nu(T)):**
    Buscamos $(x, y, z, t)$ tal que $T(x, y, z, t) = (0, 0, 0, 0)$. Esto equivale a resolver el sistema homogéneo $[T] \begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$.
    El sistema es:
    *   $x - z - t = 0$
    *   $x + y - z - t = 0$
    *   $0 = 0$
    *   $-x + 2y + z + t = 0$
    De (1): $x = z + t$. Sustituyendo en (2): $z + t + y - z - t = 0 \Rightarrow y = 0$. Sustituyendo en (4): $-(z+t) + 2(0) + z + t = 0 \Rightarrow 0 = 0$.
    Por lo tanto, $Nu(T) = \{(z+t, 0, z, t) : z, t \in \mathbb{R} \} = \{ z(1, 0, 1, 0) + t(1, 0, 0, 1) : z, t \in \mathbb{R} \}$.
    *   **Base de Nu(T):** $\{(1, 0, 1, 0), (1, 0, 0, 1)\}$
    *   **Sistema de ecuaciones de Nu(T):**
        *   $y = 0$
        *   $x - z - t = 0$

3.  ¡Excelente! Continuemos con los ejercicios 19, 20 y 21.

**Ejercicio 19 (continuación):**

2.  **Imagen (Im(T)):** (continuación)
    La imagen es el subespacio generado por las columnas de la matriz $[T]$.
    $Im(T) = \langle (1, 1, 0, -1), (0, 1, 0, 2), (-1, -1, 0, 1), (-1, -1, 0, 1) \rangle$
    Observamos que la tercera y cuarta columnas son múltiplos de la primera.
    $Im(T) = \langle (1, 1, 0, -1), (0, 1, 0, 2) \rangle$
    Estos dos vectores son linealmente independientes.
    *   **Base de Im(T):** $\{(1, 1, 0, -1), (0, 1, 0, 2)\}$
    *   **Sistema de ecuaciones de Im(T):** Para encontrar el sistema de ecuaciones, necesitamos encontrar las condiciones que deben cumplir los vectores $(a, b, c, d)$ para estar en la imagen. Esto implica resolver el sistema:
        $\begin{pmatrix} 1 & 0 \\ 1 & 1 \\ 0 & 0 \\ -1 & 2 \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \end{pmatrix} = \begin{pmatrix} a \\ b \\ c \\ d \end{pmatrix}$
        El sistema es:
        *   $\alpha = a$
        *   $\alpha + \beta = b$
        *   $0 = c$
        *   $-\alpha + 2\beta = d$
        De (1): $\alpha = a$. De (3): $c = 0$. Sustituyendo en (2): $a + \beta = b \Rightarrow \beta = b - a$. Sustituyendo en (4): $-a + 2(b-a) = d \Rightarrow -3a + 2b = d \Rightarrow 3a - 2b + d = 0$.
        El sistema de ecuaciones de Im(T) es:
        *   $c = 0$
        *   $3a - 2b + d = 0$

3.  **Nu(T)⊥:**
    Buscamos $(a, b, c, d)$ tal que $(a, b, c, d) \cdot (1, 0, 1, 0) = 0$ y $(a, b, c, d) \cdot (1, 0, 0, 1) = 0$.
    *   $a + c = 0$
    *   $a + d = 0$
    De (1): $c = -a$. De (2): $d = -a$.
    $Nu(T)^\perp = \{(a, b, -a, -a) : a, b \in \mathbb{R} \} = \{ a(1, 0, -1, -1) + b(0, 1, 0, 0) : a, b \in \mathbb{R} \}$.
    *   **Base de Nu(T)⊥:** $\{(1, 0, -1, -1), (0, 1, 0, 0)\}$
    *   **Sistema de ecuaciones de Nu(T)⊥:**
        *   $a + c = 0$
        *   $a + d = 0$

4.  **Im(T)⊥:**
    Buscamos $(a, b, c, d)$ tal que $(a, b, c, d) \cdot (1, 1, 0, -1) = 0$ y $(a, b, c, d) \cdot (0, 1, 0, 2) = 0$.
    *   $a + b - d = 0$
    *   $b + 2d = 0 \Rightarrow b = -2d$
    Sustituyendo en la primera: $a - 2d - d = 0 \Rightarrow a = 3d$.
    $Im(T)^\perp = \{(3d, -2d, c, d) : c, d \in \mathbb{R} \} = \{ d(3, -2, 0, 1) + c(0, 0, 1, 0) : c, d \in \mathbb{R} \}$.
    *   **Base de Im(T)⊥:** $\{(3, -2, 0, 1), (0, 0, 1, 0)\}$
    *   **Sistema de ecuaciones de Im(T)⊥:**
        *   $a - 3d = 0$
        *   $b + 2d = 0$

**Ejercicio 20: Hallar una transformación lineal 𝑡: ℝ𝑛 → ℝ𝑛 tal que:**

a) 𝑡(𝐿) ⊂ 𝑆 siendo:
𝐿 = 〈(2,1,2)〉 𝑦 𝑆 = {(𝑥, 𝑦, 𝑧) ∈ ℝ3
: 𝑥 − 𝑦 = 0}

1.  **Entendiendo el problema:** Queremos una TL $t: \mathbb{R}^3 \rightarrow \mathbb{R}^3$ tal que la imagen de cualquier vector en la recta $L$ esté contenida en el plano $S$.
2.  **Estrategia:** Definir $t$ en una base de $\mathbb{R}^3$. Asegurarnos de que $t(2,1,2)$ esté en $S$.
3.  **Resolución:**
    *   Sea $v_1 = (2, 1, 2)$. Para que $t(L) \subset S$, necesitamos que $t(v_1) \in S$. Esto significa que la primera componente de $t(v_1)$ debe ser igual a la segunda componente. Por ejemplo, $t(v_1) = (1, 1, 0)$.
    *   Completamos una base de $\mathbb{R}^3$: $v_2 = (1, 0, 0)$ y $v_3 = (0, 1, 0)$.
    *   Definimos $t(v_2)$ y $t(v_3)$ como queramos (por ejemplo, $t(1,0,0) = (0,0,0)$ y $t(0,1,0) = (0,0,0)$).
    *   Entonces, $t(x, y, z) = \alpha_1 t(2,1,2) + \alpha_2 t(1,0,0) + \alpha_3 t(0,1,0) = \alpha_1 (1,1,0)$.
    *   Expresamos $(x,y,z)$ como combinación lineal de $v_1, v_2, v_3$:
        $(x,y,z) = \alpha_1 (2,1,2) + \alpha_2 (1,0,0) + \alpha_3 (0,1,0)$
        $x = 2\alpha_1 + \alpha_2$
        $y = \alpha_1 + \alpha_3$
        $z = 2\alpha_1$
        De (3): $\alpha_1 = z/2$. De (1): $\alpha_2 = x - 2\alpha_1 = x - z$. De (2): $\alpha_3 = y - \alpha_1 = y - z/2$.
        $t(x,y,z) = (z/2)(1,1,0) + (x-z)(0,0,0) + (y-z/2)(0,0,0) = (z/2, z/2, 0)$.
        $t(x,y,z) = (z/2, z/2, 0)$

b) 𝑡(𝑆) = 𝑇 𝑦 𝑡(𝑇) = 𝑆 siendo:
𝑆 = 〈(1,0,1), (0,1,1)〉 𝑦 𝑇 = {(𝑥, 𝑦, 𝑧) ∈ ℝ3
: 𝑥 − 𝑦 + 𝑧 = 0}

1.  **Entendiendo el problema:** Queremos una TL $t: \mathbb{R}^3 \rightarrow \mathbb{R}^3$ que intercambie los subespacios $S$ y $T$.
2.  **Estrategia:** Definir $t$ en una base de $\mathbb{R}^3$. Asegurarnos de que $t$ mapee una base de $S$ a una base de $T$ y viceversa.
3.  **Resolución:**
    *   Base de $S$: $\{(1,0,1), (0,1,1)\}$
    *   Sistema de ecuaciones de $T$: $x - y + z = 0 \Rightarrow x = y - z$. Entonces, $T = \{(y-z, y, z) : y, z \in \mathbb{R} \} = \{ y(1,1,0) + z(-1,0,1) : y, z \in \mathbb{R} \}$.
    *   Base de $T$: $\{(1,1,0), (-1,0,1)\}$
    *   Definimos:
        *   $t(1,0,1) = (1,1,0)$
        *   $t(0,1,1) = (-1,0,1)$
        *   Completamos una base de $\mathbb{R}^3$: $v_3 = (0,0,1)$. Definimos $t(0,0,1) = (0,0,0)$.
    *   Expresamos $(x,y,z)$ como combinación lineal de $(1,0,1), (0,1,1), (0,0,1)$:
        $(x,y,z) = \alpha_1 (1,0,1) + \alpha_2 (0,1,1) + \alpha_3 (0,0,1)$
        $x = \alpha_1$
        $y = \alpha_2$
        $z = \alpha_1 + \alpha_2 + \alpha_3$
        $\alpha_1 = x$, $\alpha_2 = y$, $\alpha_3 = z - x - y$.
        $t(x,y,z) = x(1,1,0) + y(-1,0,1) + (z-x-y)(0,0,0) = (x-y, x, y)$.
        $t(x,y,z) = (x-y, x, y)$

c) Im(𝑡) = 〈(1,0,1)〉 𝑦 𝑁𝑢(𝑡) = 〈(2,1,2), (1,0,1)〉

1.  **Entendiendo el problema:** Queremos una TL $t: \mathbb{R}^3 \rightarrow \mathbb{R}^3$ con una imagen generada por un solo vector y un núcleo generado por dos vectores.
2.  **Estrategia:** Definir $t$ en una base de $\mathbb{R}^3$. Asegurarnos de que los vectores del núcleo se mapeen a cero y que el otro vector se mapee al generador de la imagen.
3.  **Resolución:**
    *   Sea $v_1 = (2, 1, 2)$ y $v_2 = (1, 0, 1)$. Estos vectores generan el núcleo, por lo tanto, $t(2,1,2) = (0,0,0)$ y $t(1,0,1) = (0,0,0)$.
    *   Completamos una base de $\mathbb{R}^3$: $v_3 = (0, 1, 0)$.
    *   Definimos $t(0,1,0) = (1,0,1)$ (el generador de la imagen).
    *   Expresamos $(x,y,z)$ como combinación lineal de $(2,1,2), (1,0,1), (0,1,0)$:
        $(x,y,z) = \alpha_1 (2,1,2) + \alpha_2 (1,0,1) + \alpha_3 (0,1,0)$
        $x = 2\alpha_1 + \alpha_2$
        $y = \alpha_1 + \alpha_3$
        $z = 2\alpha_1 + \alpha_2$
        De (1) y (3): $x = z \Rightarrow x - z = 0$.
        $\alpha_1 = 0$. $\alpha_2 = x$. $\alpha_3 = y$.
        $t(x,y,z) = x(0,0,0) + y(1,0,1) + 0(0,0,0) = (y,0,y)$.
        $t(x,y,z) = (y,0,y)$

d) 𝑁𝑢(𝑡) = {
𝑥 + 𝑦 − 𝑧 = 0
2𝑥 + 𝑧 = 0
𝑒 𝐼𝑚(𝑡) = 〈(2, −1,0), (0,1, −2)〉

1.  **Entendiendo el problema:** Queremos una TL $t: \mathbb{R}^3 \rightarrow \mathbb{R}^3$ con un núcleo definido por dos ecuaciones y una imagen generada por dos vectores.
2.  **Estrategia:** Encontrar una base para el núcleo y completar una base para $\mathbb{R}^3$. Definir la TL de manera que los vectores de la base del núcleo se mapeen a cero y los otros vectores se mapeen a los generadores de la imagen.
3.  **Resolución:**
    *   Encontramos una base para el núcleo:
        *   $x + y - z = 0$
        *   $2x + z = 0 \Rightarrow z = -2x$
        Sustituyendo en la primera: $x + y + 2x = 0 \Rightarrow y = -3x$.
        $Nu(t) = \{(x, -3x, -2x) : x \in \mathbb{R} \} = \{ x(1, -3, -2) : x \in \mathbb{R} \}$.
        Base de Nu(t): $\{(1, -3, -2)\}$.
    *   Completamos una base de $\mathbb{R}^3$: $v_1 = (1, -3, -2)$, $v_2 = (1, 0, 0)$, $v_3 = (0, 1, 0)$.
    *   Definimos:
        *   $t(1, -3, -2) = (0, 0, 0)$
        *   $t(1, 0, 0) = (2, -1, 0)$
        *   $t(0, 1, 0) = (0, 1, -2)$
    *   Expresamos $(x,y,z)$ como combinación lineal de $(1,-3,-2), (1,0,0), (0,1,0)$:
        $(x,y,z) = \alpha_1 (1,-3,-2) + \alpha_2 (1,0,0) + \alpha_3 (0,1,0)$
        $x = \alpha_1 + \alpha_2$
        $y = -3\alpha_1 + \alpha_3$
        $z = -2\alpha_1$
        $\alpha_1 = -z/2$. $\alpha_2 = x - \alpha_1 = x + z/2$. $\alpha_3 = y + 3\alpha_1 = y - 3z/2$.
        $t(x,y,z) = (-z/2)(0,0,0) + (x+z/2)(2,-1,0) + (y-3z/2)(0,1,-2) = (2x+z, -x-z/2+y-3z/2, -2y+3z)$.
        $t(x,y,z) = (2x+z, -x+y-2z, -2y+3z)$

**Ejercicio 21: Dada 𝑓: ℝ3 → ℝ3 definida como:**
𝑓(𝑥, 𝑦, 𝑧) = (𝑥 + 𝑦 + 𝑧, 𝑥 − 𝑦 + 𝑧, 𝑥 + 𝑦 − 𝑧)
¿ 𝑓 es biyectiva? En caso afirmativo calcular 𝑓
−1
.

1.  **Matriz estándar de f:**
    $f(1,0,0) = (1,1,1)$
    $f(0,1,0) = (1,-1,1)$
    $f(0,0,1) = (1,1,-1)$
    $[f] = \begin{pmatrix} 1 & 1 & 1 \\ 1 & -1 & 1 \\ 1 & 1 & -1 \end{pmatrix}$

2.  **Verificar si f es biyectiva:**
    Para que $f$ sea biyectiva, la matriz $[f]$ debe ser invertible (es decir, su determinante debe ser diferente de cero).
    $\det \begin{pmatrix} 1 & 1 & 1 \\ 1 & -1 & 1 \\ 1 & 1 & -1 \end{pmatrix} = 1(1-1) - 1(-1-1) + 1(1+1) = 0 + 2 + 2 = 4 \neq 0$
    Por lo tanto, $f$ es biyectiva.

3.  **Calcular 𝑓−1:**
    Para calcular la inversa, necesitamos encontrar la matriz inversa de $[f]$.
    $[f]^{-1} = \frac{1}{\det(f)} adj(f)$
    $adj(f) = \begin{pmatrix} 0 & 2 & 2 \\ 2 & -2 & 0 \\ 2 & 0 & -2 \end{pmatrix}$
    $[f]^{-1} = \frac{1}{4} \begin{pmatrix} 0 & 2 & 2 \\ 2 & -2 & 0 \\ 2 & 0 & -2 \end{pmatrix} = \begin{pmatrix} 0 & 1/2 & 1/2 \\ 1/2 & -1/2 & 0 \\ 1/2 & 0 & -1/2 \end{pmatrix}$
    Entonces, $f^{-1}(x,y,z) = \begin{pmatrix} 0 & 1/2 & 1/2 \\ 1/2 & -1/2 & 0 \\ 1/2 & 0 & -1/2 \end{pmatrix} \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} (y+z)/2 \\ (x-y)/2 \\ (x-z)/2 \end{pmatrix}$.
    $f^{-1}(x,y,z) = (\frac{y+z}{2}, \frac{x-y}{2}, \frac{x-z}{2})$

¡Uf! Eso fue un montón de trabajo. Espero que estas soluciones detalladas te sean de gran ayuda. Si tienes alguna otra pregunta, no dudes en consultarme.