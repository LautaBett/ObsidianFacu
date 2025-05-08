A continuación, te presento una guía detallada para resolver el práctico sobre "Técnicas de Diseño de Algoritmos: Divide y Conquista", utilizando como base la información y los conceptos del documento "CLASES TÉCNICAS DE DISEÑO- 2025.pdf" [cite: 1] que resumimos previamente.

**Nota Importante:** No puedo generar ni ejecutar código C++ directamente. Sin embargo, te proporcionaré la lógica detallada, el pseudocódigo o los pasos clave para implementar las soluciones en C++, basándome en los principios de "Divide y Conquista" explicados en el material de referencia.

---

## Resolución del Práctico: Técnicas de Diseño de Algoritmos: Divide y Conquista

### 1) Implementación de Mergesort y Quicksort

**Mergesort:**
El documento PDF proporciona una explicación detallada de Mergesort[cite: 15, 22, 31, 32, 38, 42]. La idea central es:
1.  **Dividir**: Si la lista tiene más de un elemento, divídela en dos sublistas de aproximadamente la mitad del tamaño.
2.  **Conquistar**: Ordena cada sublista recursivamente aplicando Mergesort.
3.  **Combinar**: Intercala (merge) las dos sublistas ordenadas en una sola lista ordenada. La función de intercalación es crucial y debe ser eficiente ($O(n)$)[cite: 19].

**Lógica para C++ (Mergesort):**
```cpp
// Función principal de Mergesort
void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        // Encuentra el punto medio
        int m = l + (r - l) / 2; // Evita overflow para l y r grandes

        // Ordena la primera y segunda mitad
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);

        // Combina las mitades ordenadas
        merge(arr, l, m, r);
    }
}

// Función para combinar dos subarreglos ordenados
// arr[l..m] y arr[m+1..r]
void merge(int arr[], int l, int m, int r) {
    // Crear arreglos temporales
    int n1 = m - l + 1;
    int n2 = r - m;
    int L[n1], R[n2];

    // Copiar datos a los arreglos temporales L[] y R[]
    for (int i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];

    // Intercalar los arreglos temporales de vuelta en arr[l..r]
    int i = 0; // Índice inicial del primer subarreglo
    int j = 0; // Índice inicial del segundo subarreglo
    int k = l; // Índice inicial del subarreglo combinado
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    // Copiar los elementos restantes de L[], si hay alguno
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    // Copiar los elementos restantes de R[], si hay alguno
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}
```
El PDF muestra un pseudocódigo similar y analiza su complejidad como $O(n \log n)$[cite: 22, 31, 38, 42, 45].

**Quicksort:**
Aunque no se detalla explícitamente en el PDF, Quicksort es un algoritmo fundamental de "Divide y Conquista"[cite: 3, 4, 7].
1.  **Dividir**: Escoge un elemento del arreglo como pivote. Reorganiza el arreglo de manera que todos los elementos menores que el pivote queden a su izquierda, y todos los elementos mayores queden a su derecha (partición). Tras la partición, el pivote está en su posición final ordenada.
2.  **Conquistar**: Ordena recursivamente los subarreglos a la izquierda y derecha del pivote.
3.  **Combinar**: No se necesita ninguna acción de combinación, ya que el ordenamiento se realiza "in-place" durante la partición y las llamadas recursivas.

**Lógica para C++ (Quicksort):**
```cpp
// Función para intercambiar dos elementos
void swap(int* a, int* b) {
    int t = *a;
    *a = *b;
    *b = t;
}

// Esta función toma el último elemento como pivote, coloca
// el pivote en su posición correcta en el arreglo ordenado,
// y coloca todos los menores (menores que el pivote)
// a la izquierda del pivote y todos los mayores a la derecha
int partition(int arr[], int low, int high) {
    int pivot = arr[high]; // pivote
    int i = (low - 1); // Índice del elemento más pequeño

    for (int j = low; j <= high - 1; j++) {
        // Si el elemento actual es menor o igual al pivote
        if (arr[j] <= pivot) {
            i++; // incrementa el índice del elemento más pequeño
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return (i + 1);
}

// Función principal de Quicksort
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        // pi es el índice de partición, arr[pi] está ahora en el lugar correcto
        int pi = partition(arr, low, high);

        // Ordena separadamente los elementos antes y después de la partición
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```
La complejidad promedio de Quicksort es $O(n \log n)$, y en el peor caso (con mala elección de pivotes y arreglo ya ordenado o inversamente ordenado) es $O(n^2)$.

---

### 2) Encontrar `i` tal que `T[i] = i` en un arreglo ordenado `T`

**a) Implementación del algoritmo ($O(\log n)$):**
Este problema se puede resolver utilizando una modificación de la búsqueda binaria, un ejemplo de "Divide y Conquista" por reducción[cite: 8, 10].
Dado que el arreglo `T` está ordenado y contiene enteros diferentes, si `T[mid] == mid`, hemos encontrado el índice.
* Si `T[mid] < mid`, significa que si existe un `T[i] = i`, debe estar en la parte derecha del arreglo (índices mayores que `mid`), porque los valores de `T` crecen más lento que los índices, o han "quedado atrás".
* Si `T[mid] > mid`, significa que si existe un `T[i] = i`, debe estar en la parte izquierda del arreglo (índices menores que `mid`), porque los valores de `T` crecen más rápido que los índices, o se han "adelantado".

**Lógica para C++:**
```cpp
int findIndexEqualsValue(int T[], int n) {
    int low = 0, high = n - 1;
    int result = -1; // En caso de que no se encuentre

    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (T[mid] == mid) {
            result = mid;
            // Podría haber múltiples, si se pide el primero, ajustar high = mid - 1
            // Si se pide cualquiera, se puede retornar aquí.
            // Para este problema, se asume que cualquier índice es válido.
            return result;
        } else if (T[mid] < mid) {
            low = mid + 1; // Buscar en la parte derecha
        } else { // T[mid] > mid
            high = mid - 1; // Buscar en la parte izquierda
        }
    }
    return result; // No se encontró tal índice
}
```
La complejidad es $O(\log n)$ porque en cada paso se reduce el espacio de búsqueda a la mitad, característico de la búsqueda binaria[cite: 13].

**b) Explicación de por qué una búsqueda binaria es esencial en grandes volúmenes de datos:**
La búsqueda binaria es esencial para grandes volúmenes de datos (nube, redes sociales, etc.) debido a su eficiencia logarítmica ($O(\log n)$).
* **Escalabilidad:** A medida que el tamaño de los datos (`n`) crece enormemente, el número de operaciones de una búsqueda lineal ($O(n)$) crece proporcionalmente, volviéndose inviable. En contraste, el número de operaciones para $O(\log n)$ crece muy lentamente. Por ejemplo:
    * Para $n = 1,000,000$, $\log_2 n \approx 20$.
    * Para $n = 1,000,000,000$, $\log_2 n \approx 30$.
    Esto significa que incluso para miles de millones de elementos, la búsqueda binaria puede encontrar un elemento (o determinar su ausencia) en unas pocas decenas de comparaciones.
* **Rendimiento:** En sistemas que manejan terabytes o petabytes de datos indexados y ordenados, la capacidad de localizar información rápidamente es crítica para la experiencia del usuario y la eficiencia del sistema. La búsqueda binaria permite tiempos de respuesta rápidos.
* **Base para estructuras de datos más complejas:** Muchos algoritmos y estructuras de datos eficientes utilizados en grandes sistemas, como árboles B, árboles B+ (comunes en bases de datos), y otros árboles de búsqueda balanceados, se basan en los principios de la búsqueda binaria para lograr búsquedas, inserciones y eliminaciones rápidas.

---

### 3) Contar elementos en un rango `[x, y]` en un arreglo ordenado `T`

Para determinar cuántos elementos del arreglo `T` (ordenado crecientemente, $n$ enteros distintos) se encuentran en el rango `[x, y]` (inclusive) con complejidad $O(\log n)$, podemos usar dos búsquedas binarias modificadas:
1.  Encontrar el índice del primer elemento que es mayor o igual a `x`. Llamémoslo `startIndex`.
2.  Encontrar el índice del último elemento que es menor o igual a `y`. Llamémoslo `endIndex`.

Si `startIndex` o `endIndex` no se encuentran (o `startIndex > endIndex`), entonces no hay elementos en el rango. De lo contrario, el número de elementos es `endIndex - startIndex + 1`.

**Lógica para C++:**
```cpp
// Función para encontrar el primer índice i tal que T[i] >= val
int findLowerBound(int T[], int n, int val) {
    int low = 0, high = n - 1;
    int ans = n; // Si no se encuentra, significa que todos son menores
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (T[mid] >= val) {
            ans = mid;
            high = mid - 1; // Intentar encontrar uno aún más a la izquierda
        } else {
            low = mid + 1;
        }
    }
    return ans;
}

// Función para encontrar el último índice i tal que T[i] <= val
// (Equivalente a encontrar el primer T[i] > val y restarle 1)
int findUpperBound(int T[], int n, int val) {
    int low = 0, high = n - 1;
    int ans = -1; // Si no se encuentra, significa que todos son mayores
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (T[mid] <= val) {
            ans = mid;
            low = mid + 1; // Intentar encontrar uno aún más a la derecha
        } else {
            high = mid - 1;
        }
    }
    return ans;
}

int countInRange(int T[], int n, int x, int y) {
    if (x > y) return 0;
    int startIndex = findLowerBound(T, n, x);
    int endIndex = findUpperBound(T, n, y);

    if (startIndex > endIndex || startIndex == n || endIndex == -1) {
        return 0;
    }
    return endIndex - startIndex + 1;
}
```
Cada una de las funciones `findLowerBound` y `findUpperBound` tiene una complejidad de $O(\log n)$[cite: 13]. Por lo tanto, la complejidad total es $O(\log n)$.

---

### 4) Mediana de dos vectores ordenados `X` e `Y`

Encontrar la mediana del conjunto total de $2n$ elementos (formado por dos vectores ordenados `X` e `Y`, cada uno con $n$ enteros) en tiempo $O(\log n)$ sin mezclar los vectores es un problema clásico de "Divide y Conquista". La mediana de $2n$ elementos será el promedio del $n$-ésimo y $(n+1)$-ésimo elemento si los tuviéramos todos ordenados, o simplemente el $n$-ésimo si usamos indexación basada en 0 y buscamos el elemento en la posición $n-1$ y $n$ del conjunto combinado de $2n$ elementos. Simplifiquemos buscando el $k$-ésimo elemento, donde $k$ puede ser $n$.

**Idea General (para encontrar el $k$-ésimo elemento):**
1.  Compara los elementos medios de las porciones relevantes de `X` e `Y`. Digamos `X[midX]` e `Y[midY]`.
2.  Si `X[midX] <= Y[midY]`:
    * Sabemos que todos los elementos en `X` hasta `midX` son más pequeños que `Y[midY]`. Estos elementos (y posiblemente algunos de `Y` antes de `midY`) están en la primera mitad del conjunto combinado.
    * Si $k$ es menor que la cantidad de elementos descartados de `X` más los de `Y` hasta `midY`, entonces la búsqueda continúa en la parte izquierda de `X` y/o `Y`, descartando la parte derecha de `Y`.
    * Si $k$ es mayor, entonces la búsqueda continúa en la parte derecha de `X` y/o `Y`, descartando la parte izquierda de `X`. Se ajusta $k$.
3.  Si `X[midX] > Y[midY]`, se aplica una lógica simétrica.
4.  Los casos base ocurren cuando uno de los arreglos se agota o $n$ es pequeño.

Para encontrar la mediana (que es el promedio del $n$-ésimo y $(n+1)$-ésimo elemento, o el $n$-ésimo elemento si $2n$ es impar y se considera una única mediana):
Una forma es encontrar el $n$-ésimo elemento y el $(n+1)$-ésimo elemento del conjunto combinado $X \cup Y$ y promediarlos. Cada búsqueda de $k$-ésimo elemento toma $O(\log n + \log m)$ o $O(\log (n+m))$. Como aquí $n=m$, es $O(\log n)$.

**Lógica para C++ (para la mediana de dos arreglos de igual tamaño `n`):**
El algoritmo exacto es un poco más complejo de implementar correctamente que una búsqueda binaria estándar. Una versión simplificada de la idea:
```cpp
// Esta es una versión simplificada y conceptual.
// El algoritmo completo para O(log n) es más detallado.
double findMedianSortedArrays(int X[], int n, int Y[], int m) {
    // Asegurarse de que n <= m para simplificar (no necesario aquí ya que n=m)
    if (n > m) return findMedianSortedArrays(Y, m, X, n);

    int low = 0, high = n;
    int totalLength = n + m;

    while (low <= high) {
        int partitionX = (low + high) / 2;
        int partitionY = (totalLength + 1) / 2 - partitionX;

        // Si partitionX es 0, no hay nada a la izquierda de X. Usar -INF.
        // Si partitionX es n, no hay nada a la derecha de X. Usar +INF.
        int maxLeftX = (partitionX == 0) ? INT_MIN : X[partitionX - 1];
        int minRightX = (partitionX == n) ? INT_MAX : X[partitionX];

        int maxLeftY = (partitionY == 0) ? INT_MIN : Y[partitionY - 1];
        int minRightY = (partitionY == m) ? INT_MAX : Y[partitionY];

        if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
            // Se encontró la partición correcta
            if (totalLength % 2 == 0) { // Longitud par
                return (double)(std::max(maxLeftX, maxLeftY) + std::min(minRightX, minRightY)) / 2.0;
            } else { // Longitud impar
                return (double)std::max(maxLeftX, maxLeftY);
            }
        } else if (maxLeftX > minRightY) { // Demasiado a la derecha en X
            high = partitionX - 1;
        } else { // Demasiado a la izquierda en X
            low = partitionX + 1;
        }
    }
    return -1; // No debería llegar aquí si los arreglos están ordenados
}
```
Este enfoque particular está más orientado a encontrar una partición que divida ambos arreglos de tal manera que todos los elementos a la izquierda de la partición sean menores que todos los elementos a la derecha. Es una técnica común para este problema y logra $O(\log(\min(n,m)))$. Dado que $n=m$, es $O(\log n)$.

---

### 5) Encontrar el pico `p` en una secuencia unimodal

Una secuencia unimodal $A = (a_1, ..., a_n)$ tiene un índice $p$ tal que $a_1 < ... < a_p$ y $a_p > ... > a_n$. El objetivo es encontrar $p$ en $O(\log n)$. Esto se puede hacer con una variante de la búsqueda binaria[cite: 8, 10].

**Lógica para C++:**
1.  Considera un elemento `A[mid]`.
2.  Compara `A[mid]` con sus vecinos `A[mid-1]` y `A[mid+1]` (cuidando los límites del arreglo).
    * Si `A[mid] > A[mid-1]` y `A[mid] > A[mid+1]`, entonces `mid` es el pico `p`.
    * Si `A[mid] > A[mid-1]` pero `A[mid] < A[mid+1]`, el pico está en la parte derecha (la secuencia sigue creciendo). Se busca en `[mid+1, high]`.
    * Si `A[mid] < A[mid-1]` pero `A[mid] > A[mid+1]`, el pico está en la parte izquierda (la secuencia ya está decreciendo). Se busca en `[low, mid-1]`.
    * (Un caso adicional puede ser `A[mid] < A[mid-1]` y `A[mid] < A[mid+1]` si la secuencia no es estrictamente unimodal o hay un valle, pero la definición dada implica un único pico).

**Lógica para C++:**
```cpp
int findPeakElement(int arr[], int n) {
    int low = 0, high = n - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        // Comprobar si mid es el pico
        // Considerar los casos de borde: mid=0 o mid=n-1
        bool isPeak = true;
        if (mid > 0 && arr[mid] < arr[mid - 1]) {
            isPeak = false; // No es pico, decrece a la izquierda
        }
        if (mid < n - 1 && arr[mid] < arr[mid + 1]) {
            isPeak = false; // No es pico, crece a la derecha
        }

        if (isPeak) {
            return mid; // mid es el pico
        } else if (mid > 0 && arr[mid] < arr[mid - 1]) {
            // El pico está a la izquierda (estamos en la parte decreciente)
            high = mid - 1;
        } else {
            // El pico está a la derecha (estamos en la parte creciente)
            // (arr[mid] < arr[mid+1])
            low = mid + 1;
        }
    }
    return -1; // No debería ocurrir para una secuencia unimodal válida con n >= 3
}
```
La complejidad es $O(\log n)$ porque el espacio de búsqueda se reduce a la mitad en cada iteración[cite: 13].

---

### 6) Mínimo y máximo en un arreglo de actividad física

**a) Algoritmo iterativo:**
Recorrer el arreglo una vez, manteniendo dos variables, `minVal` y `maxVal`, actualizándolas a medida que se encuentran valores menores o mayores respectivamente.

**Lógica para C++ (Iterativo):**
```cpp
#include <utility> // Para std::pair

std::pair<int, int> findMinMaxIterative(int arr[], int n) {
    if (n == 0) {
        // Manejar arreglo vacío como se desee
        return {INT_MAX, INT_MIN}; // O lanzar excepción
    }
    int minVal = arr[0];
    int maxVal = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] < minVal) {
            minVal = arr[i];
        }
        if (arr[i] > maxVal) {
            maxVal = arr[i];
        }
    }
    return {minVal, maxVal};
}
```

**b) Algoritmo usando Divide y Conquista:**
1.  **Dividir**: Si el arreglo tiene más de un elemento (o dos), divídelo en dos subarreglos.
2.  **Conquistar**: Encuentra recursivamente el mínimo y máximo de cada subarreglo. Esto devolverá `(min1, max1)` para el primer subarreglo y `(min2, max2)` para el segundo.
3.  **Combinar**: El mínimo global es `min(min1, min2)` y el máximo global es `max(max1, max2)`.
    * Caso base: Si el arreglo tiene un solo elemento, ese es tanto el mínimo como el máximo. Si tiene dos, compáralos directamente.

**Lógica para C++ (Divide y Conquista):**
```cpp
std::pair<int, int> findMinMaxDivideAndConquer(int arr[], int low, int high) {
    // Caso base: un solo elemento
    if (low == high) {
        return {arr[low], arr[low]};
    }
    // Caso base: dos elementos
    if (high == low + 1) {
        if (arr[low] < arr[high]) {
            return {arr[low], arr[high]};
        } else {
            return {arr[high], arr[low]};
        }
    }

    // Dividir
    int mid = low + (high - low) / 2;
    std::pair<int, int> leftMinMax = findMinMaxDivideAndConquer(arr, low, mid);
    std::pair<int, int> rightMinMax = findMinMaxDivideAndConquer(arr, mid + 1, high);

    // Combinar
    int finalMin = std::min(leftMinMax.first, rightMinMax.first);
    int finalMax = std::max(leftMinMax.second, rightMinMax.second);

    return {finalMin, finalMax};
}
```

**c) Complejidad temporal:**
* **Iterativo (a):** $O(n)$. Se realiza un único recorrido por el arreglo. El número de comparaciones es aproximadamente $2(n-1)$ en el peor caso.
* **Divide y Conquista (b):**
    La relación de recurrencia es $T(n) = 2T(n/2) + c$, donde $c$ es el costo de comparación para combinar (constante, 2 comparaciones).
    Usando el Teorema Maestro, esto resuelve a $T(n) = O(n)$.
    El número de comparaciones es aproximadamente $3n/2 - 2$.

**d) Análisis comparativo de eficiencia:**
* Ambos algoritmos tienen una complejidad temporal de $O(n)$.
* El algoritmo iterativo es generalmente más simple de implementar y tiene una constante oculta ligeramente menor en términos de operaciones reales (menos sobrecarga de llamadas a funciones recursivas).
* El algoritmo de Divide y Conquista, aunque también $O(n)$, realiza menos comparaciones ($3n/2 - 2$) que la versión iterativa simple ($2n - 2$) si se optimiza el caso base para dos elementos.
* En la práctica, para este problema específico (min y max), la versión iterativa suele ser preferida por su simplicidad y menor sobrecarga, a menos que el contexto requiera específicamente un enfoque de Divide y Conquista (por ejemplo, en un entorno de procesamiento paralelo donde las sub-tareas se pueden distribuir).

---

### 7) Par de cupones que suman `x` en un arreglo ordenado `S`

**a) Implementación del algoritmo:**
Dado un arreglo ordenado `S` de $n$ cupones (enteros distintos) y un valor `x`.

**Método 1: Dos Punteros (Iterativo, $O(n)$)**
1.  Inicializa un puntero `left = 0` y `right = n-1`.
2.  Mientras `left < right`:
    * Calcula `currentSum = S[left] + S[right]`.
    * Si `currentSum == x`, has encontrado un par. Retorna `true`.
    * Si `currentSum < x`, necesitas una suma mayor, así que incrementa `left`.
    * Si `currentSum > x`, necesitas una suma menor, así que decrementa `right`.
3.  Si los punteros se cruzan y no se encontró un par, retorna `false`.

**Lógica para C++ (Dos Punteros):**
```cpp
bool findPairSum(int S[], int n, int x) {
    int left = 0;
    int right = n - 1;
    while (left < right) {
        int currentSum = S[left] + S[right];
        if (currentSum == x) {
            // std::cout << "Par encontrado: " << S[left] << " + " << S[right] << " = " << x << std::endl;
            return true;
        } else if (currentSum < x) {
            left++;
        } else { // currentSum > x
            right--;
        }
    }
    return false;
}
```

**Método 2: Iterar y Búsqueda Binaria ($O(n \log n)$)**
Para cada elemento `S[i]` en el arreglo, busca `x - S[i]` en el resto del arreglo usando búsqueda binaria. Hay que tener cuidado de no usar el mismo elemento `S[i]` dos veces si `x - S[i] == S[i]`.

**Lógica para C++ (Iterar + Búsqueda Binaria):**
```cpp
// Función de búsqueda binaria estándar
bool binarySearch(int arr[], int low, int high, int key) {
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return true;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return false;
}

bool findPairSumBinarySearch(int S[], int n, int x) {
    for (int i = 0; i < n; i++) {
        int complement = x - S[i];
        // Buscar el complemento en el resto del arreglo, excluyendo S[i] mismo
        // si i < n-1 y complemento > S[i] (para evitar duplicados y buscar en la parte correcta)
        if (complement == S[i]) { // si buscamos un par donde los dos elementos son iguales
             if (i + 1 < n && S[i+1] == complement) return true; // si hay otro igual
        } else {
             // Buscar 'complement' en S[i+1 ... n-1] o S[0 ... i-1]
             // Simplificado: buscar en todo el arreglo y asegurarse que no es el mismo índice
             // Para O(n log n), es más simple buscar en todo el subarreglo restante.
            if (binarySearch(S, i + 1, n - 1, complement)) {
                 // std::cout << "Par encontrado: " << S[i] << " + " << complement << " = " << x << std::endl;
                return true;
            }
        }
    }
    return false;
}
```

**b) Complejidad temporal:**
* **Método de Dos Punteros:** $O(n)$, porque en cada paso, `left` se incrementa o `right` se decrementa, y se detienen cuando se cruzan.
* **Método de Iterar y Búsqueda Binaria:** $O(n \log n)$, porque se itera $n$ veces y cada búsqueda binaria toma $O(\log n)$.

El método de dos punteros es más eficiente para este problema.

---

### 8) Subarreglo contiguo con la suma máxima (Variaciones de pulso/ECG)

**a) Implementación del algoritmo:**
Este es el problema del "máximo sub-arreglo" discutido en el PDF como ejemplo de Divide y Conquista[cite: 46, 47, 50, 51].

**Algoritmo de Divide y Conquista ($O(n \log n)$):**
1.  **Dividir**: Divide el arreglo en dos mitades.
2.  **Conquistar**: Recursivamente encuentra la suma máxima del subarreglo en:
    * La mitad izquierda.
    * La mitad derecha.
3.  **Combinar**: Encuentra la suma máxima del subarreglo que cruza el punto medio. Esto implica encontrar el subarreglo de suma máxima que termina en el punto medio (barriendo hacia la izquierda desde el medio) y el subarreglo de suma máxima que comienza en el punto medio + 1 (barriendo hacia la derecha desde el medio), y sumarlos.
    La respuesta es el máximo de estas tres sumas.
    El PDF describe este proceso en las páginas 27-35[cite: 49, 50, 51, 52, 54, 55, 56, 57, 58]. El pseudocódigo se presenta en las páginas 97-99[cite: 166, 167, 168, 169, 170, 171, 172, 173, 174, 175, 176].

**Lógica para C++ (Divide y Conquista):**
```cpp
// Función para encontrar la suma máxima de un subarreglo que cruza el punto medio
int maxCrossingSum(int arr[], int l, int m, int h) {
    int sum = 0;
    int left_sum = INT_MIN;
    for (int i = m; i >= l; i--) {
        sum = sum + arr[i];
        if (sum > left_sum)
            left_sum = sum;
    }

    sum = 0;
    int right_sum = INT_MIN;
    for (int i = m + 1; i <= h; i++) {
        sum = sum + arr[i];
        if (sum > right_sum)
            right_sum = sum;
    }
    // Considerar el caso donde left_sum o right_sum podrían ser negativos
    // y el otro no existir (si la mitad es vacía), pero con l, m, h bien definidos
    // esto no sucede. El cruce debe tener al menos un elemento de cada lado si m no es l o h.
    // Si una de las sumas (left_sum o right_sum) no fue actualizada (sigue INT_MIN),
    // y la otra sí, se debe decidir si el cruce es válido.
    // Una forma más robusta: si left_sum es INT_MIN (todos negativos o vacío a la izq)
    // y right_sum es INT_MIN (todos negativos o vacío a la der), entonces
    // maxCrossingSum es la suma de los más grandes de cada lado,
    // o solo uno si el otro es "infinitamente negativo".
    // La suma de left_sum y right_sum es la opción si ambos son positivos.
    // Si uno es negativo y el otro positivo, el cruce podría ser solo el lado positivo.
    // El algoritmo estándar suma left_sum + right_sum.
    // Si m==h (solo queda el lado izquierdo), right_sum sería 0 o el valor de m+1 si se calcula.
    // Si m+1 > h, right_sum es 0. Si l > m, left_sum es 0.
    // El pseudocódigo del PDF [cite: 172, 173, 174, 175, 176] calcula sumas y las combina.
    
    // Si left_sum o right_sum no se actualizan porque todos los elementos en su
    // respectivo barrido son muy negativos y la suma nunca supera INT_MIN,
    // aún así se suman. Si un lado no tiene elementos (e.g., m=h), su suma de cruce es 0.
    // Sin embargo, la implementación común y la del PDF asumen que `left_sum` y `right_sum`
    // se calculan como se muestra y se suman.
    if (left_sum == INT_MIN && right_sum == INT_MIN) return INT_MIN; // Evitar overflow si ambos son INT_MIN
    if (left_sum == INT_MIN) return right_sum; // Si solo hay parte derecha
    if (right_sum == INT_MIN) return left_sum; // Si solo hay parte izquierda

    return left_sum + right_sum;
}


// Función recursiva para encontrar la suma máxima del subarreglo
int maxSubArraySum(int arr[], int l, int h) {
    if (l == h) // Caso base: un solo elemento
        return arr[l];

    int m = (l + h) / 2; // Encuentra el punto medio

    // Retorna el máximo de las tres posibilidades:
    // a) Suma máxima en el subarreglo izquierdo
    // b) Suma máxima en el subarreglo derecho
    // c) Suma máxima en el subarreglo que cruza el punto medio
    int max_left_subarray = maxSubArraySum(arr, l, m);
    int max_right_subarray = maxSubArraySum(arr, m + 1, h);
    int max_crossing_subarray = maxCrossingSum(arr, l, m, h);

    return std::max({max_left_subarray, max_right_subarray, max_crossing_subarray});
}
```

**Algoritmo de Kadane ($O(n)$):**
Este es un algoritmo iterativo más eficiente.
1.  Inicializa `max_so_far = INT_MIN` y `current_max = 0`.
2.  Recorre el arreglo:
    * `current_max = current_max + arr[i]`.
    * Si `current_max > max_so_far`, entonces `max_so_far = current_max`.
    * Si `current_max < 0`, entonces `current_max = 0` (comienza un nuevo subarreglo).
3.  Retorna `max_so_far`.

**Lógica para C++ (Kadane):**
```cpp
int maxSubArraySumKadane(int arr[], int n) {
    int max_so_far = INT_MIN;
    int current_max = 0;
    for (int i = 0; i < n; i++) {
        current_max = current_max + arr[i];
        if (max_so_far < current_max) {
            max_so_far = current_max;
        }
        if (current_max < 0) {
            current_max = 0;
        }
    }
    // Si todos los números son negativos, max_so_far será el mayor de ellos (o el menos negativo).
    // La lógica anterior de Kadane funciona bien si hay al menos un número no negativo.
    // Si todos son negativos, max_so_far podría quedar en 0 si todos son <0.
    // Modificación para manejar todos negativos:
    if (max_so_far == 0) { // Posiblemente todos negativos y current_max se reseteó a 0
        bool all_negative_or_zero = true;
        int max_val_if_all_neg = INT_MIN;
        for(int i=0; i<n; ++i) {
            if (arr[i] > 0) all_negative_or_zero = false;
            if (arr[i] > max_val_if_all_neg) max_val_if_all_neg = arr[i];
        }
        if (all_negative_or_zero && n > 0) return max_val_if_all_neg;
    }
    // Si el arreglo puede estar vacío
    if (n == 0) return 0; // O algún otro valor apropiado
    
    return max_so_far;
}
// Una implementación más simple de Kadane que maneja todos negativos correctamente:
int maxSubArraySumKadaneSimplified(int arr[], int n) {
    if (n == 0) return 0; // o error
    int max_so_far = arr[0];
    int current_max = arr[0];
    for (int i = 1; i < n; i++) {
        current_max = std::max(arr[i], current_max + arr[i]);
        max_so_far = std::max(max_so_far, current_max);
    }
    return max_so_far;
}
```

**b) Complejidad temporal y análisis:**
* **Divide y Conquista:** $O(n \log n)$[cite: 178]. La recurrencia es $T(n) = 2T(n/2) + O(n)$ (la parte de `maxCrossingSum` es $O(n)$).
* **Kadane:** $O(n)$ (un solo recorrido).

**Si todos los valores del arreglo fueran positivos:**
* El subarreglo contiguo con la mayor suma sería el arreglo completo.
* No sería necesario aplicar la técnica de Divide y Conquista ni Kadane en su forma completa. Una solución más simple sería sumar todos los elementos del arreglo, lo cual es $O(n)$.

---

### 9) Comparación de dos algoritmos alternativos

**a) Algoritmo A:** Resuelve el problema dividiéndolo en dos subproblemas de tamaño $n/2$, resuelve recursivamente cada subproblema y combina la solución en tiempo lineal.
* Relación de recurrencia: $T_A(n) = 2T_A(n/2) + O(n)$.
* Usando el Teorema Maestro (caso 2, donde $a=2, b=2, f(n) = O(n)$, entonces $\log_b a = \log_2 2 = 1$. Como $f(n) = \Theta(n^{\log_b a}) = \Theta(n^1)$), el tiempo de ejecución es $O(n \log n)$.
    Esto es característico de algoritmos como Mergesort.

**b) Algoritmo B:** Resuelve el problema resolviendo dos subproblemas de tamaño $n-1$ y combinando la solución en tiempo constante.
* Relación de recurrencia: $T_B(n) = 2T_B(n-1) + O(1)$.
* Esta recurrencia lleva a una complejidad exponencial.
    * $T_B(n) = 2T_B(n-1) + c$
    * $T_B(n) = 2(2T_B(n-2) + c) + c = 2^2 T_B(n-2) + 2c + c$
    * $T_B(n) = 2^2(2T_B(n-3) + c) + 2c + c = 2^3 T_B(n-3) + 4c + 2c + c$
    * ...
    * $T_B(n) = 2^k T_B(n-k) + c \sum_{j=0}^{k-1} 2^j$.
    * Si $k=n$ (asumiendo $T_B(0)$ es una constante), entonces $T_B(n) = 2^n T_B(0) + c(2^n - 1)$.
    * Por lo tanto, $T_B(n) = O(2^n)$.
    El PDF muestra un ejemplo similar con Fibonacci recursivo (páginas 106-107)[cite: 181, 182, 183, 184, 185, 186, 187], donde se menciona que una solución así "Divide pero ... no conquista nada" y tiene complejidad exponencial.

**¿Cuál escogería?**
Escogería el **Algoritmo A**.
* El Algoritmo A tiene una complejidad de $O(n \log n)$, que es significativamente más eficiente (especialmente para valores grandes de $n$) que la complejidad exponencial $O(2^n)$ del Algoritmo B.
* Los algoritmos exponenciales se vuelven inviables muy rápidamente a medida que $n$ aumenta. Los algoritmos $O(n \log n)$ son considerados eficientes y escalan bien.

---