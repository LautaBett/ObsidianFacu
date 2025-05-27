¡Absolutamente! Vamos a resolver el ejercicio 9 paso a paso, utilizando la información de los documentos [[Nucleo e imagen]] y [[Transformaciones Lineales]].

**Ejercicio 9:**

Si la transformación lineal $T$, en la base $B_1 = \{(-3, 7), (1, -2)\}$ y la transformación lineal $S$, en la base $B_2 = \{(6, -7), (-5, 6)\}$ tienen asociadas las matrices:

$[T]_{B_1} = \begin{pmatrix} 2 & -1 \\ 5 & -3 \end{pmatrix}$  y  $[S]_{B_2} = \begin{pmatrix} 1 & 3 \\ 2 & 7 \end{pmatrix}$

hallar la matriz de la transformación $T \circ S$ en la base canónica.

**Solución:**

1.  **Entender el problema:**

    *   Nos dan las matrices de $T$ y $S$ en bases no canónicas.
    *   Queremos encontrar la matriz de la composición $T \circ S$ en la base canónica.  Esto significa que queremos encontrar $[T \circ S]_C$, donde $C$ representa la base canónica.

2.  **Estrategia:**

    *   Recordemos que $[T \circ S]_C = [T]_C \cdot [S]_C$.  Por lo tanto, necesitamos encontrar $[T]_C$ y $[S]_C$.
    *   Usaremos la fórmula de cambio de base para encontrar $[T]_C$ a partir de $[T]_{B_1}$ y $[S]_C$ a partir de $[S]_{B_2}$.
    *   La fórmula general es: $[T]_B = I_{CB} \cdot [T]_C \cdot I_{BC}$, donde $I_{BC}$ es la matriz de cambio de base de $B$ a $C$ e $I_{CB}$ es la matriz de cambio de base de $C$ a $B$ (y $I_{CB} = I_{BC}^{-1}$).  Reorganizando, obtenemos: $[T]_C = I_{BC} \cdot [T]_B \cdot I_{CB}$.

3.  **Encontrar $[T]_C$:**

    *   $B_1 = \{(-3, 7), (1, -2)\}$
    *   $[T]_{B_1} = \begin{pmatrix} 2 & -1 \\ 5 & -3 \end{pmatrix}$
    *   $I_{CB_1}$ (matriz de cambio de base de $C$ a $B_1$):  Para encontrarla, expresamos los vectores de la base canónica como combinación lineal de los vectores de $B_1$.  Sin embargo, es más fácil encontrar $I_{B_1C}$ (matriz de cambio de base de $B_1$ a $C$) y luego invertirla.
    *   $I_{B_1C} = \begin{pmatrix} -3 & 1 \\ 7 & -2 \end{pmatrix}$ (simplemente colocamos los vectores de $B_1$ como columnas).
    *   $I_{CB_1} = I_{B_1C}^{-1} = \frac{1}{(-3)(-2) - (1)(7)} \begin{pmatrix} -2 & -1 \\ -7 & -3 \end{pmatrix} = \frac{1}{-1} \begin{pmatrix} -2 & -1 \\ -7 & -3 \end{pmatrix} = \begin{pmatrix} 2 & 1 \\ 7 & 3 \end{pmatrix}$
    *   $[T]_C = I_{B_1C} \cdot [T]_{B_1} \cdot I_{CB_1} = \begin{pmatrix} -3 & 1 \\ 7 & -2 \end{pmatrix} \cdot \begin{pmatrix} 2 & -1 \\ 5 & -3 \end{pmatrix} \cdot \begin{pmatrix} 2 & 1 \\ 7 & 3 \end{pmatrix}$
    *   $[T]_C = \begin{pmatrix} -3 & 1 \\ 7 & -2 \end{pmatrix} \cdot \begin{pmatrix} -3 & -4 \\ -11 & -16 \end{pmatrix} = \begin{pmatrix} 9+ (-11) & 12 + (-16) \\ -21 + 22 & -28 + 32 \end{pmatrix} = \begin{pmatrix} -2 & -4 \\ 1 & 4 \end{pmatrix}$

4.  **Encontrar $[S]_C$:**

    *   $B_2 = \{(6, -7), (-5, 6)\}$
    *   $[S]_{B_2} = \begin{pmatrix} 1 & 3 \\ 2 & 7 \end{pmatrix}$
    *   $I_{B_2C} = \begin{pmatrix} 6 & -5 \\ -7 & 6 \end{pmatrix}$
    *   $I_{CB_2} = I_{B_2C}^{-1} = \frac{1}{(6)(6) - (-5)(-7)} \begin{pmatrix} 6 & 5 \\ 7 & 6 \end{pmatrix} = \frac{1}{1} \begin{pmatrix} 6 & 5 \\ 7 & 6 \end{pmatrix} = \begin{pmatrix} 6 & 5 \\ 7 & 6 \end{pmatrix}$
    *   $[S]_C = I_{B_2C} \cdot [S]_{B_2} \cdot I_{CB_2} = \begin{pmatrix} 6 & -5 \\ -7 & 6 \end{pmatrix} \cdot \begin{pmatrix} 1 & 3 \\ 2 & 7 \end{pmatrix} \cdot \begin{pmatrix} 6 & 5 \\ 7 & 6 \end{pmatrix}$
    *   $[S]_C = \begin{pmatrix} 6 & -5 \\ -7 & 6 \end{pmatrix} \cdot \begin{pmatrix} 27 & 23 \\ 56 & 47 \end{pmatrix} = \begin{pmatrix} 162 - 280 & 138 - 235 \\ -189 + 336 & -161 + 282 \end{pmatrix} = \begin{pmatrix} -118 & -97 \\ 147 & 121 \end{pmatrix}$

5.  **Encontrar $[T \circ S]_C$:**

    *   $[T \circ S]_C = [T]_C \cdot [S]_C = \begin{pmatrix} -2 & -4 \\ 1 & 4 \end{pmatrix} \cdot \begin{pmatrix} -118 & -97 \\ 147 & 121 \end{pmatrix}$
    *   $[T \circ S]_C = \begin{pmatrix} 236 - 588 & 194 - 484 \\ -118 + 588 & -97 + 484 \end{pmatrix} = \begin{pmatrix} -352 & -290 \\ 470 & 387 \end{pmatrix}$

**Respuesta:**

La matriz de la transformación $T \circ S$ en la base canónica es:

$[T \circ S]_C = \begin{pmatrix} -352 & -290 \\ 470 & 387 \end{pmatrix}$

**Puntos clave:**

*   El orden de las matrices en la composición es crucial.
*   Las matrices de cambio de base son fundamentales para pasar de una base a otra.
*   La fórmula $[T]_C = I_{BC} \cdot [T]_B \cdot I_{CB}$ es esencial para resolver este tipo de problemas.

¡Espero que esta explicación detallada te sea de gran ayuda! Si tienes alguna otra pregunta, no dudes en consultarme.