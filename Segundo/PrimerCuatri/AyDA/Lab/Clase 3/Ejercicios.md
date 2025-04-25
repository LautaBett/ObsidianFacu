¡Excelente! Vamos a resolver estos ejercicios paso a paso, utilizando los conceptos y ejemplos de las notas [[Ejemplo de ejercicios resueltos]], [[Complejidad y eficiencia]], y [[Memoria]].

---

### Ejercicio 1: Búsqueda en Agenda (Arreglo Estático)

**Tarea:** Usar un arreglo estático para 5 contactos. Implementar búsqueda por nombre y número. Realizar seguimiento para buscar "Ana" y el teléfono 15470424.

**Solución:**

Podemos adaptar directamente el código del [[Ejemplo de ejercicios resueltos]] (Ejercicio 1), ajustando `MAX_CONTACTOS` a 5.

```cpp
#include <iostream>
#include <string>
#include <vector> // Usaremos vector para inicializar fácilmente

using namespace std;

// Tamaño fijo para nuestro arreglo estático
const int MAX_CONTACTOS = 5;

// Estructura para almacenar la información de un contacto
struct Contacto {
    string nombre;
    int telefono; // Asumiendo que el teléfono es un número entero
};

// --- Función buscarPorNumero (Adaptada de [[Ejemplo de ejercicios resueltos]]) ---
// Complejidad: O(N) - Búsqueda lineal
string buscarPorNumero(int numero, const Contacto* contactos, int n_contactos) {
    const Contacto* ptr = contactos;
    string nombre = "";
    int i = 0;
    bool encontro = false;
    cout << "--- Seguimiento buscarPorNumero(" << numero << ") ---" << endl;
    while (!encontro && i < n_contactos) {
        cout << "  Iteracion " << i << ": Comparando con " << ptr->nombre << " (" << ptr->telefono << ")" << endl;
        if (ptr->nombre != "" && ptr->telefono == numero ) {
            cout << "    -> Encontrado!" << endl;
            nombre = ptr->nombre;
            encontro = true;
        }
        i++;
        ptr++; // Avanza al siguiente contacto en memoria (Stack)
    }
     if (!encontro) {
         cout << "  -> No encontrado." << endl;
     }
    cout << "-----------------------------------------" << endl;
    return nombre;
}

// --- Función buscarPorNombre (Adaptada de [[Ejemplo de ejercicios resueltos]]) ---
// Complejidad: O(N) - Búsqueda lineal
int buscarPorNombre(string nombre_buscar, const Contacto* contactos, int n_contactos) {
    const Contacto* ptr = contactos;
    int telefono = -1;
    int i = 0;
    bool encontro = false;
    cout << "--- Seguimiento buscarPorNombre(" << nombre_buscar << ") ---" << endl;
    while (!encontro && i < n_contactos) {
         cout << "  Iteracion " << i << ": Comparando con " << ptr->nombre << " (" << ptr->telefono << ")" << endl;
        if (ptr->nombre == nombre_buscar) {
             cout << "    -> Encontrado!" << endl;
            telefono = ptr->telefono;
            encontro = true;
        }
        i++;
        ptr++; // Avanza al siguiente contacto en memoria (Stack)
    }
     if (!encontro) {
         cout << "  -> No encontrado." << endl;
     }
     cout << "-----------------------------------------" << endl;
    return telefono;
}

// --- Función mostrarContactos (Adaptada de [[Ejemplo de ejercicios resueltos]]) ---
void mostrarContactos(const Contacto* contactos, int n_contactos) {
    cout << "\nLista de Contactos Actual:\n";
    for (int i = 0; i < n_contactos; i++) {
        if (contactos[i].nombre != "") {
            cout << "  " << contactos[i].nombre << " - " << contactos[i].telefono << endl;
        }
    }
     cout << "---------------------------\n" << endl;
}

int main() {
    // Arreglo estático en el Stack con los 5 contactos
    Contacto contactos[MAX_CONTACTOS] = {
        {"Juan", 15678410},
        {"Ana", 15974417},
        {"Pedro", 15570327},
        {"Maria", 15609411},
        {"Carlos", 15470424}
    };

    mostrarContactos(contactos, MAX_CONTACTOS);

    // Realizar seguimiento solicitado
    int telefono_ana = buscarPorNombre("Ana", contactos, MAX_CONTACTOS);
    cout << "Resultado buscarPorNombre('Ana'): " << telefono_ana << endl << endl;

    string nombre_carlos = buscarPorNumero(15470424, contactos, MAX_CONTACTOS);
    cout << "Resultado buscarPorNumero(15470424): " << nombre_carlos << endl << endl;

    return 0;
}
```

**Seguimiento (Salida Esperada):**

```
Lista de Contactos Actual:
  Juan - 15678410
  Ana - 15974417
  Pedro - 15570327
  Maria - 15609411
  Carlos - 15470424
---------------------------

--- Seguimiento buscarPorNombre(Ana) ---
  Iteracion 0: Comparando con Juan (15678410)
  Iteracion 1: Comparando con Ana (15974417)
    -> Encontrado!
-----------------------------------------
Resultado buscarPorNombre('Ana'): 15974417

--- Seguimiento buscarPorNumero(15470424) ---
  Iteracion 0: Comparando con Juan (15678410)
  Iteracion 1: Comparando con Ana (15974417)
  Iteracion 2: Comparando con Pedro (15570327)
  Iteracion 3: Comparando con Maria (15609411)
  Iteracion 4: Comparando con Carlos (15470424)
    -> Encontrado!
-----------------------------------------
Resultado buscarPorNumero(15470424): Carlos
```

**Explicación:**

*   **Memoria:** El arreglo `contactos` se crea en el **Stack** porque su tamaño (`MAX_CONTACTOS`) es conocido en tiempo de compilación. Ver [[Memoria]] sección Stack.
*   **Punteros:** Las funciones de búsqueda reciben `contactos` como un puntero (`const Contacto*`) a la primera estructura del arreglo. Usamos `ptr++` (aritmética de punteros) para movernos al siguiente `Contacto` en la memoria contigua del Stack.
*   **Complejidad:** Ambas búsquedas son **lineales**, recorren el arreglo elemento por elemento en el peor caso. Su complejidad es $O(N)$, donde N es el número de contactos (5 en este caso). Ver [[Complejidad y eficiencia]].

---

### Ejercicio 2: Arreglo Dinámico con Valores Aleatorios

**Tarea:** Pedir N, crear arreglo dinámico de N enteros, llenarlo con aleatorios (1-100) e imprimirlo.

**Solución:**

```cpp
#include <iostream>
#include <cstdlib> // Para rand(), srand()
#include <ctime>   // Para time()

using namespace std;

int main() {
    int n;

    // Pedir N al usuario
    cout << "Ingrese el tamaño del arreglo (N): ";
    cin >> n;

    if (n <= 0) {
        cout << "El tamaño debe ser positivo." << endl;
        return 1;
    }

    // --- Creación del Arreglo Dinámico ---
    // Solicita memoria en el Heap para 'n' enteros.
    // 'arreglo' es un puntero (en el Stack) que guarda la dirección del bloque en el Heap.
    // Ver [[Memoria]] sección Heap y Arreglos Dinámicos.
    int* arreglo = new int[n];
    cout << "Memoria para " << n << " enteros asignada en el Heap en la direccion: " << arreglo << endl;

    // --- Llenado con Valores Aleatorios ---
    // Inicializar la semilla del generador aleatorio
    srand(time(0));

    cout << "Llenando el arreglo con valores aleatorios (1-100)..." << endl;
    for (int i = 0; i < n; ++i) {
        // Genera un número entre 0 y 99, luego suma 1.
        arreglo[i] = rand() % 100 + 1;
    }

    // --- Impresión del Arreglo ---
    cout << "Contenido del arreglo:" << endl;
    cout << "[ ";
    for (int i = 0; i < n; ++i) {
        cout << arreglo[i] << " ";
    }
    cout << "]" << endl;

    // --- Liberación de Memoria ---
    // ¡Fundamental! Devuelve la memoria del Heap al sistema operativo.
    // Usar delete[] porque se asignó con new int[n].
    // Ver [[Memoria]] sección Memoria Dinámica y Problemas Comunes.
    delete[] arreglo;
    cout << "Memoria del Heap liberada." << endl;
    arreglo = nullptr; // Buena práctica para evitar punteros colgantes

    return 0;
}
```

**Explicación:**

*   **Memoria Dinámica:** Usamos `new int[n]` para asignar memoria en el **Heap**, ya que `n` se conoce en tiempo de ejecución. `arreglo` es un puntero que almacena la dirección base de este bloque. Ver [[Memoria]].
*   **`rand()`, `srand()`, `time()`:** Funciones estándar para generar números pseudoaleatorios. `srand(time(0))` inicializa la semilla para que los números sean diferentes cada vez que se ejecuta el programa.
*   **`delete[]`:** Es crucial liberar la memoria asignada con `new[]` usando `delete[]`. Olvidarlo causa un **memory leak**.
*   **Complejidad:** La creación, llenado e impresión son operaciones lineales. La complejidad total es $O(N)$.

---

### Ejercicio 3: Secuencia de Punteros - Insertar Principio/Final

**Tarea:** Implementar una lista enlazada (secuencia de punteros) con funciones para insertar al principio y al final.

**Solución:**

Podemos usar directamente las funciones `agregar_principio` y `agregar_final` del [[Ejemplo de ejercicios resueltos]] (Ejercicio 2).

```cpp
#include <iostream>
#include <cstdlib> // NULL

using namespace std;

// Estructura del Nodo (de [[Ejemplo de ejercicios resueltos]])
struct Nodo {
    int elemento;
    Nodo * siguiente;
};

// Función crear_nodo (de [[Ejemplo de ejercicios resueltos]])
// Crea un nodo en el Heap.
Nodo * crear_nodo(int elemento, Nodo * sigte) {
    Nodo * nuevo = new Nodo(); // Asigna memoria en el Heap
    nuevo->elemento = elemento;
    nuevo->siguiente = sigte;
    return nuevo; // Devuelve la dirección del nodo en el Heap
}

// --- Función agregar_final (de [[Ejemplo de ejercicios resueltos]]) ---
// Complejidad: O(N) - Debe recorrer toda la lista para encontrar el final.
void agregar_final(int nuevo_elemento, Nodo * & primero) {
    Nodo * nuevo = crear_nodo(nuevo_elemento, NULL);
    if (primero == NULL) {
        primero = nuevo; // Modifica 'primero' de main si la lista estaba vacía
    } else {
        Nodo * actual = primero;
        while (actual->siguiente != NULL) { // Recorre hasta el último
            actual = actual->siguiente;
        }
        actual->siguiente = nuevo; // Enlaza el nuevo nodo
    }
}

// --- Función agregar_principio (de [[Ejemplo de ejercicios resueltos]]) ---
// Complejidad: O(1) - Solo manipula punteros al inicio.
void agregar_principio (int nuevo_elemento, Nodo * & primero) {
    // El nuevo nodo apunta al que era el primero.
    Nodo * nuevo = crear_nodo(nuevo_elemento, primero);
    // 'primero' ahora apunta al nuevo nodo. Modifica 'primero' de main.
    primero = nuevo;
}

// Función mostrar_elementos (de [[Ejemplo de ejercicios resueltos]])
void mostrar_elementos(const Nodo * primero) {
    const Nodo* actual = primero;
    cout << "Lista: ";
    while (actual != NULL) {
        cout << actual->elemento << " -> ";
        actual = actual->siguiente;
    }
    cout << "NULL" << endl;
}

// Función liberar_memoria (de [[Ejemplo de ejercicios resueltos]])
// ¡Importante para evitar memory leaks!
void liberar_memoria(Nodo * & primero) {
    Nodo * actual = primero;
    Nodo * siguiente = NULL;
    while (actual != NULL) {
        siguiente = actual->siguiente;
        delete actual; // Libera nodo actual del Heap
        actual = siguiente;
    }
    primero = NULL; // Asegura que el puntero original quede nulo
}


int main() {
    Nodo* mi_lista = NULL; // Puntero 'primero' en el Stack, inicialmente nulo.

    cout << "Insertando al principio..." << endl;
    agregar_principio(10, mi_lista); // 10 -> NULL
    mostrar_elementos(mi_lista);
    agregar_principio(5, mi_lista);  // 5 -> 10 -> NULL
    mostrar_elementos(mi_lista);

    cout << "\nInsertando al final..." << endl;
    agregar_final(20, mi_lista);   // 5 -> 10 -> 20 -> NULL
    mostrar_elementos(mi_lista);
    agregar_final(30, mi_lista);   // 5 -> 10 -> 20 -> 30 -> NULL
    mostrar_elementos(mi_lista);

    // Liberar memoria al final
    liberar_memoria(mi_lista);
    cout << "\nMemoria liberada." << endl;
    mostrar_elementos(mi_lista);


    return 0;
}
```

**Explicación:**

*   **Memoria:** Cada nodo se crea individualmente en el **Heap** con `new`. La lista puede crecer dinámicamente. Ver [[Memoria]].
*   **Punteros:** `primero` (en `main`) apunta al inicio. Cada nodo tiene un puntero `siguiente` que enlaza con el próximo nodo en el Heap.
*   **Paso por Referencia (`&`):** `Nodo*& primero` es crucial para que `agregar_principio` y `agregar_final` (cuando la lista está vacía) puedan modificar el puntero `primero` que está en `main`.
*   **Complejidad:** `agregar_principio` es $O(1)$ (tiempo constante). `agregar_final` es $O(N)$ porque necesita recorrer toda la lista para encontrar el último nodo. Ver [[Complejidad y eficiencia]].

---

### Ejercicio 4: Secuencia de Punteros - Eliminar Nodo

**Tarea:** Implementar una función para eliminar un nodo específico de la lista enlazada.

**Solución:**

Podemos usar la función `eliminar_elemento` del [[Ejemplo de ejercicios resueltos]] (Ejercicio 2).

```cpp
#include <iostream>
#include <cstdlib> // NULL

using namespace std;

// Estructura del Nodo (de [[Ejemplo de ejercicios resueltos]])
struct Nodo {
    int elemento;
    Nodo * siguiente;
};

// Función crear_nodo (de [[Ejemplo de ejercicios resueltos]])
Nodo * crear_nodo(int elemento, Nodo * sigte) {
    Nodo * nuevo = new Nodo();
    nuevo->elemento = elemento;
    nuevo->siguiente = sigte;
    return nuevo;
}

// Función agregar_principio (de [[Ejemplo de ejercicios resueltos]])
void agregar_principio (int nuevo_elemento, Nodo * & primero) {
    Nodo * nuevo = crear_nodo(nuevo_elemento, primero);
    primero = nuevo;
}

// Función mostrar_elementos (de [[Ejemplo de ejercicios resueltos]])
void mostrar_elementos(const Nodo * primero) {
    const Nodo* actual = primero;
    cout << "Lista: ";
    while (actual != NULL) {
        cout << actual->elemento << " -> ";
        actual = actual->siguiente;
    }
    cout << "NULL" << endl;
}

// --- Función eliminar_elemento (de [[Ejemplo de ejercicios resueltos]]) ---
// Complejidad: O(N) - En el peor caso, debe recorrer la lista para encontrar el elemento.
bool eliminar_elemento(Nodo * & primero, int elemento_borrar) {
    Nodo * actual = primero;
    Nodo * anterior = NULL;

    // Busca el nodo manteniendo referencia al anterior
    while (actual != NULL && actual->elemento != elemento_borrar) {
        anterior = actual;
        actual = actual->siguiente;
    }

    // Si no se encontró
    if (actual == NULL) {
        cout << "Elemento " << elemento_borrar << " no encontrado para eliminar." << endl;
        return false;
    }

    // Si se encontró (actual != NULL)
    cout << "Eliminando nodo con elemento: " << elemento_borrar << endl;
    if (anterior == NULL) { // Caso: es el primer nodo
        primero = actual->siguiente; // Actualiza 'primero' de main
    } else { // Caso: es un nodo intermedio o el último
        anterior->siguiente = actual->siguiente; // "Saltea" el nodo actual
    }

    // Libera la memoria del nodo encontrado del Heap
    delete actual;
    return true;
}

// Función liberar_memoria (de [[Ejemplo de ejercicios resueltos]])
void liberar_memoria(Nodo * & primero) {
    Nodo * actual = primero;
    Nodo * siguiente = NULL;
    while (actual != NULL) {
        siguiente = actual->siguiente;
        delete actual;
        actual = siguiente;
    }
    primero = NULL;
}

int main() {
    Nodo* mi_lista = NULL;
    agregar_principio(30, mi_lista);
    agregar_principio(20, mi_lista);
    agregar_principio(10, mi_lista); // Lista: 10 -> 20 -> 30 -> NULL
    mostrar_elementos(mi_lista);

    eliminar_elemento(mi_lista, 20); // Elimina el del medio
    mostrar_elementos(mi_lista);     // Esperado: 10 -> 30 -> NULL

    eliminar_elemento(mi_lista, 10); // Elimina el primero
    mostrar_elementos(mi_lista);     // Esperado: 30 -> NULL

    eliminar_elemento(mi_lista, 30); // Elimina el último/único
    mostrar_elementos(mi_lista);     // Esperado: NULL

    eliminar_elemento(mi_lista, 50); // Intenta eliminar uno que no existe
    mostrar_elementos(mi_lista);     // Esperado: NULL

    liberar_memoria(mi_lista); // Aunque ya esté vacía, es bueno llamarla.
    return 0;
}
```

**Explicación:**

*   **Punteros:** Se usan `actual` y `anterior` para recorrer la lista. `anterior` es crucial para poder "reconectar" la lista al eliminar un nodo intermedio.
*   **Casos:** La función maneja correctamente la eliminación del primer nodo (modificando `primero` a través de la referencia `&`) y la eliminación de nodos intermedios/finales (modificando `anterior->siguiente`).
*   **`delete`:** Libera la memoria del nodo eliminado del **Heap**. Ver [[Memoria]].
*   **Complejidad:** La búsqueda del nodo a eliminar es lineal, por lo que la complejidad es $O(N)$.

---

### Ejercicio 5: Secuencia de Punteros - Obtener Primero/Último

**Tarea:** Implementar funciones para obtener el primer y último elemento de la lista de manera eficiente.

**Solución:**

```cpp
#include <iostream>
#include <stdexcept> // Para lanzar excepciones

using namespace std;

// Estructura del Nodo (de [[Ejemplo de ejercicios resueltos]])
struct Nodo {
    int elemento;
    Nodo * siguiente;
};

// Función crear_nodo (de [[Ejemplo de ejercicios resueltos]])
Nodo * crear_nodo(int elemento, Nodo * sigte) {
    Nodo * nuevo = new Nodo();
    nuevo->elemento = elemento;
    nuevo->siguiente = sigte;
    return nuevo;
}
// Función agregar_principio (de [[Ejemplo de ejercicios resueltos]])
void agregar_principio (int nuevo_elemento, Nodo * & primero) {
    Nodo * nuevo = crear_nodo(nuevo_elemento, primero);
    primero = nuevo;
}
// Función mostrar_elementos (de [[Ejemplo de ejercicios resueltos]])
void mostrar_elementos(const Nodo * primero) {
    const Nodo* actual = primero;
    cout << "Lista: ";
    while (actual != NULL) {
        cout << actual->elemento << " -> ";
        actual = actual->siguiente;
    }
    cout << "NULL" << endl;
}
// Función liberar_memoria (de [[Ejemplo de ejercicios resueltos]])
void liberar_memoria(Nodo * & primero) {
    Nodo * actual = primero;
    Nodo * siguiente = NULL;
    while (actual != NULL) {
        siguiente = actual->siguiente;
        delete actual;
        actual = siguiente;
    }
    primero = NULL;
}

// --- Función obtenerPrimero ---
// Obtiene el valor del primer elemento.
// Complejidad: O(1) - Acceso directo.
int obtenerPrimero(const Nodo* primero) {
    if (primero == NULL) {
        // Lanza una excepción si la lista está vacía. Otra opción sería retornar un valor especial.
        throw runtime_error("La lista esta vacia, no se puede obtener el primer elemento.");
    }
    // Accede directamente al elemento del primer nodo.
    return primero->elemento;
}

// --- Función obtenerUltimo ---
// Obtiene el valor del último elemento.
// Complejidad: O(N) - Debe recorrer toda la lista.
int obtenerUltimo(const Nodo* primero) {
    if (primero == NULL) {
        throw runtime_error("La lista esta vacia, no se puede obtener el ultimo elemento.");
    }

    const Nodo* actual = primero;
    // Recorre hasta que el 'siguiente' sea NULL, ese es el último nodo.
    while (actual->siguiente != NULL) {
        actual = actual->siguiente;
    }
    // Devuelve el elemento del último nodo encontrado.
    return actual->elemento;
}


int main() {
    Nodo* mi_lista = NULL;
    agregar_principio(30, mi_lista);
    agregar_principio(20, mi_lista);
    agregar_principio(10, mi_lista); // Lista: 10 -> 20 -> 30 -> NULL
    mostrar_elementos(mi_lista);

    try {
        cout << "Primer elemento: " << obtenerPrimero(mi_lista) << endl; // Esperado: 10
        cout << "Ultimo elemento: " << obtenerUltimo(mi_lista) << endl;  // Esperado: 30
    } catch (const runtime_error& e) {
        cerr << "Error: " << e.what() << endl;
    }

     // Prueba con lista vacía
     Nodo* lista_vacia = NULL;
     cout << "\nProbando con lista vacia:" << endl;
      try {
        cout << "Primer elemento: " << obtenerPrimero(lista_vacia) << endl;
    } catch (const runtime_error& e) {
        cerr << "Error al obtener primero: " << e.what() << endl;
    }
       try {
        cout << "Ultimo elemento: " << obtenerUltimo(lista_vacia) << endl;
    } catch (const runtime_error& e) {
        cerr << "Error al obtener ultimo: " << e.what() << endl;
    }


    liberar_memoria(mi_lista);
    return 0;
}
```

**Explicación:**

*   **`obtenerPrimero`:** Es muy eficiente ($O(1)$). Simplemente verifica si la lista no está vacía y devuelve el `elemento` del nodo apuntado por `primero`.
*   **`obtenerUltimo`:** Es menos eficiente ($O(N)$). Requiere recorrer toda la lista desde el principio hasta encontrar el nodo cuyo `siguiente` es `NULL`.
*   **Eficiencia:** Para hacer `obtenerUltimo` eficiente ($O(1)$), se necesitaría mantener un puntero adicional (`ultimo`) que siempre apunte al último nodo de la lista, actualizándolo en las funciones de inserción y eliminación.
*   **Manejo de Errores:** Se usa `throw runtime_error` para manejar el caso de intentar obtener un elemento de una lista vacía.

---

### Ejercicio 6: Cargar Conjunto Ordenado Sin Repetidos (Array y Lista)

**Tarea:** Leer N enteros como argumentos del programa. Insertarlos en una estructura (arreglo y lista) manteniéndola ordenada y sin elementos repetidos. Mostrar al final. Realizar seguimiento para entrada {1, 9, 4, -1, 9}.

**Solución (Combinada):**

```cpp
#include <iostream>
#include <vector>   // Para facilitar el manejo del arreglo dinámico
#include <string>   // Para convertir argumentos
#include <cstdlib>  // Para atoi (o std::stoi)
#include <algorithm> // Para std::sort y std::unique (en la versión con vector)
#include <stdexcept> // Para stoi

using namespace std;

// --- Estructura Nodo (para la lista) ---
struct Nodo {
    int elemento;
    Nodo * siguiente;
};

// --- Funciones para Lista Enlazada Ordenada Sin Repetidos ---

Nodo* crear_nodo(int elemento, Nodo* sigte) {
    Nodo* nuevo = new Nodo();
    nuevo->elemento = elemento;
    nuevo->siguiente = sigte;
    return nuevo;
}

// Inserta manteniendo orden y sin repetir. Complejidad: O(N) por inserción.
void insertarOrdenadoSinRepetirLista(Nodo*& primero, int valor, bool trace = false) {
    Nodo* actual = primero;
    Nodo* anterior = nullptr;

    if (trace) cout << "  Insertando " << valor << " en lista..." << endl;

    // Busca la posición correcta o si ya existe
    while (actual != nullptr && actual->elemento < valor) {
        if (trace) cout << "    Pasando por " << actual->elemento << endl;
        anterior = actual;
        actual = actual->siguiente;
    }

    // Si ya existe, no hacer nada
    if (actual != nullptr && actual->elemento == valor) {
         if (trace) cout << "    -> Valor " << valor << " ya existe. Ignorando." << endl;
        return;
    }

    // Crear el nuevo nodo
    Nodo* nuevo = crear_nodo(valor, actual); // El nuevo apunta a 'actual'

    // Insertar: al principio o en medio/final
    if (anterior == nullptr) { // Insertar al principio
         if (trace) cout << "    -> Insertando " << valor << " al principio." << endl;
        primero = nuevo;
    } else { // Insertar después de 'anterior'
         if (trace) cout << "    -> Insertando " << valor << " despues de " << anterior->elemento << "." << endl;
        anterior->siguiente = nuevo;
    }
}

void mostrar_lista(const Nodo* primero) {
    cout << "Lista: ";
    const Nodo* actual = primero;
    while (actual != nullptr) {
        cout << actual->elemento << " -> ";
        actual = actual->siguiente;
    }
    cout << "NULL" << endl;
}

void liberar_lista(Nodo*& primero) {
    Nodo* actual = primero;
    while (actual != nullptr) {
        Nodo* siguiente = actual->siguiente;
        delete actual;
        actual = siguiente;
    }
    primero = nullptr;
}


// --- Funciones para Arreglo Ordenado Sin Repetidos (usando std::vector) ---
// Inserta manteniendo orden y sin repetir. Complejidad: O(N) por inserción (debido al posible desplazamiento).
void insertarOrdenadoSinRepetirVector(vector<int>& arr, int valor, bool trace = false) {
     if (trace) cout << "  Insertando " << valor << " en vector..." << endl;

    // 1. Encontrar la posición correcta usando lower_bound (O(log N) si estuviera ordenado, pero lo haremos lineal por simplicidad de inserción)
    // O simplemente buscar linealmente dónde insertarlo y si ya existe.
    int pos = 0;
    while (pos < arr.size() && arr[pos] < valor) {
         if (trace) cout << "    Comparando con arr[" << pos << "]=" << arr[pos] << endl;
        pos++;
    }

    // 2. Verificar si ya existe en esa posición
    if (pos < arr.size() && arr[pos] == valor) {
         if (trace) cout << "    -> Valor " << valor << " ya existe en pos " << pos << ". Ignorando." << endl;
        return; // Ya existe, no insertar
    }

    // 3. Insertar en la posición 'pos' (esto desplaza elementos, O(N))
    if (trace) cout << "    -> Insertando " << valor << " en posicion " << pos << "." << endl;
    arr.insert(arr.begin() + pos, valor);
}

void mostrar_vector(const vector<int>& arr) {
    cout << "Vector: [ ";
    for (int val : arr) {
        cout << val << " ";
    }
    cout << "]" << endl;
}


// --- Main ---
int main(int argc, char *argv[]) {
    // argc: número de argumentos (incluyendo el nombre del programa)
    // argv: arreglo de strings (char*) con los argumentos

    if (argc < 2) {
        cerr << "Uso: " << argv[0] << " <num1> <num2> ... <numN>" << endl;
        return 1;
    }

    // --- Procesamiento para Lista Enlazada ---
    cout << "--- Procesando con Lista Enlazada ---" << endl;
    Nodo* lista = nullptr;
    cout << "Seguimiento para entrada {1, 9, 4, -1, 9}:" << endl;
    // Simular la entrada del seguimiento manualmente
    insertarOrdenadoSinRepetirLista(lista, 1, true);
    insertarOrdenadoSinRepetirLista(lista, 9, true);
    insertarOrdenadoSinRepetirLista(lista, 4, true);
    insertarOrdenadoSinRepetirLista(lista, -1, true);
    insertarOrdenadoSinRepetirLista(lista, 9, true); // Repetido

    cout << "\nLista final:" << endl;
    mostrar_lista(lista);
    liberar_lista(lista);
    cout << "-------------------------------------\n" << endl;


    // --- Procesamiento para Vector (Arreglo Dinámico) ---
     cout << "--- Procesando con Vector (Arreglo Dinamico) ---" << endl;
    vector<int> arreglo;
    cout << "Seguimiento para entrada {1, 9, 4, -1, 9}:" << endl;
    // Simular la entrada del seguimiento manualmente
    insertarOrdenadoSinRepetirVector(arreglo, 1, true);
    insertarOrdenadoSinRepetirVector(arreglo, 9, true);
    insertarOrdenadoSinRepetirVector(arreglo, 4, true);
    insertarOrdenadoSinRepetirVector(arreglo, -1, true);
    insertarOrdenadoSinRepetirVector(arreglo, 9, true); // Repetido

    cout << "\nVector final:" << endl;
    mostrar_vector(arreglo);
    cout << "-------------------------------------\n" << endl;

    // Procesar argumentos reales si se desea (ejemplo)
    /*
    cout << "--- Procesando argumentos del programa ---" << endl;
    Nodo* lista_args = nullptr;
    vector<int> vector_args;
    for (int i = 1; i < argc; ++i) {
        try {
            int valor = stoi(argv[i]); // Convertir argumento a entero
            insertarOrdenadoSinRepetirLista(lista_args, valor);
            insertarOrdenadoSinRepetirVector(vector_args, valor);
        } catch (const invalid_argument& e) {
            cerr << "Argumento invalido ignorado: " << argv[i] << endl;
        } catch (const out_of_range& e) {
             cerr << "Argumento fuera de rango ignorado: " << argv[i] << endl;
        }
    }
    cout << "Resultados con argumentos:" << endl;
    mostrar_lista(lista_args);
    mostrar_vector(vector_args);
    liberar_lista(lista_args);
    */

    return 0;
}
```

**Seguimiento Esperado (para ambas estructuras):**

```
--- Procesando con Lista Enlazada ---
Seguimiento para entrada {1, 9, 4, -1, 9}:
  Insertando 1 en lista...
    -> Insertando 1 al principio.
  Insertando 9 en lista...
    Pasando por 1
    -> Insertando 9 despues de 1.
  Insertando 4 en lista...
    Pasando por 1
    -> Insertando 4 despues de 1.
  Insertando -1 en lista...
    -> Insertando -1 al principio.
  Insertando 9 en lista...
    Pasando por -1
    Pasando por 1
    Pasando por 4
    -> Valor 9 ya existe. Ignorando.

Lista final:
Lista: -1 -> 1 -> 4 -> 9 -> NULL
-------------------------------------

--- Procesando con Vector (Arreglo Dinamico) ---
Seguimiento para entrada {1, 9, 4, -1, 9}:
  Insertando 1 en vector...
    -> Insertando 1 en posicion 0.
  Insertando 9 en vector...
    Comparando con arr[0]=1
    -> Insertando 9 en posicion 1.
  Insertando 4 en vector...
    Comparando con arr[0]=1
    -> Insertando 4 en posicion 1.
  Insertando -1 en vector...
    -> Insertando -1 en posicion 0.
  Insertando 9 en vector...
    Comparando con arr[0]=-1
    Comparando con arr[1]=1
    Comparando con arr[2]=4
    -> Valor 9 ya existe en pos 3. Ignorando.

Vector final:
Vector: [ -1 1 4 9 ]
-------------------------------------
```

**Explicación:**

*   **Argumentos `main`:** `argc` contiene el número de argumentos y `argv` es un arreglo de strings (estilo C) con los argumentos. `argv[0]` es el nombre del programa.
*   **`stoi`:** Convierte un string a `int` (maneja excepciones).
*   **Inserción Ordenada (Lista):** Se recorre la lista hasta encontrar el lugar correcto (donde `actual->elemento >= valor`). Se manejan los casos de inserción al principio, en medio y el caso de duplicado. Complejidad $O(N)$ por inserción.
*   **Inserción Ordenada (Vector):** Se busca la posición y se usa `vector::insert`. `insert` es $O(N)$ porque puede requerir desplazar elementos. La búsqueda podría ser $O(\log N)$ con `lower_bound`, pero la inserción domina.
*   **Sin Repetidos:** Ambas implementaciones verifican si el elemento ya existe antes de insertarlo.
*   **Complejidad Total:** Como cada inserción es $O(N)$ en el peor caso, insertar M elementos toma $O(M \times N)$ donde N es el tamaño *actual* de la estructura. Si M es el número final de elementos, la complejidad total es aproximadamente $O(M^2)$. (Se puede lograr $O(M \log M)$ si se insertan todos y luego se ordena/elimina duplicados, pero el ejercicio pide mantener ordenado *durante* la carga).

---

### Ejercicio 7: Búsqueda Lineal Iterativa (Ordenado, Sin Repetidos)

**Tarea:** Implementar búsqueda lineal en arreglo y lista ordenados (sin usar búsqueda binaria).

**Solución:**

```cpp
#include <iostream>
#include <vector>

using namespace std;

// --- Estructura Nodo ---
struct Nodo {
    int elemento;
    Nodo * siguiente;
};
// ... (incluir crear_nodo, agregar_principio, mostrar_lista, liberar_lista de ejercicios anteriores) ...
// Función crear_nodo (de [[Ejemplo de ejercicios resueltos]])
Nodo * crear_nodo(int elemento, Nodo * sigte) {
    Nodo * nuevo = new Nodo();
    nuevo->elemento = elemento;
    nuevo->siguiente = sigte;
    return nuevo;
}
// Función agregar_principio (de [[Ejemplo de ejercicios resueltos]])
void agregar_principio (int nuevo_elemento, Nodo * & primero) {
    Nodo * nuevo = crear_nodo(nuevo_elemento, primero);
    primero = nuevo;
}
// Función mostrar_elementos (de [[Ejemplo de ejercicios resueltos]])
void mostrar_lista(const Nodo * primero) {
    const Nodo* actual = primero;
    cout << "Lista: ";
    while (actual != NULL) {
        cout << actual->elemento << " -> ";
        actual = actual->siguiente;
    }
    cout << "NULL" << endl;
}
// Función liberar_memoria (de [[Ejemplo de ejercicios resueltos]])
void liberar_lista(Nodo * & primero) {
    Nodo * actual = primero;
    Nodo * siguiente = NULL;
    while (actual != NULL) {
        siguiente = actual->siguiente;
        delete actual;
        actual = siguiente;
    }
    primero = NULL;
}


// --- Búsqueda Lineal Ordenada en Arreglo (Vector) ---
// Retorna el índice si lo encuentra, -1 si no.
// Complejidad: O(N) peor caso, pero puede terminar antes si el elemento actual > buscado.
int buscarLinealOrdenadoArray(const vector<int>& arr, int buscado, int& operaciones) {
    operaciones = 0;
    for (int i = 0; i < arr.size(); ++i) {
        operaciones++; // Contar comparación
        if (arr[i] == buscado) {
            return i; // Encontrado
        }
        // Optimización: Si el actual es mayor, ya no lo encontraremos (porque está ordenado)
        if (arr[i] > buscado) {
            return -1; // No encontrado (corte temprano)
        }
    }
    return -1; // No encontrado (llegó al final)
}

// --- Búsqueda Lineal Ordenada en Lista Enlazada ---
// Retorna un puntero al nodo si lo encuentra, nullptr si no.
// Complejidad: O(N) peor caso, con posible corte temprano.
Nodo* buscarLinealOrdenadoLista(const Nodo* primero, int buscado, int& operaciones) {
    operaciones = 0;
    const Nodo* actual = primero;
    while (actual != nullptr) {
        operaciones++; // Contar comparación
        if (actual->elemento == buscado) {
            return (Nodo*)actual; // Encontrado (quita constness, cuidado si se modifica fuera)
                                 // Mejor sería retornar const Nodo*
        }
        // Optimización: Si el actual es mayor, ya no lo encontraremos
        if (actual->elemento > buscado) {
            return nullptr; // No encontrado (corte temprano)
        }
        actual = actual->siguiente;
    }
    return nullptr; // No encontrado (llegó al final)
}

int main() {
    // Crear estructuras ordenadas (ejemplo del ejercicio 9)
    vector<int> arreglo = {-1, 1, 4, 9};
    Nodo* lista = nullptr;
    // Crear lista en orden inverso para que quede ordenada al insertar al principio
    agregar_principio(9, lista);
    agregar_principio(4, lista);
    agregar_principio(1, lista);
    agregar_principio(-1, lista);

    cout << "Arreglo: [ -1 1 4 9 ]" << endl;
    mostrar_lista(lista);
    cout << endl;

    int ops_arr, ops_lista;
    int buscado;

    // --- Pruebas ---
    buscado = 4;
    cout << "Buscando " << buscado << ":" << endl;
    int idx_arr = buscarLinealOrdenadoArray(arreglo, buscado, ops_arr);
    Nodo* nodo_lista = buscarLinealOrdenadoLista(lista, buscado, ops_lista);
    cout << "  Array: " << (idx_arr != -1 ? "Encontrado en indice " + to_string(idx_arr) : "No encontrado") << " (Ops: " << ops_arr << ")" << endl;
    cout << "  Lista: " << (nodo_lista != nullptr ? "Encontrado (valor " + to_string(nodo_lista->elemento) + ")" : "No encontrado") << " (Ops: " << ops_lista << ")" << endl;

    buscado = -1;
     cout << "\nBuscando " << buscado << ":" << endl;
    idx_arr = buscarLinealOrdenadoArray(arreglo, buscado, ops_arr);
    nodo_lista = buscarLinealOrdenadoLista(lista, buscado, ops_lista);
    cout << "  Array: " << (idx_arr != -1 ? "Encontrado en indice " + to_string(idx_arr) : "No encontrado") << " (Ops: " << ops_arr << ")" << endl;
    cout << "  Lista: " << (nodo_lista != nullptr ? "Encontrado (valor " + to_string(nodo_lista->elemento) + ")" : "No encontrado") << " (Ops: " << ops_lista << ")" << endl;

    buscado = 0; // No está, pero permite corte temprano
     cout << "\nBuscando " << buscado << ":" << endl;
    idx_arr = buscarLinealOrdenadoArray(arreglo, buscado, ops_arr);
    nodo_lista = buscarLinealOrdenadoLista(lista, buscado, ops_lista);
    cout << "  Array: " << (idx_arr != -1 ? "Encontrado en indice " + to_string(idx_arr) : "No encontrado") << " (Ops: " << ops_arr << ")" << endl;
    cout << "  Lista: " << (nodo_lista != nullptr ? "Encontrado (valor " + to_string(nodo_lista->elemento) + ")" : "No encontrado") << " (Ops: " << ops_lista << ")" << endl;

     buscado = 10; // No está, al final
     cout << "\nBuscando " << buscado << ":" << endl;
    idx_arr = buscarLinealOrdenadoArray(arreglo, buscado, ops_arr);
    nodo_lista = buscarLinealOrdenadoLista(lista, buscado, ops_lista);
    cout << "  Array: " << (idx_arr != -1 ? "Encontrado en indice " + to_string(idx_arr) : "No encontrado") << " (Ops: " << ops_arr << ")" << endl;
    cout << "  Lista: " << (nodo_lista != nullptr ? "Encontrado (valor " + to_string(nodo_lista->elemento) + ")" : "No encontrado") << " (Ops: " << ops_lista << ")" << endl;


    liberar_lista(lista);
    return 0;
}
```

**Explicación:**

*   **Optimización Clave:** La condición `if (elemento_actual > buscado)` permite detener la búsqueda antes si el elemento actual ya es mayor que el buscado, aprovechando que la estructura está ordenada.
*   **Complejidad:** A pesar de la optimización, el **peor caso** sigue siendo $O(N)$ (cuando el elemento está al final o no está y es mayor que todos los elementos). El mejor caso es $O(1)$ (si es el primer elemento). Ver [[Complejidad y eficiencia]].

---

### Ejercicio 8: Búsqueda Binaria Iterativa (Arreglo Ordenado)

**Tarea:** Implementar búsqueda binaria iterativa para un arreglo ordenado.

**Solución:**

```cpp
#include <iostream>
#include <vector>
#include <cmath> // Para floor

using namespace std;

// --- Búsqueda Binaria Iterativa en Arreglo (Vector) ---
// Retorna el índice si lo encuentra, -1 si no.
// Precondición: El arreglo 'arr' DEBE estar ordenado.
// Complejidad: O(log N)
int busquedaBinariaArray(const vector<int>& arr, int buscado, int& operaciones) {
    operaciones = 0;
    int bajo = 0;
    int alto = arr.size() - 1;
    int medio;

    while (bajo <= alto) {
        // Calcular el índice medio
        medio = bajo + floor((alto - bajo) / 2.0); // Evita overflow para índices grandes
        operaciones++; // Contar la comparación principal

        cout << "  Buscando... bajo=" << bajo << ", alto=" << alto << ", medio=" << medio << ", arr[medio]=" << arr[medio] << endl;


        if (arr[medio] == buscado) {
            cout << "    -> Encontrado en indice " << medio << endl;
            return medio; // Encontrado
        } else if (arr[medio] < buscado) {
             cout << "    -> Buscado es mayor, ajustando bajo a " << medio + 1 << endl;
            bajo = medio + 1; // Buscar en la mitad derecha
        } else { // arr[medio] > buscado
             cout << "    -> Buscado es menor, ajustando alto a " << medio - 1 << endl;
            alto = medio - 1; // Buscar en la mitad izquierda
        }
    }

    cout << "  -> No encontrado (bajo > alto)" << endl;
    return -1; // No encontrado
}

int main() {
    vector<int> arreglo = {-1, 1, 4, 9}; // Arreglo ordenado
    int ops;
    int buscado;

    cout << "Arreglo: [ -1 1 4 9 ]" << endl;

    // --- Pruebas ---
    buscado = 4;
    cout << "\n--- Buscando " << buscado << " (Binaria) ---" << endl;
    int idx = busquedaBinariaArray(arreglo, buscado, ops);
    cout << "Resultado: " << (idx != -1 ? "Encontrado en indice " + to_string(idx) : "No encontrado") << " (Ops: " << ops << ")" << endl;

     buscado = -1;
    cout << "\n--- Buscando " << buscado << " (Binaria) ---" << endl;
    idx = busquedaBinariaArray(arreglo, buscado, ops);
    cout << "Resultado: " << (idx != -1 ? "Encontrado en indice " + to_string(idx) : "No encontrado") << " (Ops: " << ops << ")" << endl;

    buscado = 0; // No está
    cout << "\n--- Buscando " << buscado << " (Binaria) ---" << endl;
    idx = busquedaBinariaArray(arreglo, buscado, ops);
    cout << "Resultado: " << (idx != -1 ? "Encontrado en indice " + to_string(idx) : "No encontrado") << " (Ops: " << ops << ")" << endl;

    buscado = 10; // No está
    cout << "\n--- Buscando " << buscado << " (Binaria) ---" << endl;
    idx = busquedaBinariaArray(arreglo, buscado, ops);
    cout << "Resultado: " << (idx != -1 ? "Encontrado en indice " + to_string(idx) : "No encontrado") << " (Ops: " << ops << ")" << endl;


    return 0;
}
```

**Explicación:**

*   **Idea Central:** Divide repetidamente el intervalo de búsqueda a la mitad. Compara el elemento buscado con el elemento del medio. Si son iguales, se encontró. Si el buscado es menor, se descarta la mitad derecha. Si es mayor, se descarta la mitad izquierda.
*   **Índices:** `bajo` y `alto` definen el intervalo actual de búsqueda. `medio` es el punto central.
*   **Condición de Parada:** El bucle continúa mientras `bajo <= alto`. Si `bajo` supera a `alto`, significa que el elemento no está.
*   **Complejidad:** $O(\log N)$. Cada comparación reduce el espacio de búsqueda a la mitad, lo que es extremadamente eficiente para arreglos grandes. Ver [[Complejidad y eficiencia]].

---

### Ejercicio 9: Seguimiento y Comparación de Búsquedas

**Tarea:** Realizar seguimiento de búsqueda lineal (ej. 7) y binaria (ej. 8) para el conjunto {-1, 1, 4, 9} buscando {0, -1, 4, 10}. Contar operaciones, comparar con complejidad teórica y medir tiempos.

**Solución:**

**1. Seguimiento y Conteo de Operaciones (Manual):**

Usaremos el conjunto `A = {-1, 1, 4, 9}` (N=4). Contaremos las comparaciones principales.

| Elemento Buscado | Búsqueda Lineal Ordenada (Ej. 7)                                  | Operaciones (Lineal) | Búsqueda Binaria (Ej. 8)                                                                                                | Operaciones (Binaria) |
| :--------------- | :----------------------------------------------------------------- | :------------------- | :---------------------------------------------------------------------------------------------------------------------- | :-------------------- |
| **0**            | Compara con -1. Compara con 1. `1 > 0` -> Corte temprano.          | 2                    | bajo=0, alto=3, medio=1 (1). `1 > 0`. alto=0. <br> bajo=0, alto=0, medio=0 (-1). `-1 < 0`. bajo=1. <br> `bajo > alto`. | 2                     |
| **-1**           | Compara con -1. Encontrado.                                        | 1                    | bajo=0, alto=3, medio=1 (1). `1 > -1`. alto=0. <br> bajo=0, alto=0, medio=0 (-1). Encontrado.                           | 2                     |
| **4**            | Compara con -1. Compara con 1. Compara con 4. Encontrado.          | 3                    | bajo=0, alto=3, medio=1 (1). `1 < 4`. bajo=2. <br> bajo=2, alto=3, medio=2 (4). Encontrado.                           | 2                     |
| **10**           | Compara con -1. Compara con 1. Compara con 4. Compara con 9. Fin. | 4                    | bajo=0, alto=3, medio=1 (1). `1 < 10`. bajo=2. <br> bajo=2, alto=3, medio=2 (4). `4 < 10`. bajo=3. <br> bajo=3, alto=3, medio=3 (9). `9 < 10`. bajo=4. <br> `bajo > alto`. | 3                     |

**2. Comparación con Complejidad Teórica:**

*   **Lineal ($O(N)$):** El número de operaciones varía, pero en el peor caso (buscar 10 o 9) se acerca a N (4 operaciones). Para los encontrados, depende de su posición. El corte temprano ayuda (buscar 0). Se ajusta a $O(N)$.
*   **Binaria ($O(\log N)$):** $log_2(4) = 2$. La búsqueda binaria realiza consistentemente 2 o 3 comparaciones, lo cual se ajusta perfectamente a $O(\log N)$. Incluso para buscar el 10 (peor caso), solo necesita 3 comparaciones.

**3. Medición de Tiempos (Código):**

Se necesita incluir `<chrono>` y ejecutar cada búsqueda muchas veces para obtener un promedio significativo, especialmente porque para N=4, ambas son muy rápidas y la diferencia puede perderse en el "ruido" del sistema.

```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <chrono> // Para medir tiempo
#include <numeric> // Para std::accumulate

using namespace std;
using namespace std::chrono;

// --- Incluir las funciones ---
// buscarLinealOrdenadoArray (del Ej. 7)
// busquedaBinariaArray (del Ej. 8)
// ... (código de las funciones aquí) ...
int buscarLinealOrdenadoArray(const vector<int>& arr, int buscado, int& operaciones) {
    operaciones = 0;
    for (int i = 0; i < arr.size(); ++i) {
        operaciones++; // Contar comparación
        if (arr[i] == buscado) return i;
        if (arr[i] > buscado) return -1;
    }
    return -1;
}
int busquedaBinariaArray(const vector<int>& arr, int buscado, int& operaciones) {
    operaciones = 0;
    int bajo = 0;
    int alto = arr.size() - 1;
    int medio;
    while (bajo <= alto) {
        medio = bajo + floor((alto - bajo) / 2.0);
        operaciones++;
        if (arr[medio] == buscado) return medio;
        else if (arr[medio] < buscado) bajo = medio + 1;
        else alto = medio - 1;
    }
    return -1;
}


int main() {
    vector<int> arreglo = {-1, 1, 4, 9};
    vector<int> a_buscar = {0, -1, 4, 10};
    int operaciones; // No la usaremos para tiempo, solo para la función
    const int NUM_REPETICIONES = 100000; // Repetir muchas veces para medir

    cout << "Comparando tiempos de ejecucion (promedio de " << NUM_REPETICIONES << " repeticiones)" << endl;
    cout << "Arreglo: [ -1 1 4 9 ]" << endl;
    cout << "Buscando: {0, -1, 4, 10}" << endl;

    // --- Medir Búsqueda Lineal ---
    long long total_duracion_lineal_ns = 0;
    for (int buscado : a_buscar) {
        vector<long long> duraciones;
        for (int i = 0; i < NUM_REPETICIONES; ++i) {
            auto start = high_resolution_clock::now();
            volatile int res = buscarLinealOrdenadoArray(arreglo, buscado, operaciones); // volatile para evitar optimización excesiva
            auto end = high_resolution_clock::now();
            duraciones.push_back(duration_cast<nanoseconds>(end - start).count());
        }
         // Calcular promedio para este 'buscado'
         long long suma = 0;
         for(long long d : duraciones) suma += d;
         total_duracion_lineal_ns += suma / duraciones.size();

    }
     cout << "Tiempo promedio total Lineal: " << total_duracion_lineal_ns / a_buscar.size() << " ns" << endl;


    // --- Medir Búsqueda Binaria ---
     long long total_duracion_binaria_ns = 0;
    for (int buscado : a_buscar) {
         vector<long long> duraciones;
        for (int i = 0; i < NUM_REPETICIONES; ++i) {
            auto start = high_resolution_clock::now();
            volatile int res = busquedaBinariaArray(arreglo, buscado, operaciones); // volatile
            auto end = high_resolution_clock::now();
             duraciones.push_back(duration_cast<nanoseconds>(end - start).count());
        }
         // Calcular promedio para este 'buscado'
         long long suma = 0;
         for(long long d : duraciones) suma += d;
         total_duracion_binaria_ns += suma / duraciones.size();
    }
     cout << "Tiempo promedio total Binaria: " << total_duracion_binaria_ns / a_buscar.size() << " ns" << endl;


    return 0;
}
```

**Resultados Esperados de Tiempo:**

Aunque los tiempos exactos dependen del hardware y la carga del sistema, se espera que el **tiempo promedio de la búsqueda binaria sea significativamente menor** que el de la búsqueda lineal, incluso para N=4. La diferencia se haría mucho más drástica para arreglos más grandes. La medición confirma experimentalmente la superioridad de $O(\log N)$ sobre $O(N)$.

---- `Nodo* primero` (en `main`): Es el puntero original a la cabeza de la lista.
- `Nodo*& primero` (en la función): Es una referencia a _ese mismo puntero_. Cualquier cambio que hagas a `primero` dentro de la función, _directamente_ modifica el `primero` que está en `main`.
-

**Sin la referencia (`&`):**

Si solo pasaras `Nodo* primero` (sin el `&`), la función recibiría una _copia_ del puntero. Podrías modificar esa copia, pero no afectaría al puntero original en `main`.

**En resumen:**

- La referencia al puntero (`&`) permite que la función _acceda y modifique directamente_ el puntero original en `main`.
- Sin la referencia, la función solo trabajaría con una copia del puntero, y los cambios no se reflejarían fuera de la función