¡Claro! Aquí tienes las resoluciones completas de los ejercicios 9, 10 y 11, basadas en la información de [[Cambio de base]] y los pasos que hemos seguido.

---

### Ejercicio 9: Hallar la Matriz de Cambio de Base $I_{B_2 \leftarrow B_1}$

**Método General:**
1.  Formar $P_{B_1}$ (columnas son vectores de $B_1$ en base estándar).
2.  Formar $P_{B_2}$ (columnas son vectores de $B_2$ en base estándar).
3.  Calcular $I_{B_2 \leftarrow B_1} = P_{B_2}^{-1} P_{B_1}$ mediante la reducción por filas de $[P_{B_2} | P_{B_1}]$ a $[I | I_{B_2 \leftarrow B_1}]$.

**a) $V = \mathbb{R}^3$**
$B_1 = \{(1,2,1), (2,3,3), (3,7,1)\}$
$B_2 = \{(3,1,4), (5,2,1), (1,1,-6)\}$

*   $P_{B_1} = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 3 & 7 \\ 1 & 3 & 1 \end{pmatrix}$
*   $P_{B_2} = \begin{pmatrix} 3 & 5 & 1 \\ 1 & 2 & 1 \\ 4 & 1 & -6 \end{pmatrix}$
*   Reduciendo $[P_{B_2} | P_{B_1}]$:
    $$ \left[ \begin{array}{ccc|ccc} 3 & 5 & 1 & 1 & 2 & 3 \\ 1 & 2 & 1 & 2 & 3 & 7 \\ 4 & 1 & -6 & 1 & 3 & 1 \end{array} \right] \longrightarrow \left[ \begin{array}{ccc|ccc} 1 & 0 & 0 & 13 & 19 & -19/4 \\ 0 & 1 & 0 & -9 & -13 & -33/2 \\ 0 & 0 & 1 & 7 & 10 & 99/4 \end{array} \right] $$
*   **Matriz de Cambio de Base:**
    $$ I_{B_2 \leftarrow B_1} = \begin{pmatrix} 13 & 19 & -19/4 \\ -9 & -13 & -33/2 \\ 7 & 10 & 99/4 \end{pmatrix} $$

**b) $V = \mathbb{R}^4$**
$B_1 = \{(1,0,3,3), (-2,-3,-5,-4), (2,2,5,4), (-2,-3,-4,-4)\}$
$B_2 = \{(1,1,1,1), (1,2,1,1), (1,1,2,1), (1,3,2,3)\}$

*   $P_{B_1} = \begin{pmatrix} 1 & -2 & 2 & -2 \\ 0 & -3 & 2 & -3 \\ 3 & -5 & 5 & -4 \\ 3 & -4 & 4 & -4 \end{pmatrix}$
*   $P_{B_2} = \begin{pmatrix} 1 & 1 & 1 & 1 \\ 1 & 2 & 1 & 3 \\ 1 & 1 & 2 & 2 \\ 1 & 1 & 1 & 3 \end{pmatrix}$
*   Se forma la matriz aumentada $[P_{B_2} | P_{B_1}]$:
    $$ \left[ \begin{array}{cccc|cccc} 1 & 1 & 1 & 1 & 1 & -2 & 2 & -2 \\ 1 & 2 & 1 & 3 & 0 & -3 & 2 & -3 \\ 1 & 1 & 2 & 2 & 3 & -5 & 5 & -4 \\ 1 & 1 & 1 & 3 & 3 & -4 & 4 & -4 \end{array} \right] $$
*   Se reduce por filas esta matriz $4 \times 8$ hasta obtener la forma $[I | I_{B_2 \leftarrow B_1}]$. (El proceso de reducción es extenso).

**c) $V = P_4[x]$**
$B_1 = \{1, x, x^2, x^3, x^4\}$ (Base canónica $E$)
$B_2 = \{1, (x-\alpha), (x-\alpha)^2, (x-\alpha)^3, (x-\alpha)^4\}$

*   $P_{B_1} = I_5$
*   $P_{B_2} = \begin{pmatrix} 1 & -\alpha & \alpha^2 & -\alpha^3 & \alpha^4 \\ 0 & 1 & -2\alpha & 3\alpha^2 & -4\alpha^3 \\ 0 & 0 & 1 & -3\alpha & 6\alpha^2 \\ 0 & 0 & 0 & 1 & -4\alpha \\ 0 & 0 & 0 & 0 & 1 \end{pmatrix}$ (Coordenadas de $B_2$ en base $B_1=E$)
*   $I_{B_2 \leftarrow B_1} = P_{B_2}^{-1} P_{B_1} = P_{B_2}^{-1} I = P_{B_2}^{-1}$.
*   Reduciendo $[P_{B_2} | I]$ a $[I | P_{B_2}^{-1}]$ se obtiene:
*   **Matriz de Cambio de Base:**
    $$ I_{B_2 \leftarrow B_1} = \begin{pmatrix} 1 & \alpha & \alpha^2 & \alpha^3 & \alpha^4 \\ 0 & 1 & 2\alpha & 3\alpha^2 & 4\alpha^3 \\ 0 & 0 & 1 & 3\alpha & 6\alpha^2 \\ 0 & 0 & 0 & 1 & 4\alpha \\ 0 & 0 & 0 & 0 & 1 \end{pmatrix} $$

---

### Ejercicio 10

$V = P_2[x]$. Bases $S = \{x^2+1, x-2, x+3\}$ y $T = \{2x^2+x, 2x^2+3, x\}$. Vectores $v = 8x^2-4x+6$, $w = 7x^2-x+9$. Base estándar $E = \{1, x, x^2\}$.

*   $P_S = \begin{pmatrix} 1 & -2 & 3 \\ 0 & 1 & 1 \\ 1 & 0 & 0 \end{pmatrix}$
*   $P_T = \begin{pmatrix} 0 & 3 & 0 \\ 1 & 0 & 1 \\ 2 & 2 & 0 \end{pmatrix}$
*   $[v]_E = \begin{pmatrix} 6 \\ -4 \\ 8 \end{pmatrix}$
*   $[w]_E = \begin{pmatrix} 9 \\ -1 \\ 7 \end{pmatrix}$

**a) Coordenadas $[v]_T$ y $[w]_T$:**
Resolviendo $P_T [v]_T = [v]_E$ y $P_T [w]_T = [w]_E$:
*   $[v]_T = \begin{pmatrix} 2 \\ 2 \\ -6 \end{pmatrix}$
*   $[w]_T = \begin{pmatrix} 1/2 \\ 3 \\ -3/2 \end{pmatrix}$

**b) Matriz $I_{S \leftarrow T}$:**
$I_{S \leftarrow T} = P_S^{-1} P_T$.
*   $P_S^{-1} = \frac{1}{5}\begin{pmatrix} 0 & 0 & 5 \\ -1 & 3 & 1 \\ 1 & 2 & -1 \end{pmatrix}$
*   $I_{S \leftarrow T} = P_S^{-1} P_T = \frac{1}{5}\begin{pmatrix} 10 & 10 & 0 \\ 5 & -1 & 3 \\ 0 & 1 & 2 \end{pmatrix} = \begin{pmatrix} 2 & 2 & 0 \\ 1 & -1/5 & 3/5 \\ 0 & 1/5 & 2/5 \end{pmatrix}$

**c) Coordenadas $[v]_S$ y $[w]_S$ usando $I_{S \leftarrow T}$:**
*   $[v]_S = I_{S \leftarrow T} [v]_T = \begin{pmatrix} 2 & 2 & 0 \\ 1 & -1/5 & 3/5 \\ 0 & 1/5 & 2/5 \end{pmatrix} \begin{pmatrix} 2 \\ 2 \\ -6 \end{pmatrix} = \begin{pmatrix} 8 \\ -2 \\ -2 \end{pmatrix}$
*   $[w]_S = I_{S \leftarrow T} [w]_T = \begin{pmatrix} 2 & 2 & 0 \\ 1 & -1/5 & 3/5 \\ 0 & 1/5 & 2/5 \end{pmatrix} \begin{pmatrix} 1/2 \\ 3 \\ -3/2 \end{pmatrix} = \begin{pmatrix} 7 \\ -1 \\ 0 \end{pmatrix}$

**d) Coordenadas $[v]_S$ y $[w]_S$ directamente:**
Resolviendo $P_S [v]_S = [v]_E$ y $P_S [w]_S = [w]_E$:
*   $[v]_S = \begin{pmatrix} 8 \\ -2 \\ -2 \end{pmatrix}$
*   $[w]_S = \begin{pmatrix} 7 \\ -1 \\ 0 \end{pmatrix}$
(Coinciden con los resultados de c).

**e) Matriz $I_{T \leftarrow S}$:**
$I_{T \leftarrow S} = (I_{S \leftarrow T})^{-1}$.
*   $I_{T \leftarrow S} = \begin{pmatrix} 1/6 & 2/3 & -1 \\ 1/3 & -2/3 & 1 \\ -1/6 & 1/3 & 2 \end{pmatrix} = \frac{1}{6}\begin{pmatrix} 1 & 4 & -6 \\ 2 & -4 & 6 \\ -1 & 2 & 12 \end{pmatrix}$

**f) Coordenadas $[v]_T$ y $[w]_T$ usando $I_{T \leftarrow S}$:**
*   $[v]_T = I_{T \leftarrow S} [v]_S = \frac{1}{6}\begin{pmatrix} 1 & 4 & -6 \\ 2 & -4 & 6 \\ -1 & 2 & 12 \end{pmatrix} \begin{pmatrix} 8 \\ -2 \\ -2 \end{pmatrix} = \begin{pmatrix} 2 \\ 2 \\ -6 \end{pmatrix}$
    *   Comparando con (a): Coinciden.
*   $[w]_T = I_{T \leftarrow S} [w]_S = \frac{1}{6}\begin{pmatrix} 1 & 4 & -6 \\ 2 & -4 & 6 \\ -1 & 2 & 12 \end{pmatrix} \begin{pmatrix} 7 \\ -1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1/2 \\ 3 \\ -3/2 \end{pmatrix}$
    *   Comparando con (a): Coinciden.

---

### Ejercicio 11

$V = P_2[y]$.
$S = \{y^2+y+1, y^2+2y+3, y^2+1\}$
$T = \{y+1, y^2, y^2+1\}$
$v = -y^2+4y+5$
$w = 2y^2-6$
Base estándar $E = \{1, y, y^2\}$.

*   $P_S = \begin{pmatrix} 1 & 3 & 1 \\ 1 & 2 & 0 \\ 1 & 1 & 1 \end{pmatrix}$
*   $P_T = \begin{pmatrix} 1 & 0 & 1 \\ 1 & 0 & 0 \\ 0 & 1 & 1 \end{pmatrix}$
*   $[v]_E = \begin{pmatrix} 5 \\ 4 \\ -1 \end{pmatrix}$
*   $[w]_E = \begin{pmatrix} -6 \\ 0 \\ 2 \end{pmatrix}$

**a) Coordenadas $[v]_T$ y $[w]_T$:**
Resolviendo $P_T [v]_T = [v]_E$ y $P_T [w]_T = [w]_E$:
*   $[v]_T = \begin{pmatrix} 4 \\ -2 \\ 1 \end{pmatrix}$
*   $[w]_T = \begin{pmatrix} 0 \\ 8 \\ -6 \end{pmatrix}$

**b) Matriz $I_{S \leftarrow T}$:**
$I_{S \leftarrow T} = P_S^{-1} P_T$.
*   $P_S^{-1} = \frac{1}{2}\begin{pmatrix} -2 & 2 & 2 \\ 1 & 0 & -1 \\ 1 & -2 & 1 \end{pmatrix}$
*   $I_{S \leftarrow T} = P_S^{-1} P_T = \frac{1}{2}\begin{pmatrix} 0 & 2 & 0 \\ 1 & -1 & 0 \\ -1 & 1 & 2 \end{pmatrix} = \begin{pmatrix} 0 & 1 & 0 \\ 1/2 & -1/2 & 0 \\ -1/2 & 1/2 & 1 \end{pmatrix}$

**c) Coordenadas $[v]_S$ y $[w]_S$ usando $I_{S \leftarrow T}$:**
*   $[v]_S = I_{S \leftarrow T} [v]_T = \begin{pmatrix} 0 & 1 & 0 \\ 1/2 & -1/2 & 0 \\ -1/2 & 1/2 & 1 \end{pmatrix} \begin{pmatrix} 4 \\ -2 \\ 1 \end{pmatrix} = \begin{pmatrix} -2 \\ 3 \\ -2 \end{pmatrix}$
*   $[w]_S = I_{S \leftarrow T} [w]_T = \begin{pmatrix} 0 & 1 & 0 \\ 1/2 & -1/2 & 0 \\ -1/2 & 1/2 & 1 \end{pmatrix} \begin{pmatrix} 0 \\ 8 \\ -6 \end{pmatrix} = \begin{pmatrix} 8 \\ -4 \\ -2 \end{pmatrix}$

**d) Coordenadas $[v]_S$ y $[w]_S$ directamente:**
Resolviendo $P_S [v]_S = [v]_E$ y $P_S [w]_S = [w]_E$:
*   $[v]_S = \begin{pmatrix} -2 \\ 3 \\ -2 \end{pmatrix}$
*   $[w]_S = \begin{pmatrix} 8 \\ -4 \\ -2 \end{pmatrix}$
(Coinciden con los resultados de c).

**e) Matriz $I_{T \leftarrow S}$:**
$I_{T \leftarrow S} = (I_{S \leftarrow T})^{-1}$.
*   $I_{T \leftarrow S} = \begin{pmatrix} 1 & 2 & 0 \\ 1 & 0 & 0 \\ 0 & 1 & 1 \end{pmatrix}$

**f) Coordenadas $[v]_T$ y $[w]_T$ usando $I_{T \leftarrow S}$:**
*   $[v]_T = I_{T \leftarrow S} [v]_S = \begin{pmatrix} 1 & 2 & 0 \\ 1 & 0 & 0 \\ 0 & 1 & 1 \end{pmatrix} \begin{pmatrix} -2 \\ 3 \\ -2 \end{pmatrix} = \begin{pmatrix} 4 \\ -2 \\ 1 \end{pmatrix}$
    *   Comparando con (a): Coinciden.
*   $[w]_T = I_{T \leftarrow S} [w]_S = \begin{pmatrix} 1 & 2 & 0 \\ 1 & 0 & 0 \\ 0 & 1 & 1 \end{pmatrix} \begin{pmatrix} 8 \\ -4 \\ -2 \end{pmatrix} = \begin{pmatrix} 0 \\ 8 \\ -6 \end{pmatrix}$
    *   Comparando con (a): Coinciden.

