# Rectas, Planos y Rango

## Rectas en R² y R³

### Conceptos Fundamentales

*   Una recta queda definida por un **punto de paso** $P$ por el que pasa y un **vector director** $\vec{v}$ que indica su dirección.
*   El vector director puede ser "estirado" o "contraído" mediante un escalar $\lambda \in \mathbb{R}$ ($\lambda \vec{v}$) para generar todos los puntos de una recta que pasa por el origen con esa dirección.
*   Al sumar el punto de paso $P$, se desplaza la recta para que pase por $P$.

### Ecuaciones de la Recta

1.  **Ecuación Vectorial:** Representa cualquier punto $X$ de la recta como la suma del punto de paso y un múltiplo escalar del vector director.
    *   En R²: $X = (x, y) = \lambda \vec{v} + P = \lambda (v_1, v_2) + (p_1, p_2)$
    *   En R³: $X = (x, y, z) = \lambda \vec{v} + P = \lambda (v_1, v_2, v_3) + (p_1, p_2, p_3)$

2.  **Ecuaciones Paramétricas:** Se obtienen al separar la ecuación vectorial en sus componentes. El escalar $\lambda$ actúa como parámetro.
    *   En R²:
        ```
        { x = λv₁ + p₁
        { y = λv₂ + p₂
        ```
    *   En R³:
        ```
        { x = λv₁ + p₁
        { y = λv₂ + p₂
        { z = λv₃ + p₃
        ```
    *   Estas ecuaciones son útiles para verificar si un punto pertenece a la recta (debe existir un único valor de $\lambda$ que satisfaga todas las ecuaciones simultáneamente).

### Casos Particulares

*   **Recta Paralela:** Dos rectas son paralelas si sus vectores directores son paralelos (uno es múltiplo escalar del otro). Para encontrar una recta $L$ paralela a otra recta $r$ y que pase por un punto $Q$, se usa el mismo vector director de $r$ y el punto $Q$.
*   **Recta que une dos puntos P y Q:**
    *   Se toma como vector director $\vec{v} = \vec{PQ} = Q - P$.
    *   Se usa cualquiera de los puntos ($P$ o $Q$) como punto de paso.
    *   Ejemplo en R²: $(x, y) = \lambda (Q - P) + P$.

## Planos en R³

### Conceptos Fundamentales

*   Un plano en R³ se genera mediante **dos vectores directores** $\vec{u}$ y $\vec{v}$ que **no sean paralelos** (linealmente independientes).
*   Cualquier combinación lineal $\lambda \vec{u} + \beta \vec{v}$ (con $\lambda, \beta \in \mathbb{R}$) genera un punto en el plano que pasa por el origen y es generado por $\vec{u}$ y $\vec{v}$.
*   Al igual que con las rectas, se puede añadir un **punto de paso** $P$ para desplazar el plano.

### Ecuaciones del Plano

1.  **Ecuación Vectorial:** Representa cualquier punto $X$ del plano.
    *   $X = (x, y, z) = \lambda \vec{u} + \beta \vec{v} + P$
    *   Donde $\vec{u} = (u_1, u_2, u_3)$, $\vec{v} = (v_1, v_2, v_3)$ son los vectores directores y $P = (p_1, p_2, p_3)$ es el punto de paso.

2.  **Ecuaciones Paramétricas:** Se obtienen separando la ecuación vectorial en componentes. Ahora hay dos parámetros, $\lambda$ y $\beta$.
    ```
    { x = λu₁ + βv₁ + p₁
    { y = λu₂ + βv₂ + p₂
    { z = λu₃ + βv₃ + p₃
    ```

3.  **Ecuación Implícita o General:** Tiene la forma $ax + by + cz + d = 0$.
    *   Se basa en el concepto de **vector normal** $\vec{n} = (a, b, c)$, que es un vector ortogonal (perpendicular) a *todos* los vectores contenidos en el plano (y por tanto, ortogonal a los vectores directores $\vec{u}$ y $\vec{v}$).
    *   Si $P = (p_1, p_2, p_3)$ es un punto del plano y $X = (x, y, z)$ es un punto genérico del plano, el vector $\vec{PX} = X - P$ está contenido en el plano.
    *   Como $\vec{n}$ es ortogonal a $\vec{PX}$, su producto escalar es cero: $\vec{n} \cdot (X - P) = 0$.
    *   $(a, b, c) \cdot (x - p_1, y - p_2, z - p_3) = 0$
    *   $a(x - p_1) + b(y - p_2) + c(z - p_3) = 0$
    *   $ax + by + cz + \underbrace{(-ap_1 - bp_2 - cp_3)}_{d} = 0$

### Casos Particulares

*   **Plano que pasa por tres puntos no colineales A, B, C:**
    *   **Forma Vectorial/Paramétrica:**
        1.  Elegir un punto base, por ejemplo A.
        2.  Formar dos vectores directores usando el punto base: $\vec{u} = \vec{AB} = B - A$ y $\vec{v} = \vec{AC} = C - A$.
        3.  La ecuación vectorial es: $(x, y, z) = \lambda (B - A) + \beta (C - A) + A$.
    *   **Forma Implícita:**
        1.  Calcular los vectores directores $\vec{u} = B - A$ y $\vec{v} = C - A$.
        2.  Calcular el vector normal haciendo el producto vectorial: $\vec{n} = \vec{u} \times \vec{v}$.
        3.  Usar $\vec{n}$ y uno de los puntos (ej. A) en la ecuación $\vec{n} \cdot (X - A) = 0$.

*   **Planos Equivalentes:** Dos ecuaciones representan el mismo plano si:
    *   Ambas son implícitas: una ecuación es múltiplo escalar de la otra ($a_1x+b_1y+c_1z+d_1=0$ y $a_2x+b_2y+c_2z+d_2=0$ son equivalentes si $(a_2,b_2,c_2,d_2) = k(a_1,b_1,c_1,d_1)$ para algún $k \neq 0$).
    *   Ambas son vectoriales/paramétricas: Es más complejo, pero implica que generan el mismo conjunto de puntos. Se puede verificar si los vectores directores de uno son combinación lineal de los del otro y si el punto de paso de uno pertenece al otro plano.
    *   Una de cada tipo: Convertir una a la forma de la otra y comparar.

*   **Posición Relativa entre Planos:**
    *   **Paralelos:** Sus vectores normales $\vec{n_1}$ y $\vec{n_2}$ son paralelos ($\vec{n_2} = k \vec{n_1}$). Si además un punto de un plano pertenece al otro, son coincidentes.
    *   **Secantes:** Sus vectores normales no son paralelos. Se intersecan en una recta.
    *   **Perpendiculares:** Caso particular de secantes donde sus vectores normales son ortogonales ($\vec{n_1} \cdot \vec{n_2} = 0$).

## Rango de una Matriz

### Definición (vía Forma Escalonada)

*   Dada una matriz $A \in \mathbb{R}^{m \times n}$.
*   El **rango fila** $Rg_f(A)$ es el número de filas no nulas en una forma escalonada de $A$.
*   El **rango columna** $Rg_c(A)$ es el número de columnas no nulas (o equivalentemente, el número de pivotes) en una forma escalonada de $A$.
*   Teorema fundamental: $Rg_f(A) = Rg_c(A)$. A este valor común se le llama simplemente **rango** de $A$, denotado $Rg(A)$.
*   El rango representa el número máximo de filas (o columnas) linealmente independientes de la matriz.

### Menores de una Matriz

*   Una **submatriz** de orden $h$ de $A$ se obtiene al eliminar $m-h$ filas y $n-h$ columnas. Es una matriz cuadrada de $h \times h$.
*   Un **menor** de orden $h$ de $A$ es el determinante de una submatriz de orden $h$.

### Rango por Menores

*   Una definición alternativa del rango: $Rg(A) = k$ si se cumplen dos condiciones:
    1.  Existe al menos un menor de orden $k$ que es **no nulo**.
    2.  Todos los menores de orden $h$ son **nulos** para cualquier $h > k$.
*   En la práctica, se busca el mayor orden $k$ para el cual se puede encontrar un menor no nulo. Ese $k$ es el rango.

### Rango y Determinante (Matrices Cuadradas)

*   Para una matriz cuadrada $A$ de orden $n$:
    *   $\det(A) \neq 0 \iff Rg(A) = n$ (La matriz es de rango completo, invertible, sus filas/columnas son L.I.).
    *   $\det(A) = 0 \iff Rg(A) < n$ (La matriz no es de rango completo, no es invertible, sus filas/columnas son L.D.).
