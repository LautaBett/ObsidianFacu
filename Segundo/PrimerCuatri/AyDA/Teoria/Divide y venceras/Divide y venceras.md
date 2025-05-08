## Resumen del Documento: Técnicas de Diseño de Algoritmos

El documento "Técnicas de diseño de algoritmos" por Liliana Favre, para el curso de Análisis y Diseño de Algoritmos 1-2025, presenta una introducción a diversas metodologías para la construcción de soluciones algorítmicas.

### Metodología General

La construcción de soluciones algorítmicas sigue un proceso que puede involucrar:

- Abstracción de datos y procedural.
- Creación de un algoritmo informal.
- Implementación (ej. en C++).
- Análisis de eficiencia.
- Uso de Tipos de Datos Abstractos (TDA).

El documento se centra en tres técnicas principales de diseño de algoritmos:

---

### 1. Divide y Conquista (Divide and Conquer)

Esta técnica se basa en los siguientes pasos:

1. **Caso Base**: Si la instancia del problema es simple, se resuelve directamente.
2. **División**: Si no es simple, se divide el problema en k subproblemas más pequeños (X1​,X2​,...,Xk​).
3. **Conquista**: Se resuelven los subproblemas recursivamente.
4. **Combinación**: Las soluciones de los subproblemas se combinan para formar la solución del problema original.

**Esquema Algorítmico D&C**:

```
tipoResultado DivideyConquista (tipoDato X) {
    tipoDato x1, x2, ..., xk;
    if (simple(x)) {
        return soluciónDirecta(x);
    } else {
        x1 = Parte1(x);
        x2 = Parte2(x);
        ...
        xk = Partek(x);
        return Combinar(DivideyConquista(x1), DivideyConquista(x2), ..., DivideyConquista(xk));
    }
}
// Si k=1, se denomina esquema de reducción.
```

**Consideraciones Clave**:

- La solución se obtiene combinando soluciones de subproblemas idénticos al original.
- No se resuelve el mismo subproblema más de una vez (en el contexto de D&C puro, aunque Programación Dinámica aborda esto explícitamente para subproblemas superpuestos).
- El tamaño de las entradas de los subproblemas es una fracción del original.
- Para eficiencia, se buscan problemas balanceados y funciones de división y combinación eficientes.

**Ejemplos Clásicos**:

- **Torres de Hanoi**: k=2 subproblemas, complejidad O(2n).
- **Búsqueda Binaria**: k=1 (reducción), complejidad O(log2​m).
- **Ordenamiento Mergesort**: Divide la lista, ordena recursivamente las mitades y luego las intercala. Complejidad O(nlogn).
    - La intercalación (merge) de dos sub-arreglos ordenados de tamaño n/2 toma tiempo O(n).
- **Problema de Inversión (Máximo Sub-arreglo)**: Encontrar el sub-arreglo de un arreglo de diferencias de precios de acciones que tenga la suma máxima, lo que indica el mejor momento para comprar y vender. Un algoritmo ingenuo es O(n2). Con Divide y Conquista, se puede mejorar a O(nlogn).
    - Se divide el arreglo en dos mitades. La solución puede estar enteramente en la mitad izquierda, enteramente en la derecha, o cruzar el punto medio.
    - La "Solución Media" implica encontrar el máximo sub-arreglo que termina en la mitad y el máximo que comienza después de la mitad, y sumarlos.

**Limitación de Divide y Conquista**:

- No es eficiente si los subproblemas se superponen y se recalculan múltiples veces, como en el caso de la secuencia de Fibonacci calculada recursivamente de forma directa (O(2n)). Una versión iterativa o con memoización (Programación Dinámica) es O(n).

---

### 2. Algoritmos Voraces (Greedy Algorithms)

Estos algoritmos toman decisiones localmente óptimas en cada paso con la esperanza de encontrar una solución global óptima.

Características:

- Se busca un subconjunto de entradas que satisfaga ciertas restricciones (solución factible).
- Se quiere maximizar o minimizar una función objetivo.
- La solución que logra esto es la solución óptima.
- Suelen ser sencillos de diseñar pero no siempre garantizan la solución óptima.
- Cuando garantizan la optimalidad, se les asocia una prueba.
- A menudo requieren un pre-procesamiento de las entradas (ej. ordenar).

**Ejemplos**:

- **Programación de Tareas**: Minimizar el tiempo total de espera de n clientes, conociendo el tiempo de servicio ti​ de cada uno. La estrategia óptima es procesar a los clientes en orden creciente de sus tiempos de servicio.
    - Por ejemplo, si los tiempos son t1​=5,t2​=10,t3​=3.
        - Orden <1,2,3> (5, 10, 3): Espera = 5+(5+10)+(5+10+3)=5+15+18=38.
        - Orden <3,1,2> (3, 5, 10): Espera = 3+(3+5)+(3+5+10)=3+8+18=29. (El ejemplo del PDF muestra <1,3,2> como óptimo para los datos que usa)
- **Problema de la Mochila (Fraccional)**: Dados n objetos con pesos pi​ y beneficios bi​, y una mochila de capacidad M. Se pueden tomar fracciones xi​ de los objetos. El objetivo es maximizar el beneficio total ∑bi​xi​ sujeto a ∑pi​xi​≤M.
    - La estrategia Greedy óptima es ordenar los objetos de forma descendente según su relación beneficio/peso (bi​/pi​) y llenar la mochila en ese orden.
- **Ordenamiento Secuencial de Tareas con Plazos**: n tareas, cada una toma una unidad de tiempo. Cada tarea i tiene una ganancia gi​ si se completa antes de su plazo di​. Se busca un subconjunto de tareas J que sea factible (todas se completan a tiempo) y maximice ∑i∈J​gi​.
    - Estrategia Greedy: Considerar las tareas ordenadas descendentemente por ganancias. Agregar una tarea a la solución J si J permanece factible.
    - Determinar si J es factible implica poder programar las tareas de J tal que cada una cumpla su plazo. Una forma es ordenar las tareas en J por sus plazos.
    - La complejidad puede ser O(n2) si la verificación de factibilidad es O(n) en cada paso, o O(nlogn) si se usan estructuras de datos más avanzadas (como Union-Find) para la factibilidad.

---

### 3. Programación Dinámica

Esta técnica resuelve problemas combinando soluciones de subproblemas que se superponen.

Características:

- Se aplica cuando los subproblemas no son independientes (se usan para resolver múltiples problemas mayores). Divide y Conquista sería ineficiente aquí debido a recálculos.
- Se resuelven subproblemas desde las instancias más pequeñas hacia las más grandes.
- Las soluciones óptimas de subproblemas se usan para encontrar la solución óptima del problema general (propiedad de subestructura óptima).
- Los resultados parciales se almacenan (memoización o tabulación) para ser reutilizados.

**Pasos Generales**:

1. Dividir el problema en subproblemas más pequeños.
2. Encontrar la solución óptima a estos subproblemas.
3. Usar estas soluciones óptimas para construir la solución óptima al problema original.

**Ejemplos**:

- **Multiplicación Encadenada de Matrices**: Dadas n matrices M1​,M2​,...,Mn​, donde Mi​ tiene dimensión di−1​×di​. Se busca el orden de multiplicación que minimice el número total de productos escalares.
    - El número de productos escalares para multiplicar (Ap×q​)×(Bq×r​) es p×q×r.
    - Sea mij​ el costo mínimo para multiplicar Mi​×...×Mj​.
        - mii​=0.
        - mij​=mini≤k<j​{mik​+m(k+1)j​+di−1​dk​dj​}.
    - Se llena una tabla de costos de manera ascendente por la longitud de la cadena de matrices.
- **Árboles Binarios de Búsqueda de Mínimo Costo (Variación con Hojas Fijas)**: Dada una secuencia de valores V=V1​,...,Vn​ que serán las hojas de un árbol binario. Cada nodo interno contiene la suma de los valores de sus hijos. Se busca el árbol que minimiza la suma de los valores de todos los nodos (internos y hojas, o solo internos según la interpretación). El documento parece enfocarse en minimizar la suma de los nodos internos, dado que las hojas son fijas.
    - Sea Ci,k​ el costo del árbol óptimo para la subsecuencia de hojas Vi​,...,Vk​.
    - Sea Wi,k​=∑j=ik​Vj​ la suma de los valores en la subsecuencia.
    - Ci,i​=0 (costo de un subárbol con una sola hoja es 0, ya que no tiene nodos internos o el costo es solo el valor de la hoja que no se considera en Ci,j​ para esta formulación).
    - Ci,k​=mini≤j<k​{Ci,j​+Cj+1,k​+Wi,k​}. (Aquí Wi,k​ es el valor del nodo raíz del subárbol Vi​...Vk​).
- **Decidibilidad de Lenguajes Libres de Contexto (Algoritmo CYK)**: Determinar si una cadena x=x1​x2​...xn​ pertenece a un lenguaje generado por una gramática libre de contexto G en Forma Normal de Chomsky (FNC).
    - En FNC, las reglas son de la forma A→BC o A→a.
    - Sea Mji​ el conjunto de no terminales que pueden generar la subcadena de x de longitud j comenzando en xi​.
    - M1i​={A∣(A→xi​)∈P}.
    - Mji​=⋃1≤k<j​{A∣(A→BC)∈P y B∈Mki​ y C∈M(j−k)(i+k)​}.
    - La cadena x pertenece al lenguaje si el símbolo inicial S∈Mn1​.
- **Triangulación de un Polígono Convexo**: Dividir un polígono convexo de n vértices en n−2 triángulos usando n−3 diagonales que no se intersecten, de manera que la suma de las longitudes (costos) de estas diagonales sea mínima.
    - El número de triangulaciones es el número de Catalan Cn−2​.
    - Sea Cij​ el costo de la triangulación óptima del polígono formado por los vértices vi​,vi+1​,...,vj​.
    - Si se elige una diagonal (vi​,vk​) y (vk​,vj​) para formar un triángulo (vi​,vk​,vj​), el costo es Cik​+Ckj​+costo(vi​,vk​)+costo(vk​,vj​). (La formulación exacta varía, a veces se considera el costo de los lados del polígono o solo las diagonales internas).
    - El documento presenta una generalización donde Sij​ es el subproblema con j vértices a partir de vi​. La recurrencia parece ser: Ci,s​=min1≤k<s−1​{Ci,k+1​+Ci+k,s−k​+D(vi​,vi+k​)+D(vi+k​,vi+s−1​)}, donde D(va​,vb​) es la distancia. (La formulación del PDF para S06​ involucra C0,k​+Ck,s−k​+costos de diagonales que forman el primer triaˊngulo con v0​,vk​,vs−1​).
