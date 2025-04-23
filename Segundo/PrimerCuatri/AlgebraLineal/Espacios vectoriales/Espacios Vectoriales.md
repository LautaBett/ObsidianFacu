# <span style="color:blue;">Álgebra Lineal: Espacios Vectoriales, Dependencia Lineal y Bases</span>

## <span style="color:green;">1. Introducción: Operaciones con Vectores en $\mathbb{R}^2$</span>

Empecemos con lo básico en el plano $\mathbb{R}^2$ (el conjunto de todos los pares de números reales como $(x, y)$).

*   **Vectores:** Son como flechas con dirección y magnitud. Los representamos como pares ordenados, por ejemplo, $\mathbf{v} = (v_1, v_2)$.
*   **Escalares:** Son simplemente números reales (como 3, -1.5, $\pi$). Los usamos para "escalar" (estirar o encoger) vectores. Usaremos la letra griega $\lambda$ (lambda) para representarlos.

Dados dos vectores $\mathbf{v} = (v_1, v_2), \mathbf{u} = (u_1, u_2)$ y un escalar $\lambda$:

*   **<span style="color:purple;">Suma de vectores:</span>** Se suman componente a componente.
    $\mathbf{v} + \mathbf{u} = (v_1, v_2) + (u_1, u_2) = (v_1 + u_1, v_2 + u_2)$
    *(Piensa en poner una flecha a continuación de la otra).*
*   **<span style="color:purple;">Producto por escalar:</span>** Se multiplica cada componente por el escalar.
    $\lambda \mathbf{v} = \lambda (v_1, v_2) = (\lambda v_1, \lambda v_2)$
    *(Esto estira o encoge la flecha, y si $\lambda$ es negativo, invierte su dirección).*

Estas dos operaciones ($\langle \mathbb{R}^2, +, \cdot \rangle$) cumplen ciertas reglas o propiedades que son fundamentales.

### <span style="color:teal;">Propiedades (¡Las reglas del juego!)</span>

Estas propiedades nos dicen cómo se comportan la suma y el producto por escalar. Son bastante intuitivas:

**<span style="color:darkorange;">Propiedades de la Suma (entre vectores):</span>**

*   **S1 (Asociativa):** No importa cómo agrupes al sumar tres vectores: $\mathbf{u} + (\mathbf{v} + \mathbf{w}) = (\mathbf{u} + \mathbf{v}) + \mathbf{w}$.
*   **S2 (Conmutativa):** El orden no importa al sumar: $\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}$.
*   **S3 (Elemento Neutro):** Existe un vector especial, el $\vec{0} = (0, 0)$, que no cambia nada al sumarlo: $\mathbf{v} + \vec{0} = \mathbf{v}$.
*   **S4 (Inverso Aditivo):** Todo vector $\mathbf{v}$ tiene un "opuesto" $-\mathbf{v}$ tal que al sumarlos dan el vector cero: $\mathbf{v} + (-\mathbf{v}) = \vec{0}$. (Si $\mathbf{v}=(v_1, v_2)$, entonces $-\mathbf{v}=(-v_1, -v_2)$).

**<span style="color:darkorange;">Propiedades del Producto por Escalar (mezcla escalares y vectores):</span>**

*   **P1 (Asociativa):** Multiplicar escalares primero o después da lo mismo: $(\lambda \beta) \cdot \mathbf{v} = \lambda \cdot (\beta \cdot \mathbf{v})$.
*   **P2 (Neutro Multiplicativo):** Multiplicar por el escalar $1$ no cambia el vector: $1 \cdot \mathbf{v} = \mathbf{v}$.
*   **P3 (Distributiva I):** Puedes distribuir un vector sobre una suma de escalares: $(\lambda + \beta) \cdot \mathbf{v} = (\lambda \cdot \mathbf{v}) + (\beta \cdot \mathbf{v})$.
*   **P4 (Distributiva II):** Puedes distribuir un escalar sobre una suma de vectores: $\lambda \cdot (\mathbf{u} + \mathbf{v}) = (\lambda \cdot \mathbf{u}) + (\lambda \cdot \mathbf{v})$.

---

## <span style="color:green;">2. Espacios Vectoriales: La Generalización</span>

La idea clave es que las propiedades que vimos para $\mathbb{R}^2$ son tan útiles que las usamos para definir una estructura más general llamada **Espacio Vectorial**.

### <span style="color:teal;">Definición Formal</span>

Un **Espacio Vectorial** es un conjunto $V$ (cuyos elementos llamamos *vectores*) junto con un conjunto $K$ (cuyos elementos llamamos *escalares*, usualmente los números reales $\mathbb{R}$ o complejos $\mathbb{C}$, que forman un "cuerpo") y dos operaciones (una suma de vectores $+$ y un producto por escalar $*$) que cumplen **exactamente las mismas 8 propiedades** que vimos antes (S1-S4 y P1-P4).

Lo escribimos como $\langle V, +, * \rangle$.

**<span style="color:darkorange;">Axiomas de la Suma (Grupo Abeliano):</span>** (Las mismas S1-S4 de antes)
*   **S1 (Asociativa):** $\vec{u} + (\vec{v} + \vec{w}) = (\vec{u} + \vec{v}) + \vec{w}$
*   **S2 (Conmutativa):** $\vec{u} + \vec{v} = \vec{v} + \vec{u}$
*   **S3 (Elemento Neutro):** Existe $\vec{0} \in V$ tal que $\vec{v} + \vec{0} = \vec{v}$.
*   **S4 (Elemento Inverso):** Para cada $\vec{v} \in V$, existe $-\vec{v} \in V$ tal que $\vec{v} + (-\vec{v}) = \vec{0}$.

**<span style="color:darkorange;">Axiomas del Producto por Escalar:</span>** (Las mismas P1-P4 de antes, usando $*$ para el producto)
*   **P1 (Identidad Multiplicativa):** $1 * \vec{v} = \vec{v}$ (donde $1$ es el neutro multiplicativo de $K$).
*   **P2 (Asociatividad Mixta):** $(\lambda * \beta) * \vec{v} = \lambda * (\beta * \vec{v})$
*   **P3 (Distributiva I):** $\lambda * (\vec{u} + \vec{v}) = (\lambda * \vec{u}) + (\lambda * \vec{v})$
*   **P4 (Distributiva II):** $(\lambda + \beta) * \vec{v} = (\lambda * \vec{v}) + (\beta * \vec{v})$

**¿Por qué es útil?** Porque muchos conjuntos diferentes (no solo $\mathbb{R}^n$) se comportan de esta manera. Si demostramos algo usando solo estas 8 propiedades, ¡será válido para *todos* los espacios vectoriales!

### <span style="color:teal;">Comentarios Importantes</span>

*   **Vectores vs. Escalares:** Los vectores viven en $V$, los escalares en $K$. Solo podemos sumar vectores con vectores y escalares con escalares. El producto por escalar mezcla uno de cada uno.
*   **Abuso de Notación:** A menudo usamos el mismo símbolo $+$ para la suma de vectores y la suma de escalares, y omitimos el $*$ del producto por escalar (escribimos $\lambda \vec{v}$ en lugar de $\lambda * \vec{v}$). Se entiende por el contexto.
*   **Nuestro Foco:** En general, trabajaremos con $K = \mathbb{R}$ (escalares reales).

---

## <span style="color:green;">3. Ejemplos de Espacios Vectoriales</span>

### <span style="color:teal;">Ejemplo 1: $\mathbb{R}^n$ (Generalización de $\mathbb{R}^2$)</span>

*   **Conjunto V:** $\mathbb{R}^n$, el conjunto de n-tuplas (listas ordenadas de $n$ números reales).
*   **Vectores:** $(x_1, x_2, \dots, x_n)$.
*   **Escalares K:** $\mathbb{R}$.
*   **Suma:** $(x_1, \dots, x_n) + (y_1, \dots, y_n) = (x_1 + y_1, \dots, x_n + y_n)$ (componente a componente).
*   **Producto por escalar:** $\lambda (x_1, \dots, x_n) = (\lambda x_1, \dots, \lambda x_n)$ (multiplica cada componente).
*   Se puede verificar que cumple las 8 propiedades. $\mathbb{R}^2$ y $\mathbb{R}^3$ son los casos más familiares.

### <span style="color:teal;">Ejemplo 2: Polinomios $P_n[X]$</span>

*   **Conjunto V:** $P_n[X]$, el conjunto de todos los polinomios con coeficientes reales de grado *menor o igual* que $n$, más el polinomio cero.
*   **Vectores:** Polinomios como $P(x) = a_n x^n + \dots + a_1 x + a_0$.
*   **Escalares K:** $\mathbb{R}$.
*   **Suma:** La suma usual de polinomios (sumar coeficientes del mismo grado).
    Si $P(x) = \sum a_i x^i$ y $Q(x) = \sum b_i x^i$, entonces $P(x) + Q(x) = \sum (a_i + b_i) x^i$.
*   **Producto por escalar:** Multiplicar cada coeficiente por el escalar.
    $\lambda P(x) = \sum (\lambda a_i) x^i$.
*   ¡También cumple las 8 propiedades! Esto muestra que los "vectores" no tienen por qué ser flechas o listas de números.

---

## <span style="color:green;">4. Combinaciones Lineales y Subespacio Generado</span>

Una idea central en espacios vectoriales es la **combinación lineal**.

*   **Combinación Lineal:** Es una suma de vectores, cada uno multiplicado por un escalar.
    Dados los vectores $v_1, v_2, \dots, v_k$ y los escalares $\alpha_1, \alpha_2, \dots, \alpha_k$, la expresión:
    $$ \alpha_1 v_1 + \alpha_2 v_2 + \dots + \alpha_k v_k $$
    es una combinación lineal de los vectores $v_1, \dots, v_k$. El resultado de esta operación es *siempre* otro vector dentro del mismo espacio vectorial $V$.

*   **Subespacio Generado (Span):** El conjunto de *todas* las posibles combinaciones lineales que puedes formar con un conjunto de vectores $\{v_1, \dots, v_k\}$ se llama el **subespacio generado** por ellos, y se denota como $\langle v_1, \dots, v_k \rangle$ o $span\{v_1, \dots, v_k\}$.
    *   Este conjunto $\langle v_1, \dots, v_k \rangle$ es, en sí mismo, un espacio vectorial (un "subespacio" de $V$).
    *   Decimos que $v \in \langle v_1, \dots, v_k \rangle$ si $v$ *se puede escribir* como combinación lineal de $v_1, \dots, v_k$.

*   **Conjunto Generador:** Si resulta que *todo* vector del espacio $V$ se puede escribir como combinación lineal de $\{v_1, \dots, v_k\}$, entonces decimos que $\{v_1, \dots, v_k\}$ es un **conjunto generador** de $V$. Es decir, $V = \langle v_1, \dots, v_k \rangle$.

---

## <span style="color:green;">5. Dependencia e Independencia Lineal</span>

Ahora nos preguntamos: ¿son necesarios todos los vectores de un conjunto $\{v_1, \dots, v_n\}$ para generar $\langle v_1, \dots, v_n \rangle$? ¿O hay alguna redundancia?

### <span style="color:teal;">Dependencia Lineal (L.D.)</span>

*   **Definición:** Un conjunto de vectores $\{v_1, \dots, v_n\}$ es **Linealmente Dependiente (L.D.)** si es posible encontrar escalares $\alpha_1, \dots, \alpha_n$, **donde al menos uno no sea cero**, tal que la combinación lineal dé el vector nulo:
    $$ \alpha_1 v_1 + \alpha_2 v_2 + \dots + \alpha_n v_n = \vec{0} $$
*   **Significado Intuitivo:** Si son L.D., significa que hay "redundancia". Al menos uno de los vectores se puede expresar como combinación lineal de los demás. ¡Es como tener una dirección repetida en un mapa!
*   **Equivalencia:** Un conjunto $\{v_1, \dots, v_n\}$ es L.D. si y solo si al menos uno de los vectores $v_j$ pertenece al subespacio generado por los otros: $v_j \in \langle \{v_i : i \neq j\} \rangle$.

#### <span style="color:purple;">Ejemplos L.D.</span>

1.  $\{(1, 0, 0), (0, 1, 0), (1, 1, 0)\}$ en $\mathbb{R}^3$. Son L.D. porque $(1, 1, 0)$ es la suma de los otros dos: $1 \cdot (1, 0, 0) + 1 \cdot (0, 1, 0) - 1 \cdot (1, 1, 0) = (0, 0, 0)$. Aquí $\alpha_1=1, \alpha_2=1, \alpha_3=-1$ (no todos cero).
2.  $\{(1, 0, 1), (2, 0, 2)\}$ en $\mathbb{R}^3$. Son L.D. porque el segundo es múltiplo del primero: $(2, 0, 2) = 2 \cdot (1, 0, 1)$. La combinación lineal que da cero es $2(1, 0, 1) - 1(2, 0, 2) = (0, 0, 0)$. Aquí $\alpha_1=2, \alpha_2=-1$.
    *   El subespacio generado es $\langle (1, 0, 1), (2, 0, 2) \rangle = \langle (1, 0, 1) \rangle$, que es una recta. El vector $(2, 0, 2)$ era redundante.

### <span style="color:teal;">Independencia Lineal (L.I.)</span>

*   **Definición:** Un conjunto de vectores $\{v_1, \dots, v_n\}$ es **Linealmente Independiente (L.I.)** si **NO** es L.D.
*   **Significado Formal:** La *única* forma de que la combinación lineal dé el vector nulo es que *todos* los escalares sean cero:
    $$ \alpha_1 v_1 + \alpha_2 v_2 + \dots + \alpha_n v_n = \vec{0} \quad \implies \quad \alpha_1 = \alpha_2 = \dots = \alpha_n = 0 $$
*   **Significado Intuitivo:** Si son L.I., significa que no hay redundancia. Cada vector aporta información "nueva" que no puede ser representada por los demás. Son como direcciones únicas y esenciales en un mapa.
*   **Equivalencia:** Un conjunto $\{v_1, \dots, v_n\}$ es L.I. si y solo si ningún vector $v_j$ se puede escribir como combinación lineal de los otros.

---

## <span style="color:green;">6. ¿Cómo Verificar si un Conjunto es L.I. o L.D.?</span>

La pregunta clave es: ¿La ecuación $\alpha_1 v_1 + \dots + \alpha_n v_n = \vec{0}$ tiene solo la solución $\alpha_1 = \dots = \alpha_n = 0$ (L.I.) o tiene otras soluciones donde algún $\alpha_i \neq 0$ (L.D.)?

### <span style="color:teal;">Método General: Sistemas de Ecuaciones Homogéneos</span>

1.  **Plantea la ecuación:** Escribe $\alpha_1 v_1 + \dots + \alpha_n v_n = \vec{0}$.
2.  **Convierte a sistema:** Si trabajas en $\mathbb{R}^m$, esta ecuación vectorial se convierte en un sistema de $m$ ecuaciones lineales con $n$ incógnitas ($\alpha_1, \dots, \alpha_n$). El sistema siempre será **homogéneo** (los términos independientes son todos cero).
3.  **Forma la matriz:** Escribe la matriz $A$ del sistema, donde las columnas son los vectores $v_1, \dots, v_n$. El sistema es $A \mathbf{x} = \vec{0}$, donde $\mathbf{x} = (\alpha_1, \dots, \alpha_n)^T$.
4.  **Analiza la solución:**
    *   Si la **única solución** es $\mathbf{x} = \vec{0}$ (la solución trivial $\alpha_1 = \dots = \alpha_n = 0$), entonces los vectores son **L.I.**
    *   Si existen **infinitas soluciones** (además de la trivial), entonces los vectores son **L.D.**

#### <span style="color:purple;">Ejemplo (Verificación L.I.)</span>

¿Es $\{(1, 0, 1), (1, 1, 1), (0, 1, 1)\}$ L.I. en $\mathbb{R}^3$?
1.  Ecuación: $\alpha_1(1, 0, 1) + \alpha_2(1, 1, 1) + \alpha_3(0, 1, 1) = (0, 0, 0)$
2.  Sistema:
    $1\alpha_1 + 1\alpha_2 + 0\alpha_3 = 0$
    $0\alpha_1 + 1\alpha_2 + 1\alpha_3 = 0$
    $1\alpha_1 + 1\alpha_2 + 1\alpha_3 = 0$
3.  Matriz: $A = \begin{pmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 1 & 1 \end{pmatrix}$
4.  Solución: Resolvemos $A\mathbf{x} = \vec{0}$ usando Gauss:
    $$ \begin{pmatrix} 1 & 1 & 0 & | & 0 \\ 0 & 1 & 1 & | & 0 \\ 1 & 1 & 1 & | & 0 \end{pmatrix} \sim \begin{pmatrix} 1 & 1 & 0 & | & 0 \\ 0 & 1 & 1 & | & 0 \\ 0 & 0 & 1 & | & 0 \end{pmatrix} $$
    El sistema escalonado tiene 3 pivotes (rango 3) y 3 incógnitas. La única solución es $\alpha_3=0 \implies \alpha_2=0 \implies \alpha_1=0$.
    **Conclusión:** El conjunto es **L.I.**

#### <span style="color:purple;">Ejemplo (Verificación L.D.)</span>

¿Es $\{(1, 1, 1), (-1, 0, 1), (2, 1, 0)\}$ L.D. en $\mathbb{R}^3$?
1.  Ecuación: $\alpha_1(1, 1, 1) + \alpha_2(-1, 0, 1) + \alpha_3(2, 1, 0) = (0, 0, 0)$
2.  Sistema:
    $1\alpha_1 - 1\alpha_2 + 2\alpha_3 = 0$
    $1\alpha_1 + 0\alpha_2 + 1\alpha_3 = 0$
    $1\alpha_1 + 1\alpha_2 + 0\alpha_3 = 0$
3.  Matriz: $A = \begin{pmatrix} 1 & -1 & 2 \\ 1 & 0 & 1 \\ 1 & 1 & 0 \end{pmatrix}$
4.  Solución: Resolvemos $A\mathbf{x} = \vec{0}$ usando Gauss:
    $$ \begin{pmatrix} 1 & -1 & 2 & | & 0 \\ 1 & 0 & 1 & | & 0 \\ 1 & 1 & 0 & | & 0 \end{pmatrix} \sim \begin{pmatrix} 1 & -1 & 2 & | & 0 \\ 0 & 1 & -1 & | & 0 \\ 0 & 0 & 0 & | & 0 \end{pmatrix} $$
    El sistema escalonado tiene solo 2 pivotes (rango 2) pero 3 incógnitas. Hay una variable libre, lo que significa **infinitas soluciones**.
    **Conclusión:** El conjunto es **L.D.**

### <span style="color:teal;">Método del Determinante (¡Atajo para Conjuntos Cuadrados!)</span>

Si estás en $\mathbb{R}^n$ y tienes exactamente $n$ vectores, puedes formar una matriz cuadrada $A$ con ellos. En este caso especial:

*   Calcula el determinante de $A$: $\det(A)$.
*   Si $\det(A) \neq 0 \implies$ Solución única para $A\mathbf{x}=\vec{0} \implies$ Los vectores son **L.I.**
*   Si $\det(A) = 0 \implies$ Infinitas soluciones para $A\mathbf{x}=\vec{0} \implies$ Los vectores son **L.D.**

#### <span style="color:purple;">Ejemplo 1 (L.I. con Determinante)</span>

Vectores: $\{(1, 0, 1), (0, 1, 1), (-1, 1, -1)\}$ (3 vectores en $\mathbb{R}^3$).
Matriz $A = \begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \\ 1 & 1 & -1 \end{pmatrix}$.
$\det(A) = -1 \neq 0$. **Conclusión:** Son **L.I.**

#### <span style="color:purple;">Ejemplo 2 (L.D. con Determinante)</span>

Vectores: $\{(1, 0, 1), (1, 1, 1), (-1, -1, -1)\}$ (3 vectores en $\mathbb{R}^3$).
Matriz $A = \begin{pmatrix} 1 & 1 & -1 \\ 0 & 1 & -1 \\ 1 & 1 & -1 \end{pmatrix}$.
$\det(A) = 0$. **Conclusión:** Son **L.D.**

**¡Cuidado!** Este método solo funciona si el número de vectores es igual a la dimensión del espacio (matriz cuadrada). Si tienes 2 vectores en $\mathbb{R}^3$, no puedes usar el determinante.

---

## <span style="color:green;">7. Identificando Vectores Redundantes (Descartar L.D.)</span>

Si un conjunto es L.D., ¿cómo sabemos cuáles vectores "sobran"? La eliminación Gaussiana nos ayuda.

#### <span style="color:purple;">Ejemplo</span>

Conjunto L.D.: $\{(1, 0, 1), (1, 1, -1), (2, 1, 0)\}$.
Matriz y forma escalonada:
$$ A = \begin{pmatrix} 1 & 1 & 2 \\ 0 & 1 & 1 \\ 1 & -1 & 0 \end{pmatrix} \sim \begin{pmatrix} \mathbf{1} & 1 & 2 \\ 0 & \mathbf{1} & 1 \\ 0 & 0 & 0 \end{pmatrix} $$
*   **Pivotes:** Las columnas que tienen pivotes (marcados en negrita, columnas 1 y 2) corresponden a los vectores del conjunto original que forman un subconjunto L.I. maximal: $\{(1, 0, 1), (1, 1, -1)\}$.
*   **Columnas sin pivote:** La columna que no tiene pivote (columna 3) corresponde al vector que es combinación lineal de los vectores asociados a los pivotes anteriores. En este caso, $(2, 1, 0)$ depende de los dos primeros.
*   **Relación de dependencia:** La forma escalonada nos dice cómo: la tercera columna $(2, 1)^T$ (mirando las filas con pivote) es $1 \times (\text{columna 1}) + 1 \times (\text{columna 2})$. Esto se traduce a los vectores originales: $(2, 1, 0) = 1 \cdot (1, 0, 1) + 1 \cdot (1, 1, -1)$.

---

## <span style="color:green;">8. Base y Dimensión: La Esencia de un Espacio Vectorial</span>

### <span style="color:teal;">Definición de Base</span>

Una **Base** de un espacio vectorial $V$ es un conjunto de vectores $\{v_1, \dots, v_n\}$ que cumple **dos condiciones simultáneamente**:

1.  **Genera V:** $V = \langle v_1, \dots, v_n \rangle$ (Todo vector en $V$ es combinación lineal de ellos).
2.  **Es Linealmente Independiente (L.I.):** No hay redundancia en el conjunto.

**Idea Clave:** Una base es el conjunto "mínimo" de vectores que necesitas para construir (generar) todo el espacio, sin desperdiciar vectores (sin dependencia lineal). Es como el conjunto mínimo de ladrillos LEGO diferentes que necesitas para poder construir cualquier figura posible dentro de un cierto sistema.

### <span style="color:teal;">Dimensión</span>

Un resultado fundamental del álgebra lineal es que:
*   **Todas las bases de un mismo espacio vectorial tienen el mismo número de vectores.**

Este número único se llama la **Dimensión** del espacio vectorial $V$, y se escribe $\dim(V)$.

*   $\dim(\mathbb{R}^2) = 2$ (La base canónica es $\{(1, 0), (0, 1)\}$).
*   $\dim(\mathbb{R}^3) = 3$ (La base canónica es $\{(1, 0, 0), (0, 1, 0), (0, 0, 1)\}$).
*   $\dim(\mathbb{R}^n) = n$.
*   $\dim(P_n[X]) = n+1$ (Una base es $\{1, x, x^2, \dots, x^n\}$).

### <span style="color:teal;">Observaciones Importantes</span>

*   Una base **siempre** genera el espacio.
*   Un conjunto generador **no siempre** es una base (podría ser L.D.). Para obtener una base a partir de un conjunto generador L.D., debes eliminar los vectores redundantes (usando Gauss, por ejemplo) hasta que te quedes con un conjunto L.I.
*   Un espacio vectorial tiene **infinitas bases** posibles, pero todas tienen el mismo tamaño (la dimensión).

---

## <span style="color:green;">9. Extensión a una Base</span>

Si tienes un conjunto de vectores L.I. en un espacio $V$ de dimensión $n$, pero tienes menos de $n$ vectores, siempre puedes **añadir más vectores** (elegidos cuidadosamente) para completar una base de $V$.

### <span style="color:teal;">Procedimiento (Ejemplo en $\mathbb{R}^3$)</span>

Supongamos que $\dim(V)=n$. Tenemos un conjunto L.I. $\{v_1, \dots, v_k\}$ con $k < n$. Queremos encontrar $v_{k+1}, \dots, v_n$ tal que $\{v_1, \dots, v_k, v_{k+1}, \dots, v_n\}$ sea una base de $V$.

**Ejemplo:** Extender $\{(1, 2, -1)\}$ a una base de $\mathbb{R}^3$ ($\dim=3$). Necesitamos añadir $3-1=2$ vectores.

1.  **Añadir un vector L.I.:** Elige un vector $v_2$ que *no* sea combinación lineal de $v_1$. Es decir, $v_2$ no debe ser múltiplo de $(1, 2, -1)$. Una opción fácil es $v_2 = (1, 0, 0)$. Ahora tenemos el conjunto L.I. $\{(1, 2, -1), (1, 0, 0)\}$.
2.  **Añadir otro vector L.I.:** Busca un $v_3 = (x, y, z)$ tal que $\{v_1, v_2, v_3\}$ sea L.I. Esto significa que $v_3$ *no* debe ser combinación lineal de $v_1$ y $v_2$. Ponemos los tres vectores como columnas de una matriz y buscamos que el rango sea 3 (o que el determinante sea no nulo).
    $$ A = \begin{pmatrix} 1 & 1 & x \\ 2 & 0 & y \\ -1 & 0 & z \end{pmatrix} $$
3.  **Verificar Independencia:** Calculamos $\det(A) = -(2z + y)$. Para que sean L.I., necesitamos $\det(A) \neq 0$, es decir, $2z + y \neq 0$.
4.  **Elegir un vector válido:** Cualquier $(x, y, z)$ que cumpla $2z + y \neq 0$ funciona. Por ejemplo, $v_3 = (0, 0, 1)$ cumple ($2(1)+0 = 2 \neq 0$). Otra opción válida es $v_3 = (1, 1, 1)$ ($2(1)+1 = 3 \neq 0$).
5.  **Base Completa:** Si elegimos $v_3 = (1, 1, 1)$, entonces $B = \{(1, 2, -1), (1, 0, 0), (1, 1, 1)\}$ es un conjunto L.I. con 3 vectores en $\mathbb{R}^3$. Por lo tanto, es una **base** de $\mathbb{R}^3$.
