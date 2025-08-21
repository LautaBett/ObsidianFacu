¡Claro! Vamos a resolver estos ejercicios utilizando la información de las notas que me proporcionaste.

**Ejercicio 1:**

Dado $S^\perp = \begin{cases}
x - 9y + 8z - t = 0 \\
x - y + z + t = 0 \\
2x - 3y + 5z - 7t = 0
\end{cases}$

1.  **Hallar una base de** $S^\perp$:

   *   Escribimos la matriz de coeficientes del sistema:
       $A = \begin{pmatrix} 1 & -9 & 8 & -1 \\ 1 & -1 & 1 & 1 \\ 2 & -3 & 5 & -7 \end{pmatrix}$
   *   Reducimos la matriz a su forma escalonada reducida por filas:
       $\begin{pmatrix} 1 & -9 & 8 & -1 \\ 1 & -1 & 1 & 1 \\ 2 & -3 & 5 & -7 \end{pmatrix} \sim \begin{pmatrix} 1 & 0 & \frac{1}{8} & \frac{17}{8} \\ 0 & 1 & -\frac{7}{8} & -\frac{1}{8} \\ 0 & 0 & 0 & 0 \end{pmatrix}$
   *   Resolvemos el sistema resultante:
       $x + \frac{1}{8}z + \frac{17}{8}t = 0 \implies x = -\frac{1}{8}z - \frac{17}{8}t$
       $y - \frac{7}{8}z - \frac{1}{8}t = 0 \implies y = \frac{7}{8}z + \frac{1}{8}t$
   *   Expresamos las soluciones en forma paramétrica:
       $\begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = z \begin{pmatrix} -\frac{1}{8} \\ \frac{7}{8} \\ 1 \\ 0 \end{pmatrix} + t \begin{pmatrix} -\frac{17}{8} \\ \frac{1}{8} \\ 0 \\ 1 \end{pmatrix}$
   *   Una base para $S^\perp$ es:
       $B_{S^\perp} = \left\{ \begin{pmatrix} -1 \\ 7 \\ 8 \\ 0 \end{pmatrix}, \begin{pmatrix} -17 \\ 1 \\ 0 \\ 8 \end{pmatrix} \right\}$

2.  **Hallar una base de** $S$:

   *   Como $S = (S^\perp)^\perp$, necesitamos encontrar un sistema de ecuaciones que determine $S$.
   *   Los vectores de la base de $S^\perp$ son ortogonales a $S$. Por lo tanto, para cualquier vector $(x, y, z, t) \in S$, se cumple:
       $\begin{cases} -x + 7y + 8z = 0 \\ -17x + y + 8t = 0 \end{cases}$
   *   Este sistema de ecuaciones define $S$.
   *   Para encontrar una base de $S$, resolvemos este sistema:
       $y = 17x - 8t$
       $-x + 7(17x - 8t) + 8z = 0 \implies -x + 119x - 56t + 8z = 0 \implies 118x - 56t + 8z = 0 \implies z = - \frac{59}{4}x + 7t$
   *   Expresamos las soluciones en forma paramétrica:
       $\begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = x \begin{pmatrix} 1 \\ 17 \\ -\frac{59}{4} \\ 0 \end{pmatrix} + t \begin{pmatrix} 0 \\ -8 \\ 7 \\ 1 \end{pmatrix}$
   *   Una base para $S$ es:
       $B_S = \left\{ \begin{pmatrix} 4 \\ 68 \\ -59 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ -8 \\ 7 \\ 1 \end{pmatrix} \right\}$

3.  **Sistema de ecuaciones que determina** $S$:

   *   El sistema de ecuaciones que determina $S$ es:
       $\begin{cases} -x + 7y + 8z = 0 \\ -17x + y + 8t = 0 \end{cases}$

**Ejercicio 2:**

Dado $S = \begin{cases}
x - y - z + t = 0 \\
x + y + z + t = 0 \\
x - y - z - t = 0
\end{cases}$

1.  **Hallar una base de** $S$:

   *   Escribimos la matriz de coeficientes del sistema:
       $A = \begin{pmatrix} 1 & -1 & -1 & 1 \\ 1 & 1 & 1 & 1 \\ 1 & -1 & -1 & -1 \end{pmatrix}$
   *   Reducimos la matriz a su forma escalonada reducida por filas:
       $\begin{pmatrix} 1 & -1 & -1 & 1 \\ 1 & 1 & 1 & 1 \\ 1 & -1 & -1 & -1 \end{pmatrix} \sim \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$
   *   Resolvemos el sistema resultante:
       $x = 0$
       $y + z = 0 \implies y = -z$
       $t = 0$
   *   Expresamos las soluciones en forma paramétrica:
       $\begin{pmatrix} x \\ y \\ z \\ t \end{pmatrix} = z \begin{pmatrix} 0 \\ -1 \\ 1 \\ 0 \end{pmatrix}$
   *   Una base para $S$ es:
       $B_S = \left\{ \begin{pmatrix} 0 \\ -1 \\ 1 \\ 0 \end{pmatrix} \right\}$

2.  **Hallar una base de** $S^\perp$:

   *   Como $S$ está definido por las ecuaciones dadas, $S^\perp$ estará generado por los vectores normales a estos planos. Es decir, los coeficientes de las ecuaciones forman los vectores generadores de $S^\perp$:
       $S^\perp = \langle (1, -1, -1, 1), (1, 1, 1, 1), (1, -1, -1, -1) \rangle$
   *   Para encontrar una base, verificamos si estos vectores son linealmente independientes. Formamos la matriz con estos vectores como columnas:
       $A = \begin{pmatrix} 1 & 1 & 1 \\ -1 & 1 & -1 \\ -1 & 1 & -1 \\ 1 & 1 & -1 \end{pmatrix}$
   *   Reducimos la matriz a su forma escalonada reducida por filas:
       $\begin{pmatrix} 1 & 1 & 1 \\ -1 & 1 & -1 \\ -1 & 1 & -1 \\ 1 & 1 & -1 \end{pmatrix} \sim \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & 0 \end{pmatrix}$
   *   Los tres vectores son linealmente independientes, pero como estamos en $\mathbb{R}^4$ y $\dim(S) = 1$, entonces $\dim(S^\perp) = 4 - 1 = 3$. Necesitamos encontrar tres vectores linealmente independientes que generen $S^\perp$.
   *   Observamos que el tercer vector es una combinación lineal de los dos primeros: $(1, -1, -1, -1) = -1 \cdot (1, -1, -1, 1) + 0 \cdot (1, 1, 1, 1)$. Por lo tanto, podemos eliminarlo.
   *   Sin embargo, necesitamos tres vectores. Como $S$ está definido por las ecuaciones dadas, $S^\perp$ estará generado por los vectores normales a estos planos. Es decir, los coeficientes de las ecuaciones forman los vectores generadores de $S^\perp$:
       $S^\perp = \langle (1, -1, -1, 1), (1, 1, 1, 1), (1, -1, -1, -1) \rangle$
   *   Como $\dim(S) = 1$, entonces $\dim(S^\perp) = 4 - 1 = 3$. Necesitamos encontrar tres vectores linealmente independientes que generen $S^\perp$.
   *   Observamos que el tercer vector es una combinación lineal de los dos primeros: $(1, -1, -1, -1) = -1 \cdot (1, -1, -1, 1) + 0 \cdot (1, 1, 1, 1)$. Por lo tanto, podemos eliminarlo.
   *   Necesitamos encontrar un tercer vector que sea ortogonal a $S$. Un vector $(a, b, c, d)$ es ortogonal a $S$ si su producto punto con el vector de la base de $S$ es cero:
       $(a, b, c, d) \cdot (0, -1, 1, 0) = 0 \implies -b + c = 0 \implies b = c$
   *   Podemos elegir un vector que no sea combinación lineal de los dos primeros, por ejemplo, $(0, 1, 1, 0)$.
   *   Una base para $S^\perp$ es:
       $B_{S^\perp} = \left\{ (1, -1, -1, 1), (1, 1, 1, 1), (0, 1, 1, 0) \right\}$

3.  **Sistema de ecuaciones que determina** $S^\perp$:

   *   Como $S = (S^\perp)^\perp$, necesitamos encontrar un sistema de ecuaciones que determine $S^\perp$.
   *   Los vectores de la base de $S$ son ortogonales a $S^\perp$. Por lo tanto, para cualquier vector $(x, y, z, t) \in S^\perp$, se cumple:
       $(x, y, z, t) \cdot (0, -1, 1, 0) = 0 \implies -y + z = 0$
   *   El sistema de ecuaciones que determina $S^\perp$ es:
       $-y + z = 0$

**Ejercicio 3:**

a) $S = \{(x, y, z) \in \mathbb{R}^3 : x + 3y - z = 0\}$

*   **Base ortogonal:**
    *   Resolvemos la ecuación: $x = -3y + z$
    *   Expresamos las soluciones en forma paramétrica:
        $\begin{pmatrix} x \\ y \\ z \end{pmatrix} = y \begin{pmatrix} -3 \\ 1 \\ 0 \end{pmatrix} + z \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}$
    *   Una base para $S$ es: $B_S = \left\{ \begin{pmatrix} -3 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix} \right\}$
    *   Verificamos si los vectores son ortogonales: $(-3, 1, 0) \cdot (1, 0, 1) = -3 + 0 + 0 = -3 \neq 0$. No son ortogonales.
    *   Aplicamos Gram-Schmidt:
        *   $v_1 = (-3, 1, 0)$
        *   $v_2' = (1, 0, 1) - \frac{(1, 0, 1) \cdot (-3, 1, 0)}{||(-3, 1, 0)||^2} (-3, 1, 0) = (1, 0, 1) - \frac{-3}{10} (-3, 1, 0) = (1, 0, 1) - (-\frac{3}{10})(-3, 1, 0) = (1, 0, 1) - (\frac{9}{10}, -\frac{3}{10}, 0) = (\frac{1}{10}, \frac{3}{10}, 1)$
    *   Una base ortogonal para $S$ es: $B_{S}^{ortogonal} = \left\{ \begin{pmatrix} -3 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 1 \\ 3 \\ 10 \end{pmatrix} \right\}$
*   **Base ortonormal:**
    *   Normalizamos los vectores de la base ortogonal:
        *   $||(-3, 1, 0)|| = \sqrt{(-3)^2 + 1^2 + 0^2} = \sqrt{10}$
        *   $||(1, 3, 10)|| = \sqrt{1^2 + 3^2 + 10^2} = \sqrt{110}$
    *   Una base ortonormal para $S$ es: $B_{S}^{ortonormal} = \left\{ \frac{1}{\sqrt{10}} \begin{pmatrix} -3 \\ 1 \\ 0 \end{pmatrix}, \frac{1}{\sqrt{110}} \begin{pmatrix} 1 \\ 3 \\ 10 \end{pmatrix} \right\}$

b) $S = \{(x, y, z) \in \mathbb{R}^3 : x = \alpha, y = -\alpha, z = 3\alpha\}$

*   **Base ortogonal:**
    *   $S = \langle (1, -1, 3) \rangle$
    *   Una base para $S$ es: $B_S = \left\{ \begin{pmatrix} 1 \\ -1 \\ 3 \end{pmatrix} \right\}$
    *   Como solo hay un vector, ya es ortogonal.
*   **Base ortonormal:**
    *   Normalizamos el vector:
        *   $||(1, -1, 3)|| = \sqrt{1^2 + (-1)^2 + 3^2} = \sqrt{11}$
    *   Una base ortonormal para $S$ es: $B_{S}^{ortonormal} = \left\{ \frac{1}{\sqrt{11}} \begin{pmatrix} 1 \\ -1 \\ 3 \end{pmatrix} \right\}$

**Ejercicio 4:**

a) $n = 3, S = \{(x, y, z) \in \mathbb{R}^3 : x + y + z = 0\}$

*   Resolvemos la ecuación: $x = -y - z$
*   Expresamos las soluciones en forma paramétrica:
    $\begin{pmatrix} x \\ y \\ z \end{pmatrix} = y \begin{pmatrix} -1 \\ 1 \\ 0 \end{pmatrix} + z \begin{pmatrix} -1 \\ 0 \\ 1 \end{pmatrix}$
*   Una base para $S$ es: $B_S = \left\{ \begin{pmatrix} -1 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} -1 \\ 0 \\ 1 \end{pmatrix} \right\}$
*   Verificamos si los vectores son ortogonales: $(-1, 1, 0) \cdot (-1, 0, 1) = 1 + 0 + 0 = 1 \neq 0$. No son ortogonales.
*   Aplicamos Gram-Schmidt:
    *   $v_1 = (-1, 1, 0)$
    *   $v_2' = (-1, 0, 1) - \frac{(-1, 0, 1) \cdot (-1, 1, 0)}{||(-1, 1, 0)||^2} (-1, 1, 0) = (-1, 0, 1) - \frac{1}{2} (-1, 1, 0) = (-1, 0, 1) - (-\frac{1}{2}, \frac{1}{2}, 0) = (-\frac{1}{2}, -\frac{1}{2}, 1)$
*   Una base ortogonal para $S$ es: $B_{S}^{ortogonal} = \left\{ \begin{pmatrix} -1 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} -1 \\ -1 \\ 2 \end{pmatrix} \right\}$
*   Normalizamos los vectores de la base ortogonal:
    *   $||(-1, 1, 0)|| = \sqrt{(-1)^2 + 1^2 + 0^2} = \sqrt{2}$
    *   $||(-1, -1, 2)|| = \sqrt{(-1)^2 + (-1)^2 + 2^2} = \sqrt{6}$
*   Una base ortonormal para $S$ es: $B_{S}^{ortonormal} = \left\{ \frac{1}{\sqrt{2}} \begin{pmatrix} -1 \\ 1 \\ 0 \end{pmatrix}, \frac{1}{\sqrt{6}} \begin{pmatrix} -1 \\ -1 \\ 2 \end{pmatrix} \right\}$

b) $n = 3, S = \langle(1,2,2, -1), (1,1, -5,3), (3,2,8, -7)\rangle$

*   Primero, verificamos si los vectores son linealmente independientes. Formamos la matriz con estos vectores como columnas:
    $A = \begin{pmatrix} 1 & 1 & 3 \\ 2 & 1 & 2 \\ 2 & -5 & 8 \\ -1 & 3 & -7 \end{pmatrix}$
*   Reducimos la matriz a su forma escalonada reducida por filas:
    $\begin{pmatrix} 1 & 1 & 3 \\ 2 & 1 & 2 \\ 2 & -5 & 8 \\ -1 & 3 & -7 \end{pmatrix} \sim \begin{pmatrix} 1 & 0 & 1 \\ 0 & 1 & 2 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}$
*   Los vectores son linealmente dependientes. Los dos primeros vectores forman una base para $S$.
*   Una base para $S$ es: $B_S = \left\{ \begin{pmatrix} 1 \\ 2 \\ 2 \\ -1 \end{pmatrix}, \begin{pmatrix} 1 \\ 1 \\ -5 \\ 3 \end{pmatrix} \right\}$
*   Aplicamos Gram-Schmidt:
    *   $v_1 = (1, 2, 2, -1)$
    *   $v_2' = (1, 1, -5, 3) - \frac{(1, 1, -5, 3) \cdot (1, 2, 2, -1)}{||(1, 2, 2, -1)||^2} (1, 2, 2, -1) = (1, 1, -5, 3) - \frac{1 + 2 - 10 - 3}{1 + 4 + 4 + 1} (1, 2, 2, -1) = (1, 1, -5, 3) - \frac{-10}{10} (1, 2, 2, -1) = (1, 1, -5, 3) + (1, 2, 2, -1) = (2, 3, -3, 2)$
*   Una base ortogonal para $S$ es: $B_{S}^{ortogonal} = \left\{ \begin{pmatrix} 1 \\ 2 \\ 2 \\ -1 \end{pmatrix}, \begin{pmatrix} 2 \\ 3 \\ -3 \\ 2 \end{pmatrix} \right\}$
*   Normalizamos los vectores de la base ortogonal:
    *   $||(1, 2, 2, -1)|| = \sqrt{1^2 + 2^2 + 2^2 + (-1)^2} = \sqrt{10}$
    *   $||(2, 3, -3, 2)|| = \sqrt{2^2 + 3^2 + (-3)^2 + 2^2} = \sqrt{26}$
*   Una base ortonormal para $S$ es: $B_{S}^{ortonormal} = \left\{ \frac{1}{\sqrt{10}} \begin{pmatrix} 1 \\ 2 \\ 2 \\ -1 \end{pmatrix}, \frac{1}{\sqrt{26}} \begin{pmatrix} 2 \\ 3 \\ -3 \\ 2 \end{pmatrix} \right\}$

c) $n = 3, S = \begin{cases}
x + y + z = 0 \\
x - y + z = 0
\end{cases}$

*   Resolvemos el sistema de ecuaciones:
    *   Sumamos las ecuaciones: $2x + 2z = 0 \implies x = -z$
    *   Sustituimos en la primera ecuación: $-z + y + z = 0 \implies y = 0$
*   Expresamos las soluciones en forma paramétrica:
    $\begin{pmatrix} x \\ y \\ z \end{pmatrix} = z \begin{pmatrix} -1 \\ 0 \\ 1 \end{pmatrix}$
*   Una base para $S$ es: $B_S = \left\{ \begin{pmatrix} -1 \\ 0 \\ 1 \end{pmatrix} \right\}$
*   Como solo hay un vector, ya es ortogonal.
*   Normalizamos el vector:
    *   $||(-1, 0, 1)|| = \sqrt{(-1)^2 + 0^2 + 1^2} = \sqrt{2}$
*   Una base ortonormal para $S$ es: $B_{S}^{ortonormal} = \left\{ \frac{1}{\sqrt{2}} \begin{pmatrix} -1 \\ 0 \\ 1 \end{pmatrix} \right\}$

**Ejercicio 5:**

a) $S = \{(x, y, z) \in \mathbb{R}^3 : x + y + z = 0\}, v = (2,1,1)$

*   El vector normal al hiperplano $S$ es $n = (1, 1, 1)$.
*   La proyección de $v$ sobre $S^\perp$ es:
    $proy_{S^\perp}(v) = \frac{v \cdot n}{||n||^2} n = \frac{(2, 1, 1) \cdot (1, 1, 1)}{||(1, 1, 1)||^2} (1, 1, 1) = \frac{2 + 1 + 1}{1 + 1 + 1} (1, 1, 1) = \frac{4}{3} (1, 1, 1) = (\frac{4}{3}, \frac{4}{3}, \frac{4}{3})$
*   La proyección de $v$ sobre $S$ es:
    $proy_S(v) = v - proy_{S^\perp}(v) = (2, 1, 1) - (\frac{4}{3}, \frac{4}{3}, \frac{4}{3}) = (\frac{6}{3} - \frac{4}{3}, \frac{3}{3} - \frac{4}{3}, \frac{3}{3} - \frac{4}{3}) = (\frac{2}{3}, -\frac{1}{3}, -\frac{1}{3})$

b) $S = \{(x, y, z, t) \in \mathbb{R}^4 : x + y + z + t = 0\}, v = (1,1,1,1)$

*   El vector normal al hiperplano $S$ es $n = (1, 1, 1, 1)$.
*   La proyección de $v$ sobre $S^\perp$ es:
    $proy_{S^\perp}(v) = \frac{v \cdot n}{||n||^2} n = \frac{(1, 1, 1, 1) \cdot (1, 1, 1, 1)}{||(1, 1, 1, 1)||^2} (1, 1, 1, 1) = \frac{1 + 1 + 1 + 1}{1 + 1 + 1 + 1} (1, 1, 1, 1) = \frac{4}{4} (1, 1, 1, 1) = (1, 1, 1, 1)$
*   La proyección de $v$ sobre $S$ es:
    $proy_S(v) = v - proy_{S^\perp}(v) = (1, 1, 1, 1) - (1, 1, 1, 1) = (0, 0, 0, 0)$

c) $S = \{(x, y, z) \in \mathbb{R}^3 : x - y + 2z = 0\}, v = (3, -1, 2)$

*   El vector normal al hiperplano $S$ es $n = (1, -1, 2)$.
*   La proyección de $v$ sobre $S^\perp$ es:
    $proy_{S^\perp}(v) = \frac{v \cdot n}{||n||^2} n = \frac{(3, -1, 2) \cdot (1, -1, 2)}{||(1, -1, 2)||^2} (1, -1, 2) = \frac{3 + 1 + 4}{1 + 1 + 4} (1, -1, 2) = \frac{8}{6} (1, -1, 2) = \frac{4}{3} (1, -1, 2) = (\frac{4}{3}, -\frac{4}{3}, \frac{8}{3})$
*   La proyección de $v$ sobre $S$ es:
    $proy_S(v) = v - proy_{S^\perp}(v) = (3, -1, 2) - (\frac{4}{3}, -\frac{4}{3}, \frac{8}{3}) = (\frac{9}{3} - \frac{4}{3}, -\frac{3}{3} + \frac{4}{3}, \frac{6}{3} - \frac{8}{3}) = (\frac{5}{3}, \frac{1}{3}, -\frac{2}{3})$

¡Espero que esto te ayude! Si tienes alguna otra pregunta, no dudes en preguntar.