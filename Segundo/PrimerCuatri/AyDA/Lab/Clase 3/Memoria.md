# Resumen: Administración de Memoria en C++ (Basado en Material AyDA I - UNICEN)

Este resumen cubre cómo C++ organiza y administra la memoria durante la ejecución de un programa, enfocándose en la memoria estática, dinámica (heap), punteros y problemas comunes.

## 1. Organización de la Memoria del Programa

Cuando un programa C++ se ejecuta, el sistema operativo le asigna memoria virtual, típicamente dividida en estas secciones principales:

1.  **Segmento de Código (Text):** Contiene las instrucciones compiladas del programa (código máquina). Generalmente de solo lectura.
2.  **Segmento de Datos (Data Segment):**
    *   **Datos Inicializados:** Variables globales y estáticas que tienen un valor inicial asignado en el código.
    *   **BSS (Block Started by Symbol):** Variables globales y estáticas no inicializadas (o inicializadas a cero).
    *   *Vida útil:* Duran toda la ejecución del programa. Administradas por el sistema.
3.  **Stack (Pila):**
    *   **Uso:** Almacena variables locales de funciones, parámetros de funciones, direcciones de retorno (para saber a dónde volver después de llamar a una función).
    *   **Gestión:** **Automática** por el sistema operativo/compilador. Funciona como una pila (LIFO - Last In, First Out). La memoria se asigna al entrar a una función y se libera automáticamente al salir.
    *   **Tamaño:** **Limitado** y fijo al inicio del programa. Si se excede (ej. recursión muy profunda o variables locales muy grandes), ocurre un **Stack Overflow**.
    *   **Acceso:** Muy rápido.
4.  **Heap (Montón):**
    *   **Uso:** Almacena memoria asignada **dinámicamente** durante la ejecución usando los operadores `new` y `new[]`.
    *   **Gestión:** **Manual** por el programador. **Es responsabilidad del programador liberar (`delete`, `delete[]`) la memoria cuando ya no se necesita.**
    *   **Tamaño:** Grande, limitado principalmente por la memoria RAM disponible en el sistema. Puede crecer y decrecer durante la ejecución.
    *   **Acceso:** Más lento que el Stack debido a la necesidad de buscar bloques libres y gestionar la asignación/liberación.

### Comparación Rápida: Stack vs. Heap

| Característica | Stack (Pila)                     | Heap (Montón)                       |
| :------------- | :------------------------------- | :---------------------------------- |
| **Ubicación**  | Stack                            | Heap                                |
| **Gestión**    | Sistema Operativo (Automática)   | Usuario/Programador (Manual)      |
| **Cantidad**   | Fija y limitada                  | Variable, limitada por RAM        |
| **Asignación** | Al entrar a función/bloque       | Explícita con `new` / `new[]`     |
| **Liberación** | Automática al salir              | Explícita con `delete` / `delete[]` |
| **Acceso**     | Rápido                           | Más lento                           |
| **Fragmentación**| No (generalmente)              | Sí (puede ocurrir)                |
| **Uso Típico** | Variables locales, parámetros    | Objetos grandes, datos persistentes |

## 2. Acceso a Memoria y Tipos Primitivos

*   Los **nombres de variables** son etiquetas que el compilador traduce a **direcciones de memoria**.
*   Leer/Escribir una variable implica enviar esa dirección a la memoria para obtener/almacenar los bits del valor.
*   **Tipos Primitivos (int, float, char, etc.):**
    *   Ocupan un número **fijo** de bytes.
    *   Esos bytes están **contiguos** (uno al lado del otro).
    *   Representan un **único valor**.
    *   *Nota:* `float`/`double` usan notación científica interna; `char` usa códigos ASCII (o similar).

## 3. Punteros

*   **Definición:** Variables especiales cuyo valor es una **dirección de memoria** de otra variable.
*   **Declaración:** Se usa el asterisco (`*`). El tipo del puntero debe coincidir con el tipo de la variable a la que apuntará.
    ```cpp
    int variable = 14;
    int* ptr_variable; // Declara un puntero a un entero (aún no apunta a nada útil)
    ```
*   **Operador de Dirección (`&`):** Obtiene la dirección de memoria de una variable. Se usa para asignar una dirección a un puntero.
    ```cpp
    ptr_variable = &variable; // ptr_variable ahora almacena la dirección de 'variable'
    ```
*   **Operador de Desreferenciación (`*`):** Accede al **valor** almacenado en la dirección a la que apunta el puntero.
    ```cpp
    cout << ptr_variable;  // Imprime la dirección de memoria (ej. 0x7ffc1234)
    cout << *ptr_variable; // Imprime el valor almacenado en esa dirección (14)
    
    *ptr_variable = 20;   // Cambia el valor de 'variable' a 20 a través del puntero
    cout << variable;     // Imprime 20
    ```
*   **Dirección del Puntero Mismo:** Un puntero también es una variable y tiene su propia dirección (generalmente en el Stack si es una variable local).
    ```cpp
    cout << &ptr_variable; // Imprime la dirección donde está almacenado el propio puntero
    ```

## 4. Memoria Dinámica (Heap)

*   Permite solicitar memoria **durante la ejecución**.
*   **Operador `new`:** Reserva memoria en el Heap y devuelve un puntero (la dirección) a esa memoria.
    ```cpp
    int* ptr_dinamico = new int; // Reserva espacio para UN entero en el Heap
    *ptr_dinamico = 14;         // Almacena 14 en el espacio reservado
    ```
*   **Operador `delete`:** Libera la memoria del Heap previamente reservada con `new`. **Es fundamental hacerlo para evitar memory leaks.**
    ```cpp
    delete ptr_dinamico; // Devuelve la memoria al sistema
    ```
*   **`nullptr`:** Constante que representa un puntero nulo (no apunta a ninguna dirección válida). Es buena práctica asignar `nullptr` a un puntero después de usar `delete`.
    ```cpp
    ptr_dinamico = nullptr; // Indica que el puntero ya no apunta a memoria válida
    ```
*   **Bloques Contiguos (Arreglos Dinámicos):** Se usa `new tipo[tamaño]` para reservar espacio para un arreglo en el Heap.
    ```cpp
    int* ptr_bloque = new int[4]; // Reserva espacio para 4 enteros contiguos en el Heap
    ```
*   **Acceso a Arreglos Dinámicos:**
    *   Notación de corchetes: `ptr_bloque[2] = 10;`
    *   Aritmética de punteros: `*(ptr_bloque + 3) = 70;` (Avanza 3 posiciones *del tamaño del tipo* desde la dirección inicial y desreferencia).
*   **Liberación de Arreglos Dinámicos:** Se usa `delete[]`. **¡Es crucial usar `delete[]` (con corchetes) para arreglos dinámicos!**
    ```cpp
    delete[] ptr_bloque; // Libera TODO el bloque de 4 enteros
    ptr_bloque = nullptr;
    ```

## 5. Problemas Comunes con la Memoria Dinámica

*   **Punteros Colgantes (Dangling Pointers):** Punteros que apuntan a una dirección de memoria que ya no es válida (porque fue liberada con `delete` o nunca fue válida). Usarlos lleva a comportamiento indefinido (crashes, corrupción de datos).
    *   **Tipos/Causas:**
        1.  Punteros no inicializados (apuntan a "basura").
        2.  Punteros que apuntan a memoria ya liberada (`delete`d).
        3.  Múltiples punteros a la misma memoria, y uno la libera mientras otros aún la usan.
    *   **Prevención:**
        *   Inicializar siempre los punteros (a `nullptr` o a una dirección válida).
        *   Asignar `nullptr` después de `delete`.
        *   Verificar `if (ptr != nullptr)` antes de desreferenciar (`*ptr`).

*   **Pérdidas de Memoria (Memory Leaks):** Ocurren cuando se reserva memoria en el Heap (`new`/`new[]`) pero se pierde la única referencia (puntero) a esa memoria **sin haberla liberado** con `delete`/`delete[]`. Esa memoria queda ocupada pero inaccesible por el resto de la ejecución del programa.
    *   **Ejemplo 1:**
        ```cpp
        int* p_nro_1 = new int[3]; // Reserva memoria en Heap
        int nro = 99;             // Variable en Stack
        p_nro_1 = &nro;           // ¡ERROR! p_nro_1 ahora apunta a 'nro' (Stack). 
                                  // La dirección del bloque de 3 ints en el Heap se perdió. ¡Memory Leak!
        // Nunca se hizo delete[] al bloque original.
        ```
    *   **Ejemplo 2:**
        ```cpp
        int* p_nro_2 = new int[3]; // Reserva bloque 1 en Heap
        p_nro_2 = new int[4];     // ¡ERROR! Reserva bloque 2 en Heap y asigna su dirección a p_nro_2.
                                  // La dirección del bloque 1 (de 3 ints) se perdió. ¡Memory Leak!
        delete[] p_nro_2;         // Solo libera el bloque 2 (de 4 ints).
        ```
    *   **Nota:** Lenguajes como Java tienen "Garbage Collector" que maneja esto automáticamente, pero C++ requiere gestión manual.

## 6. Arreglos y Punteros

*   **Relación Estrecha:** En C++, el nombre de un arreglo declarado estáticamente (ej. `int arr[4];`) actúa como un **puntero constante** a su primer elemento (`&arr[0]`).
    ```cpp
    int arr[4] = {4, 11, 19, 91}; // Arreglo en el Stack
    int* ptr = arr; // Válido. ptr ahora apunta a arr[0]
    // arr = ...; // ¡Inválido! No puedes cambiar dónde empieza 'arr'.
    ```
*   **Paso a Funciones:** Cuando pasas un arreglo `arr` a una función, en realidad estás pasando una copia del puntero (la dirección del primer elemento). Por eso, las modificaciones dentro de la función afectan al arreglo original. Usa `const` en el parámetro si no quieres permitir modificaciones.
*   **Diferencia Clave:**
    *   `int arr[4];` -> 4 `int`s en el **Stack**. `arr` es como un puntero constante al inicio.
    *   `int* ptr_block = new int[4];` -> 4 `int`s en el **Heap**. `ptr_block` es una variable puntero (en el Stack) que almacena la dirección del bloque en el Heap.

## 7. Secuencias con Punteros (Listas Enlazadas - Introducción)

*   **Concepto:** Estructura de datos donde los elementos (Nodos) no están necesariamente contiguos en memoria. Cada nodo contiene el dato y un puntero al siguiente nodo.
*   **Nodo (`struct Nodo`):**
    ```cpp
    struct Nodo {
        int elemento;      // El dato almacenado
        Nodo* siguiente; // Puntero al próximo nodo (o nullptr si es el último)
    };
    ```
*   **Operaciones Básicas (Ejemplos):**
    *   `crear_nodo`: Reserva memoria (`new Nodo`) para un nuevo nodo, le asigna el `elemento` y el puntero `siguiente`.
    *   `agregar_elemento`: Crea un nuevo nodo y lo enlaza a la lista (ej. al principio).
    *   `mostrar_elementos`: Recorre la lista desde el primer nodo siguiendo los punteros `siguiente` hasta llegar a `nullptr`.
    *   `eliminar_elemento`: Busca un nodo con un `elemento` específico, ajusta los punteros para "saltárselo" y libera su memoria (`delete`). Requiere manejar el caso de borrar el primer nodo (pasando `primero` por referencia `&`).
*   **Visualización:** Los diagramas del final ilustran cómo los punteros en el Stack (`primero`) apuntan a Nodos en el Heap, y cómo los punteros `siguiente` dentro de cada Nodo enlazan la secuencia.




- `const int`: El valor del `int` es constante.
- `const Contacto* ptr`: El `Contacto` apuntado por `ptr` no se puede modificar _usando `ptr`_. El puntero `ptr` sí puede cambiar. (Este es el caso del ejercicio).
- `Contacto* const ptr`: El puntero `ptr` no puede cambiar (siempre apunta a la misma dirección). El `Contacto` apuntado sí podría modificarse (si no fuera `const Contacto`).