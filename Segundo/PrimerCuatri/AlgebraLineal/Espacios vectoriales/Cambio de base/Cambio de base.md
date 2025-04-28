

## <span style="color:blue;">Álgebra Lineal: Cambio de Base</span>

### <span style="color:green;">1. La Idea Principal: Diferentes Perspectivas</span>

Imagina que estás describiendo la ubicación de un objeto en una habitación. Puedes decir "está a 3 pasos de la pared norte y 2 pasos de la pared este" (usando las paredes como referencia). Pero otra persona podría decir "está a 4 pasos en diagonal desde la esquina suroeste y 1 paso hacia la ventana" (usando la esquina y la ventana como referencia).

*   **El objeto (vector) es el mismo.** Su posición física no cambia.
*   **El sistema de referencia (base) es diferente.** En el primer caso, la base son los vectores "1 paso al norte" y "1 paso al este". En el segundo, son "1 paso en diagonal" y "1 paso hacia la ventana".
*   **La descripción (coordenadas) cambia.** Los números (3, 2) y (4, 1) son diferentes, pero describen la misma ubicación respecto a *su* sistema de referencia.

En álgebra lineal:

*   Un **vector** $\mathbf{v}$ existe en un espacio vectorial $V$.
*   Una **base** $B = \{\mathbf{b}_1, \dots, \mathbf{b}_n\}$ es un conjunto de vectores L.I. que genera $V$. Nos da un "sistema de coordenadas" para $V$.
*   Las **coordenadas** de $\mathbf{v}$ en la base $B$, denotadas como $[\mathbf{v}]_B$, son los escalares únicos $c_1, \dots, c_n$ tales que $\mathbf{v} = c_1 \mathbf{b}_1 + \dots + c_n \mathbf{b}_n$. Usualmente escribimos $[\mathbf{v}]_B = \begin{pmatrix} c_1 \\ \vdots \\ c_n \end{pmatrix}$.

El **cambio de base** es el proceso de encontrar las coordenadas de un mismo vector $\mathbf{v}$ pero respecto a una **nueva base** $C = \{\mathbf{c}_1, \dots, \mathbf{c}_n\}$, es decir, encontrar $[\mathbf{v}]_C$, si ya conocemos sus coordenadas $[\mathbf{v}]_B$ en la base original $B$.

### <span style="color:green;">2. La Herramienta: La Matriz de Cambio de Base</span>

Existe una matriz cuadrada invertible, llamada **matriz de cambio de base** (o matriz de transición), que nos permite "traducir" las coordenadas de una base a otra.

*   Denotaremos como $P_{C \leftarrow B}$ la matriz que transforma las coordenadas de la base $B$ a la base $C$.
*   La relación es:
    $$ [\mathbf{v}]_C = P_{C \leftarrow B} [\mathbf{v}]_B $$

**¿Cómo encontrar esta matriz $P_{C \leftarrow B}$?**

Hay varias formas, pero una muy práctica (especialmente cuando trabajamos en $\mathbb{R}^n$) utiliza la base canónica (estándar) $E$ como intermediaria.

1.  **Formar las Matrices de Base:**
    *   Crea la matriz $P_B$ cuyas columnas son los vectores de la base $B$ expresados en coordenadas de la base estándar $E$. (Si los vectores de $B$ ya están dados como vectores columna usuales en $\mathbb{R}^n$, $P_B$ es simplemente la matriz que tiene esos vectores como columnas).
    *   Crea la matriz $P_C$ cuyas columnas son los vectores de la base $C$ expresados en coordenadas de la base estándar $E$.

    *Interpretación:*
    *   $P_B$ transforma coordenadas de $B$ a $E$: $[\mathbf{v}]_E = P_B [\mathbf{v}]_B$.
    *   $P_C$ transforma coordenadas de $C$ a $E$: $[\mathbf{v}]_E = P_C [\mathbf{v}]_C$.

2.  **Relacionar las Coordenadas:**
    Como ambas expresiones dan $[\mathbf{v}]_E$, tenemos:
    $$ P_C [\mathbf{v}]_C = P_B [\mathbf{v}]_B $$

3.  **Despejar $[\mathbf{v}]_C$:**
    Para obtener $[\mathbf{v}]_C$, necesitamos multiplicar por la inversa de $P_C$ (que existe porque las columnas de $P_C$ forman una base y son L.I.):
    $$ [\mathbf{v}]_C = P_C^{-1} P_B [\mathbf{v}]_B $$

4.  **Identificar la Matriz de Cambio de Base:**
    Comparando con la fórmula original $[\mathbf{v}]_C = P_{C \leftarrow B} [\mathbf{v}]_B$, vemos que:
    $$ P_{C \leftarrow B} = P_C^{-1} P_B $$

**En resumen:** La matriz que convierte coordenadas de la base $B$ a la base $C$ se calcula como el producto de la inversa de la matriz de la base $C$ (en coords estándar) por la matriz de la base $B$ (en coords estándar).

### <span style="color:green;">3. Pasos Prácticos (Ejemplo en $\mathbb{R}^n$)</span>

Dados:
*   Base "vieja" $B = \{\mathbf{b}_1, \dots, \mathbf{b}_n\}$ (vectores dados en coords estándar).
*   Base "nueva" $C = \{\mathbf{c}_1, \dots, \mathbf{c}_n\}$ (vectores dados en coords estándar).
*   Coordenadas de un vector $\mathbf{v}$ en la base $B$: $[\mathbf{v}]_B$.

Objetivo: Encontrar $[\mathbf{v}]_C$.

**Procedimiento:**

1.  **Construir $P_B$:** La matriz cuyas columnas son $\mathbf{b}_1, \dots, \mathbf{b}_n$.
2.  **Construir $P_C$:** La matriz cuyas columnas son $\mathbf{c}_1, \dots, \mathbf{c}_n$.
3.  **Calcular $P_C^{-1}$:** Encontrar la inversa de la matriz $P_C$.
4.  **Calcular $P_{C \leftarrow B}$:** Multiplicar las matrices: $P_{C \leftarrow B} = P_C^{-1} P_B$.
5.  **Calcular $[\mathbf{v}]_C$:** Multiplicar la matriz por el vector de coordenadas: $[\mathbf{v}]_C = P_{C \leftarrow B} [\mathbf{v}]_B$.

### <span style="color:green;">4. Explicación Sencilla (Analogía del Traductor)</span>

Piensa en las bases $B$ y $C$ como dos idiomas diferentes (por ejemplo, Español y Japonés). El vector $\mathbf{v}$ es una idea o concepto.

*   $[\mathbf{v}]_B$ es cómo expresas esa idea en Español.
*   $[\mathbf{v}]_C$ es cómo expresas la *misma* idea en Japonés.

La **matriz de cambio de base $P_{C \leftarrow B}$ es como un diccionario o un traductor automático** que toma la frase en Español ($[\mathbf{v}]_B$) y la convierte a su equivalente en Japonés ($[\mathbf{v}]_C$).

*   La matriz $P_B$ traduce del Español al "lenguaje universal" (la base estándar $E$).
*   La matriz $P_C$ traduce del Japonés al "lenguaje universal" ($E$).
*   Para traducir de Español a Japonés ($B \to C$), primero traduces de Español a Universal ($P_B$), y luego necesitas "invertir" el traductor Japonés-Universal para ir de Universal a Japonés ($P_C^{-1}$). Por eso la fórmula es $P_{C \leftarrow B} = P_C^{-1} P_B$.

Cambiar de base nos permite elegir el "idioma" o el "sistema de coordenadas" más conveniente para describir un vector o resolver un problema particular. A veces, un problema que parece complicado en una base se vuelve mucho más simple en otra.