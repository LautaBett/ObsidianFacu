Okay, aquí tienes un resumen de la información proporcionada sobre C++, formateado en Markdown para Obsidian y con explicaciones adicionales para facilitar la comprensión.

```markdown
# Resumen: Introducción a C++ (Basado en Material AyDA I - UNICEN)

Este resumen cubre los conceptos introductorios de C++ presentados, enfocándose en cadenas, debugging, argumentos de programa, arreglos, funciones y punteros básicos.

## 1. Configuración y Recursos

*   **Entorno de Desarrollo (IDE):** Se recomienda [Code::Blocks](https://www.codeblocks.org/).
    *   *Explicación:* Un IDE (Entorno de Desarrollo Integrado) es un software que te ayuda a escribir, compilar (traducir tu código a lenguaje máquina) y depurar (encontrar errores) tus programas. Code::Blocks es una opción popular y gratuita.
*   **Bibliografía:**
    *   SAVITCH, W. A. *Resolución de problemas con C++*.
    *   CORMEN, Thomas H., et al. *Introduction to algorithms*. (Un clásico de algoritmos, útil en general).
*   **Documentación Oficial:**
    *   [cppreference.com](https://en.cppreference.com/w/) (Muy técnico y detallado)
    *   [cplusplus.com](https://cplusplus.com/) (Más amigable para principiantes)

## 2. Cadenas (Strings)

*   **Estilo C:** Son arreglos de caracteres (`char`) que **deben** terminar con un carácter especial nulo (`\0`). Su tamaño es fijo una vez declarado.
    ```cpp
    char nombre_c[20]; // Arreglo para hasta 19 caracteres + '\0'
    ```
*   **Estilo C++ (`std::string`):** Son objetos más flexibles y fáciles de usar.
    *   **Ventajas:**
        *   **Tamaño dinámico:** Se ajustan automáticamente al contenido.
        *   **Operadores:** Soportan comparación (`==`, `<`, `>`), concatenación (`+`, `+=`), etc. de forma intuitiva.
    ```cpp
    #include <string> // Necesario incluir la librería
    using namespace std; // Para no escribir std::string
    
    string nombre_cpp; // Declara una cadena C++
    ```
*   **Entrada de Cadenas:**
    *   `cin >> nombre;`: Lee la entrada **hasta el primer espacio en blanco** (espacio, tabulador, enter). Si ingresas "Juan Perez", solo guardará "Juan".
    *   `getline(cin, nombre);`: Lee la entrada **hasta encontrar un salto de línea (Enter)**. Guarda la línea completa, incluyendo espacios. Es generalmente preferible para leer nombres o frases.

    ```cpp
    #include <iostream>
    #include <string>
    using namespace std;

    int main() {
        string nombre;
        cout << "Ingrese su nombre completo: ";
        // cin >> nombre; // Solo leería la primera palabra
        getline(cin, nombre); // Lee toda la línea
        cout << "Hola " << nombre << "!\n";
        return 0;
    }
    ```

## 3. Debugging (Depuración)

*   **Concepto:** Es el proceso de encontrar y corregir errores ("bugs") en un programa.
*   **Origen del Término:** La anécdota de la polilla ("bug") en el Mark II en 1947.
*   **Métodos:**
    *   **Prueba de escritorio:** Seguir la ejecución del código en papel, paso a paso, anotando el valor de las variables.
    *   **Impresiones por consola:** Usar `cout` para mostrar el valor de las variables en puntos clave del programa y ver cómo cambian.
    *   **Herramientas de Debugging (Debugger):** Los IDEs (como Code::Blocks) incluyen herramientas potentes:
        *   **Breakpoints (Puntos de interrupción):** Marcas en el código donde la ejecución se detendrá temporalmente.
        *   **Step Over/Into/Out:** Ejecutar el código línea por línea o saltar/entrar/salir de funciones.
        *   **Watches (Inspección):** Ventanas donde puedes ver el valor actual de las variables mientras el programa está pausado.
*   **Importancia de las Pruebas:** Que un programa funcione para *algunos* casos no significa que sea correcto para *todos*.
*   **Selección de Valores de Prueba:**
    *   **Aleatorias:** Detectan errores inesperados.
    *   **Límite:** Valores extremos (el más pequeño, el más grande, cero, negativos si aplica). Muy útiles para encontrar errores comunes.
    *   **Basadas en especificaciones:** Usar los requisitos del programa para diseñar pruebas.
    *   **Basadas en escenarios:** Simular situaciones de uso real.
    *   **Basadas en datos históricos:** Usar datos reales de ejecuciones pasadas.

*   **Ejemplo (Factorial):** Se usa como caso para aplicar debugging. El código calcula el factorial de un número `n` (n! = 1 * 2 * ... * n). Usa `abs(nro)` para manejar negativos (calcula el factorial del valor absoluto) y `unsigned long` para poder almacenar resultados grandes.

    ```cpp
    #include <iostream>
    #include <cmath> // Para abs()
    using namespace std;

    int main() {
        int nro;
        cout << "Ingrese un numero para calcular su factorial: ";
        cin >> nro;
        nro = abs(nro); // Tomamos el valor absoluto
        unsigned long long resultado = 1; // Usar unsigned long long para resultados más grandes
        // El factorial de 0 es 1, el bucle no se ejecuta si nro es 0 o 1.
        for (unsigned int i = 2; i <= nro; i++) {
            resultado *= i; 
        }
        cout << "El factorial de " << nro << " es: " << resultado << endl;
        return 0;
    }
    ```
    *Nota: Se cambió `unsigned long` a `unsigned long long` para mayor capacidad.*

## 4. Argumentos de Programa (Línea de Comandos)

*   La función `main` puede recibir parámetros que representan los argumentos pasados al programa al ejecutarlo desde la terminal.
*   **Firma:** `int main(int argc, char *argv[])`
    *   `argc` (Argument Count): Un entero que indica **cuántos** argumentos se pasaron (incluyendo el nombre del programa).
    *   `argv` (Argument Vector): Un **arreglo de cadenas estilo C** (`char*`). Cada elemento `argv[i]` es uno de los argumentos.
        *   `argv[0]` es **siempre** el nombre con el que se ejecutó el programa.
        *   `argv[1]` es el primer argumento real, `argv[2]` el segundo, y así sucesivamente hasta `argv[argc - 1]`.

*   **Ejemplo:**

    ```cpp
    #include <iostream>
    #include <string> // Para convertir argv a std::string si es necesario
    using namespace std;

    int main(int argc, char *argv[]) {
        cout << "Cantidad de argumentos: " << argc << "\n";
        cout << "Argumentos: ";
        for (int i = 0; i < argc; i++) {
            cout << argv[i] << " "; 
        }
        cout << endl;

        // Ejemplo de uso: verificar si se pasó un argumento específico
        if (argc == 2) { // Si hay 2 argumentos (nombre_programa + 1 argumento)
            string param1(argv[1]); // Convertir C-string a C++ string
            if (param1 == "ayuda") {
                cout << "Mostrando ayuda del programa..." << endl;
            } else {
                cout << "Argumento desconocido: " << param1 << endl;
            }
        }
        return 0;
    }
    ```
    *   Si compilas este código como `mi_programa.exe` y lo ejecutas en la terminal como: `mi_programa.exe hola mundo`
    *   `argc` será `3`.
    *   `argv[0]` será `"mi_programa.exe"`.
    *   `argv[1]` será `"hola"`.
    *   `argv[2]` será `"mundo"`.

## 5. Arreglos (Arrays)

*   **Concepto:** Colecciones de elementos del **mismo tipo** almacenados en memoria de forma **contigua** (uno después del otro).
*   **Acceso:** Se accede a los elementos mediante un **índice** numérico, que **empieza en 0**. `arreglo[0]` es el primer elemento, `arreglo[1]` el segundo, etc.
*   **Declaración:**
    *   **Tamaño fijo (estático):** Se define al compilar.
        ```cpp
        const int TAMANO = 5;
        char arreglo_chars[TAMANO]; // Arreglo de 5 chars
        int numeros[10]; // Arreglo de 10 ints
        ```
    *   **Inicialización directa:**
        ```cpp
        char letras[] = {'A', 'y', 'D', 'A', '1'}; // El tamaño se deduce (5)
        int valores[] = {10, 20, 30}; // Tamaño 3
        ```
    *   **Tamaño definido por el usuario (VLA - Variable Length Array):** *Nota: Esto es una característica de C99, soportada como extensión en algunos compiladores C++, pero **no es estándar C++**. La forma estándar C++ para tamaños dinámicos es `std::vector` o memoria dinámica (`new`).*
        ```cpp
        // Ejemplo mostrado en el material (puede no compilar en todos los C++ estándar)
        int tamanio;
        cout << "Ingrese el tamaño del arreglo:\n";
        cin >> tamanio;
        char arreglo_usuario[tamanio]; // VLA
        ```
*   **Cuidado con los Tipos:** Asignar un `char` a un `int` guardará su valor ASCII.
    ```cpp
    int arreglo_ascii[] = {'A', 'B', 'C'}; // Guarda 65, 66, 67
    ```

## 6. Funciones

*   **Concepto:** Bloques de código reutilizables que realizan una tarea específica. Ayudan a organizar el código.
*   **Declaración (Prototipo):** Informa al compilador sobre la existencia de la función antes de su uso.
    `<tipo_retorno> <nombre_función>(<lista_de_parámetros>);`
*   **Definición:** Contiene el código que ejecuta la función.
    ```cpp
    <tipo_retorno> <nombre_función>(<lista_de_parámetros>) {
        // Cuerpo de la función (sentencias)
        return <valor>; // Si tipo_retorno no es void
    }
    ```
*   **`tipo_retorno`:** El tipo de dato que la función devuelve (`int`, `float`, `string`, `void` si no devuelve nada, etc.).
*   **`lista_de_parámetros`:** Variables que la función recibe para trabajar. Pueden ser cero o más.

*   **Pasaje de Parámetros:** Cómo se entregan los valores a la función:
    *   **Por Valor (Copia):** La función recibe una **copia** de la variable original. Los cambios dentro de la función **NO afectan** a la variable original fuera de ella. Es el comportamiento por defecto.
        ```cpp
        void modificar_copia(int variable) { // Recibe una copia
            variable = 10; // Modifica la copia local
        }
        int main() {
            int numero = 2;
            modificar_copia(numero);
            // numero sigue valiendo 2 aquí
            cout << numero; // Imprime 2
            return 0;
        }
        ```
    *   **Por Referencia (`&`):** La función recibe una **referencia** (un alias) a la variable original. Los cambios dentro de la función **SÍ afectan** a la variable original. Exclusivo de C++.
        ```cpp
        void modificar_original(int& variable) { // Recibe una referencia
            variable = 10; // Modifica la variable original
        }
        int main() {
            int numero = 2;
            modificar_original(numero);
            // numero ahora vale 10 aquí
            cout << numero; // Imprime 10
            return 0;
        }
        ```

*   **Pasaje de Arreglos a Funciones:**
    *   Cuando pasas un arreglo a una función, **no se copia todo el arreglo**. Se pasa la dirección de memoria del primer elemento (similar a un puntero).
    *   Por lo tanto, las modificaciones al arreglo dentro de la función **SÍ afectan** al arreglo original.
    *   Para **evitar modificaciones accidentales**, puedes declarar el parámetro como `const`.
        ```cpp
        // Esta función PUEDE modificar el arreglo original
        void inicializarArreglo(char arreglo[], int tam) { ... } 
        
        // Esta función NO PUEDE modificar el arreglo (el compilador dará error si lo intenta)
        void mostrarArreglo(const char arreglo[], int tam) { ... } 
        ```
    *   Los parámetros de arreglo también se pueden declarar usando sintaxis de puntero:
        `void inicializarArreglo(char* arreglo, int tam)` es equivalente a `void inicializarArreglo(char arreglo[], int tam)`.

## 7. Punteros y Memoria Dinámica

*   **Puntero:** Una variable que almacena una **dirección de memoria** de otra variable.
    ```cpp
    int v = 10;
    int* p1; // Declara un puntero a un entero
    p1 = &v; // El operador '&' obtiene la dirección de 'v'. p1 ahora "apunta" a 'v'.
    ```
*   **Operador de Desreferenciación (`*`):** Cuando se usa delante de un puntero, accede al **valor** almacenado en la dirección a la que apunta.
    ```cpp
    cout << *p1; // Imprime el valor de v (10)
    *p1 = 20;   // Cambia el valor de v a 20 a través del puntero p1
    ```
*   **Memoria Dinámica:** Permite solicitar memoria durante la **ejecución** del programa, en lugar de definir todo al compilar. Útil cuando no sabes de antemano cuánta memoria necesitarás (ej. tamaño de arreglo definido por el usuario).
    *   **Operador `new`:** Reserva memoria en una zona llamada "heap". Devuelve un puntero a la memoria reservada.
    *   **Operador `delete` / `delete[]`:** Libera la memoria reservada con `new` para que pueda ser reutilizada. **Es crucial liberar la memoria que ya no necesitas para evitar "fugas de memoria" (memory leaks).**
        *   `delete ptr;` (para memoria reservada con `new tipo;`)
        *   `delete[] ptr_arreglo;` (para memoria reservada con `new tipo[tamaño];`)

    ```cpp
    int* ptr_dinamico = new int; // Reserva memoria para un int
    *ptr_dinamico = 50;
    cout << *ptr_dinamico; // Imprime 50
    delete ptr_dinamico; // Libera la memoria

    int tam;
    cout << "Tamaño del arreglo dinámico: ";
    cin >> tam;
    double* arreglo_dinamico = new double[tam]; // Reserva memoria para 'tam' doubles
    // ... usar el arreglo_dinamico ...
    arreglo_dinamico[0] = 3.14;
    // ...
    delete[] arreglo_dinamico; // Libera la memoria del arreglo
    ```

## 8. Ejemplo Integrador (Notas de Alumnos)

*   Combina varios conceptos:
    *   Pide al usuario el número de estudiantes.
    *   Usa arreglos (probablemente dinámicos o VLA según el código mostrado) para almacenar nombres (`string`) y calificaciones (`double`).
    *   Usa funciones separadas para:
        *   `cargarNombres` (lee los nombres, usa `getline`).
        *   `cargarNotas` (lee las notas).
        *   `calcularPromedio` (calcula y devuelve el promedio).
    *   Muestra el resultado.

## 9. Bonus Track (Carga desde Archivo `.csv`)

*   Muestra cómo leer los datos de los estudiantes desde un archivo de texto (`datos.csv`) en lugar de pedirlos por consola.
*   Usa `ifstream` para abrir y leer el archivo.
*   Maneja errores (si el archivo no se puede abrir, está vacío, etc.).
*   Lee la primera línea para obtener el número de estudiantes.
*   Lee las líneas siguientes, separando el nombre y la nota (que están separados por coma) usando `stringstream` y `getline`.
*   Convierte la nota (leída como texto) a `double` usando `atof` (o preferiblemente `stod` en C++ moderno).
*   Define `INF 99` como un tamaño máximo predefinido para los arreglos estáticos, lo cual es una **mala práctica** si se espera leer el tamaño real del archivo. Sería mejor usar memoria dinámica o `std::vector`.

```