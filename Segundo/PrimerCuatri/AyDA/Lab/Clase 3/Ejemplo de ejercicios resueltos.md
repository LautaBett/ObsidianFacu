	¡Claro! Analicemos y expliquemos estos ejercicios de C++ centrados en la memoria y los punteros, en formato Markdown para Obsidian.

---

## TP MEMORIA - Ejercicio 1: Agenda de Contactos (Array Estático)

Este ejercicio implementa una agenda simple usando un **arreglo estático** de estructuras `Contacto`. La memoria para el arreglo se asigna en el **Stack** cuando se declara en `main`.

```markdown
#include <iostream>
#include <string> // Incluir para std::string
#include <cstring> // No parece necesario aquí
using namespace std;

// Define un máximo de contactos para el arreglo estático
const int MAX_CONTACTOS = 10;

// Estructura para almacenar la información de un contacto
struct Contacto {
    string nombre;
    int telefono; // Asumiendo que el teléfono es un número entero
};

// --- Función buscarPorNumero ---
// Busca un contacto por su número de teléfono en el arreglo.
// Parámetros:
//   - numero: El teléfono a buscar.
//   - contactos: Un puntero al inicio del arreglo de Contacto. 
//                (Nota: 'const Contacto &*' es inusual, probablemente debería ser 'const Contacto*')
// Retorna: El nombre del contacto si se encuentra, o una cadena vacía si no.
string buscarPorNumero(int numero, const Contacto* contactos) { // Tipo corregido
    const Contacto* ptr = contactos; // Puntero para recorrer el arreglo
    string nombre = ""; // Nombre a retornar, inicializado como no encontrado
    int i = 0;
    bool encontro = false;

    // Recorre el arreglo mientras no se encuentre y no se supere el máximo
    while (!encontro && i < MAX_CONTACTOS) {
        // Verifica si el contacto actual tiene nombre (no está vacío) y coincide el teléfono
        // Se asume que un nombre vacío indica un slot no utilizado.
        if (ptr->nombre != "" && ptr->telefono == numero ) {
            nombre = ptr->nombre; // Guarda el nombre encontrado
            encontro = true;      // Marca como encontrado para salir del bucle
        }
        i++;    // Incrementa el índice
        ptr++;  // Mueve el puntero al siguiente Contacto en memoria
    }
    return nombre; // Devuelve el nombre encontrado o ""
}

// --- Función buscarPorNombre ---
// Busca un contacto por su nombre en el arreglo.
// Parámetros:
//   - nombre: El nombre a buscar.
//   - contactos: Puntero al inicio del arreglo de Contacto. (Misma nota sobre el tipo)
// Retorna: El teléfono del contacto si se encuentra, o -1 si no.
int buscarPorNombre(string nombre, const Contacto* contactos) { // Tipo corregido
    const Contacto* ptr = contactos; // Puntero para recorrer
    int telefono = -1; // Teléfono a retornar, inicializado como no encontrado
    int i = 0;
    bool encontro = false;

    // Recorre el arreglo
    while (!encontro && i < MAX_CONTACTOS) {
        // Compara nombres
        if (ptr->nombre == nombre) {
            telefono = ptr->telefono; // Guarda el teléfono
            encontro = true;          // Marca como encontrado
        }
        i++;    // Incrementa índice
        ptr++;  // Mueve el puntero
    }
    return telefono; // Devuelve el teléfono o -1
}

// --- Función mostrarContactos ---
// Muestra todos los contactos "válidos" (con nombre no vacío) en la consola.
// Parámetros:
//   - contactos: Puntero al inicio del arreglo de Contacto. (Misma nota sobre el tipo)
void mostrarContactos(const Contacto* contactos) { // Tipo corregido
    cout << "\nLista de Contactos:\n";
    // Recorre el arreglo usando indexación (equivalente a usar puntero ptr++)
    for (int i = 0; i < MAX_CONTACTOS; i++) {
        // Si el nombre no está vacío, muestra el contacto
        if (contactos[i].nombre != "") { // Corrección: faltaba cerrar comillas
            cout << contactos[i].nombre << " - " << contactos[i].telefono << endl;
        }
    }
}

// --- Función main ---
int main() {
    // 1. Declara e inicializa PARCIALMENTE un arreglo de Contacto en el STACK.
    //    Los elementos no inicializados explícitamente tendrán valores por defecto
    //    (string vacío, int 0).
    Contacto contactos[MAX_CONTACTOS] = {
        {"Juan", 15678410}, // Asumiendo que los teléfonos son int
        {"Ana", 15974417},
        {"Pedro", 15570327},
        {"Maria", 15609411},
        {"Carlos", 15470424}
        // Los índices 5 a 9 quedan con nombre="" y telefono=0
    };

    // 2. Llama a buscarPorNumero.
    //    Nota: El número debe ser int, no string.
    cout << "Buscando 15470424: " << buscarPorNumero(15470424, contactos) << endl; // Corregido a int

    // 3. Llama a buscarPorNombre.
    cout << "Buscando Ana: " << buscarPorNombre("Ana", contactos) << endl;

    // 4. Llama a mostrarContactos para imprimir la lista.
    mostrarContactos(contactos);

    // 5. Finaliza el programa.
    return 0;
}

/* --- Análisis del Stack Trace (Proporcionado) ---
La información del stack trace ilustra cómo se maneja la memoria durante las llamadas a funciones:

*   'main': Contiene el arreglo 'contactos' en su espacio de memoria local (Stack).
*   'buscarPorNumero' (llamada desde main línea 2):
    *   Parámetros: 'numero' (valor 15470424), 'contactos' (dirección del arreglo, ej. 0x1000h).
    *   Locales: 'ptr' (puntero que avanza hasta 0x10F0h, la dirección de "Carlos"), 'nombre' (se actualiza a "Carlos"), 'i' (llega a 5, índice de Carlos), 'encontro' (se vuelve true).
    *   Retorna a 'main' línea 2.
*   'buscarPorNombre' (llamada desde main línea 3):
    *   Parámetros: 'nombre' ("Ana"), 'contactos' (misma dirección 0x1000h).
    *   Locales: 'ptr' (avanza hasta 0x1060h, dirección de "Ana"), 'telefono' (se actualiza al de Ana), 'i' (llega a 1, índice de Ana), 'encontro' (se vuelve true).
    *   Retorna a 'main' línea 3.
*   'mostrarContactos' (llamada desde main línea 4):
    *   Parámetros: 'contactos' (misma dirección 0x1000h).
    *   Locales: 'i' (itera de 0 a 9).
    *   Retorna a 'main' línea 4.

Esto muestra cómo se pasan los parámetros (el arreglo se pasa como puntero/dirección) y cómo las variables locales existen solo durante la ejecución de cada función en el Stack.
*/
```

**Conceptos Clave de Memoria/Punteros:**

*   **Arreglo Estático:** `contactos[MAX_CONTACTOS]` se aloja en el **Stack**. Su tamaño es fijo en tiempo de compilación.
*   **Paso de Arreglos:** Cuando pasas un arreglo a una función, en realidad pasas un **puntero** a su primer elemento. No se copia todo el arreglo.
*   **Aritmética de Punteros:** `ptr++` avanza el puntero a la siguiente estructura `Contacto` en memoria. El compilador sabe cuánto avanzar porque conoce `sizeof(Contacto)`.
*   **Acceso con Puntero:** `ptr->nombre` accede al miembro `nombre` de la estructura a la que apunta `ptr`. Es equivalente a `(*ptr).nombre`.
*   **Acceso con Índice:** `contactos[i].nombre` accede al miembro `nombre` del i-ésimo elemento del arreglo.

---

## TP MEMORIA - Ejercicio 2: Lista Enlazada (Memoria Dinámica)

Este ejercicio implementa una **lista enlazada simple** usando nodos `struct Nodo`. La memoria para cada nodo se asigna **dinámicamente** en el **Heap** usando `new`.

```markdown
#include <iostream>
#include <cstdlib> // Necesario para NULL (aunque nullptr es preferible en C++ moderno)
using namespace std;

// Estructura del Nodo para la lista enlazada
struct Nodo {
    int elemento;      // El dato almacenado en el nodo
    Nodo * siguiente; // Puntero al siguiente nodo en la lista (o NULL/nullptr si es el último)
};

// --- Función crear_nodo ---
// Crea un nuevo nodo en el HEAP.
// Parámetros:
//   - elemento: El valor a almacenar en el nodo.
//   - sigte: El puntero al que apuntará el 'siguiente' del nuevo nodo.
// Retorna: Un puntero a la dirección del nodo recién creado en el Heap.
Nodo * crear_nodo(int elemento, Nodo * sigte) {
    // 1. Solicita memoria en el Heap para un objeto Nodo.
    Nodo * nuevo = new Nodo();
    // 2. Asigna los valores a los miembros del nuevo nodo.
    nuevo->elemento = elemento;
    nuevo->siguiente = sigte;
    // 3. Devuelve el puntero (dirección) al nuevo nodo.
    return nuevo;
}

// --- Función agregar_final ---
// Agrega un nuevo elemento al final de la lista enlazada.
// Parámetros:
//   - nuevo_elemento: El valor a agregar.
//   - primero: REFERENCIA al puntero del primer nodo. Se usa referencia (&)
//              para poder modificar el puntero 'primero' original si la lista está vacía.
void agregar_final(int nuevo_elemento, Nodo * & primero) {
    // Crea el nuevo nodo. Su 'siguiente' será NULL porque irá al final.
    Nodo * nuevo = crear_nodo(nuevo_elemento, NULL); // O nullptr

    // Caso 1: La lista está vacía.
    if (primero == NULL) {
        // El nuevo nodo se convierte en el primero (y único) nodo.
        // Se modifica el 'primero' original gracias a la referencia (&).
        primero = nuevo;
    }
    // Caso 2: La lista NO está vacía.
    else {
        Nodo * actual = primero; // Puntero temporal para recorrer la lista
        // Recorre la lista hasta encontrar el ÚLTIMO nodo
        // El último nodo es aquel cuyo 'siguiente' es NULL.
        while (actual->siguiente != NULL) {
            actual = actual->siguiente; // Avanza al siguiente nodo
        }
        // Enlaza el 'siguiente' del último nodo actual al nuevo nodo.
        actual->siguiente = nuevo;
    }
}

// --- Función agregar_principio ---
// Agrega un nuevo elemento al principio de la lista enlazada.
// Parámetros:
//   - nuevo_elemento: El valor a agregar.
//   - primero: REFERENCIA al puntero del primer nodo. Necesario para
//              actualizar cuál es el nuevo primer nodo.
void agregar_principio (int nuevo_elemento, Nodo * & primero) {
    // 1. Crea un nuevo nodo. El 'siguiente' de este nuevo nodo debe ser
    //    el nodo que ACTUALMENTE es el primero.
    Nodo * nuevo = crear_nodo(nuevo_elemento, primero);
    // 2. Actualiza el puntero 'primero' para que apunte a este nuevo nodo.
    //    Se modifica el 'primero' original gracias a la referencia (&).
    primero = nuevo;
}

// --- Función mostrar_elementos ---
// Muestra todos los elementos de la lista en la consola.
// Parámetros:
//   - primero: Puntero al primer nodo. Se pasa por valor (copia del puntero),
//              ya que no necesitamos modificar la lista original, solo leerla.
//              Usar 'const' indica que la función no modificará los nodos.
void mostrar_elementos(const Nodo * primero) {
    const Nodo* actual = primero; // Usa un puntero local para recorrer
    while (actual != NULL) { // Mientras no lleguemos al final de la lista
        cout << actual->elemento << " -> "; // Imprime el elemento actual
        actual = actual->siguiente;       // Avanza al siguiente nodo
    }
    cout << "NULL" << endl; // Indica el final de la lista
}

// --- Función eliminar_elemento ---
// Elimina la primera ocurrencia de un nodo con 'elemento_borrar'.
// Parámetros:
//   - primero: REFERENCIA al puntero del primer nodo. Necesario por si
//              se borra el primer elemento.
//   - elemento_borrar: El valor del nodo a eliminar.
// Retorna: true si se encontró y eliminó el elemento, false si no se encontró.
bool eliminar_elemento(Nodo * & primero, int elemento_borrar) {
    Nodo * actual = primero; // Puntero para recorrer
    Nodo * anterior = NULL;  // Puntero al nodo anterior al actual

    // Busca el nodo a borrar, manteniendo 'anterior' un paso atrás.
    while (actual != NULL && actual->elemento != elemento_borrar) {
        anterior = actual;
        actual = actual->siguiente;
    }

    // Si actual es NULL, el elemento no se encontró en la lista.
    if (actual == NULL) {
        return false;
    }

    // Si se encontró el elemento (actual != NULL):
    // Caso 1: El nodo a borrar es el PRIMERO (anterior es NULL).
    if (anterior == NULL) {
        primero = actual->siguiente; // El nuevo 'primero' es el siguiente del borrado.
    }
    // Caso 2: El nodo a borrar está en medio o al final.
    else {
        // El 'siguiente' del nodo anterior ahora apunta al nodo que sigue al borrado,
        // "saltándose" el nodo 'actual'.
        anterior->siguiente = actual->siguiente;
    }

    // Libera la memoria del nodo borrado (que está apuntado por 'actual').
    delete actual;
    // actual = NULL; // Opcional, buena práctica si se siguiera usando 'actual'.

    return true; // Indica que se eliminó correctamente.
}

// --- Función liberar_memoria ---
// Libera TODA la memoria asignada dinámicamente para los nodos de la lista.
// ¡Es crucial llamar a esta función antes de terminar el programa para evitar memory leaks!
// Parámetros:
//   - primero: REFERENCIA al puntero del primer nodo. Se necesita para ponerlo
//              a NULL al final, indicando que la lista está vacía.
void liberar_memoria(Nodo * & primero) {
    Nodo * actual = primero; // Puntero para recorrer
    Nodo * siguiente = NULL; // Puntero temporal para guardar el siguiente nodo

    while (actual != NULL) {
        siguiente = actual->siguiente; // Guarda el puntero al siguiente NODO
        cout << "Liberando nodo con elemento: " << actual->elemento << endl; // Mensaje opcional
        delete actual;                 // Libera la memoria del nodo ACTUAL
        actual = siguiente;            // Avanza al siguiente nodo guardado
    }
    // Al final, establece 'primero' a NULL para reflejar que la lista está vacía
    // y evitar un puntero colgante (dangling pointer).
    primero = NULL;
}

// --- Función main ---
int main() {
    // Inicializa la lista como vacía. 'primero' es un puntero en el Stack.
    Nodo * primero = NULL;

    cout << "\nSecuencia con un solo valor (agrega al principio): " << endl;
    agregar_principio(4, primero); // Lista: 4 -> NULL
    mostrar_elementos(primero);

    cout << "\nSecuencia con dos valores (agrega al final): " << endl;
    agregar_final(11, primero); // Lista: 4 -> 11 -> NULL
    mostrar_elementos(primero);

    cout << "\nSecuencia con tres valores (agrega al principio): " << endl;
    agregar_principio(1991, primero); // Lista: 1991 -> 4 -> 11 -> NULL
    mostrar_elementos(primero);

    // Intenta eliminar el nodo con valor 11.
    bool elimino = eliminar_elemento(primero, 11); // Lista: 1991 -> 4 -> NULL
    if (elimino) {
        cout << "\nSecuencia luego de eliminar el 11: " << endl;
        mostrar_elementos(primero);
    } else {
        cout << "\nElemento 11 no encontrado para eliminar." << endl;
    }

    // ¡MUY IMPORTANTE! Libera toda la memoria del Heap usada por la lista.
    cout << "\nLiberando memoria de la lista..." << endl;
    liberar_memoria(primero);
    cout << "Memoria liberada. Estado final de la lista:" << endl;
    mostrar_elementos(primero); // Debería mostrar "NULL"

    return 0; // Termina el programa.
}
```

**Conceptos Clave de Memoria/Punteros:**

*   **Memoria Dinámica (Heap):** Los nodos (`Nodo`) se crean en el **Heap** usando `new`. El tamaño de la lista puede crecer y decrecer durante la ejecución.
*   **`new`:** Operador que solicita memoria del Heap. Devuelve un **puntero** a la memoria asignada.
*   **`delete`:** Operador que libera la memoria previamente asignada con `new`. Es **responsabilidad del programador** liberar la memoria para evitar **memory leaks**.
*   **Punteros:** Esenciales para enlazar los nodos (`siguiente`) y para mantener una referencia al inicio de la lista (`primero`).
*   **`nullptr` (o `NULL`):** Valor especial que indica que un puntero no apunta a ninguna dirección válida. Se usa para marcar el final de la lista y para inicializar punteros.
*   **Paso por Referencia (`&`):** `Nodo*& primero` permite a funciones como `agregar_principio`, `agregar_final`, `eliminar_elemento` y `liberar_memoria` modificar el puntero `primero` original que está en `main`. Esto es crucial cuando la operación afecta al primer nodo de la lista o vacía la lista.
*   **Memory Leaks:** Si olvidas llamar a `liberar_memoria` (o si `eliminar_elemento` no usara `delete`), la memoria de los nodos permanecería ocupada en el Heap pero inaccesible después de que `main` termine.
*   **Dangling Pointers:** Si `liberar_memoria` no pusiera `primero = NULL` al final, `primero` en `main` seguiría apuntando a una dirección de memoria que ya ha sido liberada, lo cual es peligroso si se intentara usar después.

---