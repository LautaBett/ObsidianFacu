# Sistemas de Ecuaciones Lineales (SEL)

## 1. Ecuaciones Lineales

*   Una **ecuación lineal** en $n$ variables $x_1, x_2, \dots, x_n$ tiene la forma:
    $a_1x_1 + a_2x_2 + \dots + a_nx_n = b$
    donde $a_1, \dots, a_n$ (coeficientes) y $b$ (término independiente) son constantes.
*   **Interpretación Geométrica:**
    *   1 variable ($ax=b$): Un punto en la recta real (si $a \neq 0$).
    *   2 variables ($ax+by=c$): Una recta en el plano R².
    *   3 variables ($ax+by+cz=d$): Un plano en el espacio R³.

## 2. Sistemas de Ecuaciones Lineales (SEL)

*   Un **sistema de $n$ ecuaciones lineales con $m$ incógnitas** es un conjunto de $n$ ecuaciones lineales que deben satisfacerse simultáneamente:
    ```
    a₁₁x₁ + a₁₂x₂ + ... + a₁ₘxₘ = b₁
    a₂₁x₁ + a₂₂x₂ + ... + a₂ₘxₘ = b₂
    ...
    aₙ₁x₁ + aₙ₂x₂ + ... + aₙₘxₘ = bₙ
    ```
*   **Sistema Homogéneo:** Un SEL es homogéneo si todos los términos independientes son cero ($b_1 = b_2 = \dots = b_n = 0$).
*   **Interpretación Geométrica:** La solución de un SEL corresponde a la intersección de los objetos geométricos representados por cada ecuación (rectas en R², planos en R³, etc.).

## 3. Tipos de Soluciones de un SEL

Un SEL puede tener:

1.  **Solución Única:** Existe exactamente una combinación de valores para las incógnitas que satisface todas las ecuaciones.
    *   **Clasificación:** Sistema Compatible Determinado (SCD).
    *   *Geometría (2x2):* Dos rectas que se cortan en un punto.
2.  **Infinitas Soluciones:** Existe un número infinito de combinaciones de valores para las incógnitas que satisfacen todas las ecuaciones.
    *   **Clasificación:** Sistema Compatible Indeterminado (SCI).
    *   *Geometría (2x2):* Dos rectas coincidentes (la misma recta).
3.  **Ninguna Solución:** No existe ninguna combinación de valores para las incógnitas que satisfaga todas las ecuaciones simultáneamente.
    *   **Clasificación:** Sistema Incompatible (SI).
    *   *Geometría (2x2):* Dos rectas paralelas distintas.

## 4. Representaciones Matriciales de un SEL

Un SEL $a_{11}x_1 + \dots + a_{1m}x_m = b_1, \dots, a_{n1}x_1 + \dots + a_{nm}x_m = b_n$ se puede representar como:

1.  **Forma Matricial:** $A \vec{x} = \vec{b}$
    *   $A = \begin{pmatrix} a_{11} & \dots & a_{1m} \\ \vdots & \ddots & \vdots \\ a_{n1} & \dots & a_{nm} \end{pmatrix}$ (Matriz de coeficientes, $n \times m$)
    *   $\vec{x} = \begin{pmatrix} x_1 \\ \vdots \\ x_m \end{pmatrix}$ (Vector de incógnitas, $m \times 1$)
    *   $\vec{b} = \begin{pmatrix} b_1 \\ \vdots \\ b_n \end{pmatrix}$ (Vector de términos independientes, $n \times 1$)

2.  **Matriz Ampliada (o Aumentada):** Se añade el vector $\vec{b}$ como una columna adicional a la matriz $A$.
    *   $(A | \vec{b}) = \begin{pmatrix} a_{11} & \dots & a_{1m} & | & b_1 \\ \vdots & \ddots & \vdots & | & \vdots \\ a_{n1} & \dots & a_{nm} & | & b_n \end{pmatrix}$

3.  **Forma Vectorial:** El sistema $A\vec{x} = \vec{b}$ es equivalente a expresar el vector $\vec{b}$ como una combinación lineal de las columnas de $A$, donde las incógnitas $x_1, \dots, x_m$ son los escalares de la combinación.
    *   $x_1 \vec{c_1} + x_2 \vec{c_2} + \dots + x_m \vec{c_m} = \vec{b}$
    *   Donde $\vec{c_j}$ es la j-ésima columna de $A$.
    *   Resolver el sistema equivale a encontrar si $\vec{b}$ es combinación lineal de las columnas de $A$ y, si lo es, encontrar los coeficientes $x_i$.

## 5. Métodos de Resolución de SEL

### 5.1. Regla de Cramer (Solo para sistemas $n \times n$)

*   Aplicable solo si la matriz de coeficientes $A$ es cuadrada ($n=m$) y $\det(A) \neq 0$.
*   **Solución Única:** Si $\det(A) \neq 0$, la solución es única y viene dada por:
    $x_i = \frac{\det(A_i)}{\det(A)}$ para $i = 1, \dots, n$.
    Donde $A_i$ es la matriz obtenida al reemplazar la columna $i$ de $A$ por el vector $\vec{b}$.
*   **Análisis si $\det(A) = 0$:**
    *   Si **todos** los $\det(A_i) = 0$ para $i=1, \dots, n \implies$ Sistema Compatible Indeterminado (SCI).
    *   Si **al menos un** $\det(A_i) \neq 0 \implies$ Sistema Incompatible (SI).

### 5.2. Método de Gauss-Jordan (General)

*   **Idea:** Transformar el sistema original $A\vec{x} = \vec{b}$ en un sistema equivalente $E\vec{x} = \vec{d}$ que sea más fácil de resolver (idealmente, $E$ es una matriz escalonada o escalonada reducida). Esto se hace trabajando con la matriz ampliada $(A|\vec{b})$.
*   **Operaciones Elementales entre Filas:** Son operaciones que no cambian el conjunto solución del sistema:
    1.  Intercambiar dos filas ($F_i \leftrightarrow F_j$).
    2.  Multiplicar una fila por un escalar no nulo ($k F_i \to F_i$, con $k \neq 0$).
    3.  Sumar a una fila un múltiplo escalar de otra fila ($F_i + k F_j \to F_i$).
*   **Proceso:** Aplicar operaciones elementales a la matriz ampliada $(A|\vec{b})$ hasta obtener una forma escalonada $(E|\vec{d})$.
*   **Forma Escalonada:** Una matriz está escalonada si:
    1.  Las filas nulas (si las hay) están al final.
    2.  El **pivote** (primer elemento no nulo de izquierda a derecha) de cada fila está a la derecha del pivote de la fila superior.
    3.  Todos los elementos debajo de un pivote son cero.
*   **Forma Escalonada Reducida:** Es una forma escalonada donde, además:
    1.  Todos los pivotes son iguales a 1.
    2.  Todos los elementos *encima* de cada pivote también son cero.
*   **Resolución:** Una vez obtenida la forma escalonada $(E|\vec{d})$, el sistema $E\vec{x} = \vec{d}$ se resuelve fácilmente por **sustitución hacia atrás**.

## 6. Teorema de Rouché-Frobenius (Análisis de Compatibilidad)

Este teorema relaciona el rango de la matriz de coeficientes $A$ y el rango de la matriz ampliada $(A|\vec{b})$ con el tipo de solución del sistema $A\vec{x} = \vec{b}$ (con $m$ incógnitas).

*   **Condición de Compatibilidad:** El sistema $A\vec{x} = \vec{b}$ es **compatible** (tiene al menos una solución) si y solo si $rg(A) = rg(A|\vec{b})$.
    *   Equivalentemente: si $\vec{b}$ es combinación lineal de las columnas de $A$.

*   **Clasificación de Soluciones (si es compatible):**
    *   Si $rg(A) = rg(A|\vec{b}) = m$ (número de incógnitas) $\implies$ **Solución Única** (SCD).
    *   Si $rg(A) = rg(A|\vec{b}) = k < m$ (número de incógnitas) $\implies$ **Infinitas Soluciones** (SCI). El número de parámetros (variables libres) será $m-k$.

*   **Condición de Incompatibilidad:** El sistema $A\vec{x} = \vec{b}$ es **incompatible** (no tiene solución) si y solo si $rg(A) < rg(A|\vec{b})$. (Esto ocurre cuando al escalonar aparece una fila de la forma $(0 \ 0 \ \dots \ 0 \ | \ d)$ con $d \neq 0$).



## 7. Solución de Sistemas Compatibles Indeterminados

*   Cuando $rg(A) = rg(A|\vec{b}) = k < m$, el sistema tiene infinitas soluciones.
*   Habrá $k$ **variables pivote** (correspondientes a las columnas con pivotes en la forma escalonada) y $m-k$ **variables libres**.
*   Se asignan parámetros (ej. $s, t, \dots$) a las variables libres.
*   Se expresan las variables pivote en función de estos parámetros usando el sistema escalonado.
*   La solución general se escribe como un vector que es la suma de una **solución particular** (obtenida haciendo los parámetros cero) y una combinación lineal de vectores asociados a cada parámetro (que forman la solución del sistema homogéneo asociado).
    *   Ejemplo: $\vec{x} = \vec{p} + s \vec{u} + t \vec{v}$

## 8. Relación con Combinaciones Lineales

*   Determinar si un vector $\vec{v}$ es combinación lineal de otros vectores $\{\vec{v_1}, \dots, \vec{v_m}\}$ es equivalente a resolver el sistema $A\vec{x} = \vec{v}$, donde las columnas de $A$ son los vectores $\vec{v_1}, \dots, \vec{v_m}$.
*   $\vec{v}$ es combinación lineal de $\{\vec{v_1}, \dots, \vec{v_m}\}$ si y solo si el sistema $A\vec{x} = \vec{v}$ es **compatible** ($rg(A) = rg(A|\vec{v})$).
*   Si es compatible determinado, la combinación lineal es única.
*   Si es compatible indeterminado, existen infinitas formas de escribir $\vec{v}$ como combinación lineal.

## 9. Teorema de Equivalencias para Matrices Cuadradas

Para una matriz $A$ de orden $n \times n$, las siguientes afirmaciones son equivalentes:

1.  $A$ es inversible (existe $A^{-1}$).
2.  $\det(A) \neq 0$.
3.  El sistema $A\vec{x} = \vec{b}$ tiene **solución única** para cualquier $\vec{b}$.
4.  El sistema homogéneo $A\vec{x} = \vec{0}$ tiene **solo la solución trivial** ($\vec{x} = \vec{0}$).
5.  $rg(A) = n$ (rango completo).
6.  Las filas (o columnas) de $A$ forman un conjunto linealmente independiente.
7.  La forma escalonada reducida de $A$ es la matriz identidad $I_n$.
