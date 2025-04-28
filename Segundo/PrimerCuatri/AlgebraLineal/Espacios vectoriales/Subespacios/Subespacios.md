
### Resumen de la Nota [[Espacios Vectoriales]] sobre Subespacios

Tu nota introduce los conceptos fundamentales de los espacios vectoriales, comenzando con $\mathbb{R}^2$ y generalizando a cualquier conjunto $V$ con escalares $K$ que cumpla las 8 propiedades axiomáticas (S1-S4 para la suma, P1-P4 para el producto por escalar).

La idea de **subespacio** aparece directamente en la **Sección 4: Combinaciones Lineales y Subespacio Generado**:

1.  **Combinación Lineal:** Es la operación fundamental de formar un nuevo vector sumando vectores multiplicados por escalares: $\alpha_1 v_1 + \alpha_2 v_2 + \dots + \alpha_k v_k$. El resultado siempre pertenece al mismo espacio vectorial $V$.
2.  **Subespacio Generado (Span):** Se define como el conjunto de *todas las posibles* combinaciones lineales que se pueden formar a partir de un conjunto de vectores $\{v_1, \dots, v_k\}$. Se denota $\langle v_1, \dots, v_k \rangle$ o $span\{v_1, \dots, v_k\}$.
3.  **Propiedad Clave:** La nota afirma explícitamente que este conjunto $\langle v_1, \dots, v_k \rangle$ **es, en sí mismo, un espacio vectorial** (usando las mismas operaciones de $V$) y, por lo tanto, es un **subespacio** de $V$.

Aunque la nota no da una definición formal de subespacio más allá del "generado", sí introduce conceptos relacionados:

*   **Dependencia/Independencia Lineal (L.D./L.I.):** Determina si los vectores usados para generar el subespacio son "eficientes" (L.I.) o si hay redundancia (L.D.). Si son L.D., alguno de los vectores puede expresarse como combinación lineal de los otros y podría eliminarse sin cambiar el subespacio generado.
*   **Base y Dimensión:** Una base de un espacio (o subespacio) es un conjunto L.I. que lo genera. La dimensión es el número de vectores en cualquier base. Estos conceptos también aplican a los subespacios generados.

***

### Explicación Sencilla de Subespacios

Imagina que el **Espacio Vectorial** $V$ es como un gran universo donde viven los vectores y donde se cumplen ciertas reglas de movimiento (suma) y de tamaño (producto por escalar).

Un **Subespacio** $S$ es como un "universo más pequeño" o una "región especial" *dentro* de ese universo $V$. Para que una región $S$ sea considerada un subespacio, debe cumplir tres condiciones muy importantes:

1.  **No está vacío y contiene el "centro":** Debe contener al vector nulo $\vec{0}$ de $V$. Piensa en ello como que cualquier "región especial" debe incluir el origen.
2.  **Cerrado bajo la suma:** Si tomas dos vectores cualesquiera que vivan *dentro* de la región $S$ y los sumas (usando la regla de suma de $V$), el resultado *también debe caer dentro* de $S$. No te puedes "salir" de la región solo por sumar elementos que ya estaban dentro.
3.  **Cerrado bajo el producto por escalar:** Si tomas cualquier vector que viva *dentro* de $S$ y lo multiplicas por cualquier escalar (lo estiras, encoges o inviertes), el resultado *también debe permanecer dentro* de $S$. No te puedes "salir" de la región por escalar un elemento que ya estaba dentro.

**¿Por qué el "Subespacio Generado" $\langle v_1, \dots, v_k \rangle$ es un subespacio?**

Piensa en los vectores $v_1, \dots, v_k$ como los "ladrillos básicos" o las "direcciones fundamentales" de tu región especial.

*   El **subespacio generado** es el conjunto de *todos los puntos (vectores) a los que puedes llegar* partiendo del origen y moviéndote usando solo combinaciones de esas direcciones $v_1, \dots, v_k$ (es decir, haciendo $\alpha_1 v_1 + \dots + \alpha_k v_k$).

Este conjunto cumple automáticamente las tres reglas:

1.  **Contiene el $\vec{0}$:** Sí, solo tienes que elegir todos los escalares $\alpha_i = 0$. La combinación $0v_1 + \dots + 0v_k$ da $\vec{0}$.
2.  **Cerrado bajo suma:** Si tienes dos vectores en el subespacio generado, digamos $u = \alpha_1 v_1 + \dots + \alpha_k v_k$ y $w = \beta_1 v_1 + \dots + \beta_k v_k$, su suma es $u+w = (\alpha_1+\beta_1)v_1 + \dots + (\alpha_k+\beta_k)v_k$. ¡Esto sigue siendo una combinación lineal de $v_1, \dots, v_k$! Por lo tanto, $u+w$ también está en el subespacio generado.
3.  **Cerrado bajo producto por escalar:** Si tienes $u = \alpha_1 v_1 + \dots + \alpha_k v_k$ y un escalar $\lambda$, entonces $\lambda u = (\lambda\alpha_1)v_1 + \dots + (\lambda\alpha_k)v_k$. ¡Esto también es una combinación lineal de $v_1, \dots, v_k$! Por lo tanto, $\lambda u$ está en el subespacio generado.

**Ejemplos Geométricos en $\mathbb{R}^3$ (el espacio 3D):**

*   El espacio $\mathbb{R}^3$ completo es un espacio vectorial (y técnicamente, un subespacio de sí mismo).
*   Un **plano que pasa por el origen (0,0,0)** es un subespacio de $\mathbb{R}^3$. Si sumas dos vectores en el plano, te quedas en el plano. Si escalas un vector del plano, te quedas en el plano. Y contiene el origen. Por ejemplo, el plano generado por $\langle (1,0,0), (0,1,0) \rangle$ (el plano XY).
*   Una **recta que pasa por el origen (0,0,0)** es un subespacio de $\mathbb{R}^3$. Cumple las mismas condiciones. Por ejemplo, la recta generada por $\langle (1,1,1) \rangle$.
*   El conjunto que contiene **únicamente al vector $\vec{0} = (0,0,0)$** es el subespacio más pequeño posible, llamado subespacio trivial $\{\vec{0}\}$.
*   **Importante:** Un plano o una recta que *no* pasen por el origen *no* son subespacios, porque no cumplen la condición 1 (no contienen el $\vec{0}$).

En resumen, un subespacio es una parte de un espacio vectorial que hereda su estructura y se comporta como un espacio vectorial por sí mismo. La forma más común de construirlos es tomando todas las combinaciones lineales de un conjunto de vectores (el subespacio generado).