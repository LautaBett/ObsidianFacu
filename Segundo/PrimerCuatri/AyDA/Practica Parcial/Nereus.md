El lenguaje Nereus es un lenguaje específico de dominio (DSL) declarativo diseñado para describir la disposición de datos (data layout). Su propósito principal es generar automáticamente código C++ que maneje la serialización y deserialización de estos datos, asegurando eficiencia y seguridad de tipos en tiempo de compilación.

Aquí te explico cómo funciona, sus características, su relación con C++ y un ejemplo, basándome en la información de la nota [[Nereus]].

### ¿Qué es Nereus?

Nereus es un lenguaje que te permite definir cómo se estructuran tus datos para ser almacenados o transmitidos. En lugar de escribir manualmente código C++ para leer y escribir cada campo de una estructura de datos, describes la estructura en Nereus, y él genera el código C++ necesario.

### Características Clave de Nereus

*   **Declarativo:** Te enfocas en *qué* datos tienes y cómo están organizados, no en *cómo* leerlos o escribirlos.
*   **Legible por Humanos:** La sintaxis está diseñada para ser clara y fácil de entender.
*   **Seguridad de Tipos en Tiempo de Compilación:** Los errores en la definición del layout se detectan durante la compilación, no en tiempo de ejecución.
*   **Eficiencia:** Genera código C++ optimizado para el acceso a datos.
*   **Extensibilidad:** Permite definir tipos personalizados y validaciones.
*   **Generación de Código:** Produce encabezados C++ (`.hpp`) con las estructuras y funciones necesarias.

### ¿Cómo Funciona Nereus?

1.  **Definición:** Escribes una descripción de tu formato de datos en un archivo Nereus (generalmente con extensión `.ner`).
2.  **Compilación:** Un compilador de Nereus procesa este archivo `.ner`.
3.  **Generación de Código:** El compilador genera un archivo de cabecera C++ (`.hpp`). Este archivo contiene:
    *   Estructuras C++ que representan los datos descritos.
    *   Funciones para leer (deserializar) y escribir (serializar) estas estructuras desde/hacia un buffer de memoria.
    *   Métodos para acceder a los campos individuales de manera segura.

### Relación con C++

Nereus está íntimamente ligado a C++.
*   **Genera Código C++:** La salida principal del compilador de Nereus son archivos de cabecera C++.
*   **Integración Directa:** Incluyes el archivo `.hpp` generado en tu proyecto C++ y utilizas las clases y funciones proporcionadas como si las hubieras escrito tú mismo.
*   **API para C++:** Proporciona una API en C++ para interactuar con los datos definidos, como acceder a campos, obtener tamaños, y realizar la serialización/deserialización.
*   **Sin Dependencias en Tiempo de Ejecución (generalmente):** El código generado suele ser C++ estándar y no requiere bibliotecas adicionales de Nereus en tiempo de ejecución, aunque esto puede depender de las características específicas utilizadas.

### Ejemplo de Nereus

Aquí tienes un ejemplo sencillo de cómo se podría ver una definición en Nereus y cómo se usaría en C++ (basado en los conceptos descritos en la nota [[Nereus]]):

**Archivo `mi_paquete.ner` (Ejemplo hipotético):**

```nereus
// mi_paquete.ner
namespace mi_protocolo;

struct MiPaquete {
  u32 version;        // Un entero sin signo de 32 bits para la versión
  u16 tipo_mensaje;   // Un entero sin signo de 16 bits para el tipo de mensaje
  string<64> nombre;  // Una cadena de hasta 64 caracteres
  // ... otros campos
}
```

**Proceso:**

1.  Compilas `mi_paquete.ner` con el compilador de Nereus: `nereus_compiler mi_paquete.ner`
2.  Esto generaría un archivo `mi_paquete.hpp`.

**Uso en C++ (`main.cpp`):**

```cpp
#include "mi_paquete.hpp" // Archivo generado por Nereus
#include <vector>
#include <iostream>
#include <string>

int main() {
  // Crear un buffer de datos (podría venir de una red, archivo, etc.)
  std::vector<std::byte> buffer(1024); // Asumimos un buffer suficientemente grande

  // Escribir datos usando Nereus (Serialización)
  mi_protocolo::MiPaquete::Writer paquete_writer(buffer.data(), buffer.size());
  if (paquete_writer.is_valid()) {
    paquete_writer.set_version(1);
    paquete_writer.set_tipo_mensaje(101);
    paquete_writer.set_nombre("HolaNereus");
    // ... establecer otros campos

    size_t bytes_escritos = paquete_writer.size_bytes();
    std::cout << "Bytes escritos: " << bytes_escritos << std::endl;

    // Aquí podrías enviar 'buffer' a través de la red o guardarlo en un archivo
    // (solo los 'bytes_escritos' son relevantes)
  } else {
    std::cerr << "Error al inicializar el writer de MiPaquete." << std::endl;
    return 1;
  }

  // Leer datos usando Nereus (Deserialización)
  // Asumimos que 'buffer' ahora contiene los datos serializados
  mi_protocolo::MiPaquete::Reader paquete_reader(buffer.data(), buffer.size());
  if (paquete_reader.is_valid()) {
    std::cout << "Versión: " << paquete_reader.get_version() << std::endl;
    std::cout << "Tipo de Mensaje: " << paquete_reader.get_tipo_mensaje() << std::endl;
    std::cout << "Nombre: " << paquete_reader.get_nombre().value_or("N/A") << std::endl;
    // ... leer otros campos
  } else {
    std::cerr << "Error al leer MiPaquete o buffer inválido." << std::endl;
    return 1;
  }

  return 0;
}

```

**Explicación del Ejemplo C++:**

*   Se incluye `mi_paquete.hpp`, que contiene la definición de `mi_protocolo::MiPaquete` y sus clases `Writer` y `Reader` (o nombres similares, dependiendo de la implementación exacta de Nereus).
*   Para **escribir (serializar)**, se crea un objeto `Writer` (por ejemplo, `MiPaquete::Writer`) que toma un puntero a un buffer de memoria y su tamaño. Luego, se usan métodos `set_XXX` para establecer los valores de los campos.
*   Para **leer (deserializar)**, se crea un objeto `Reader` (por ejemplo, `MiPaquete::Reader`) que también toma un puntero al buffer con los datos y su tamaño. Luego, se usan métodos `get_XXX` para acceder a los valores de los campos.
*   Nereus se encarga de la correcta disposición de los bytes, el empaquetado, el alineamiento y la conversión entre los tipos de Nereus y los tipos de C++.

En resumen, Nereus simplifica el manejo de layouts de datos binarios en C++ al automatizar la generación de código de serialización/deserialización, lo que reduce errores, mejora la mantenibilidad y permite enfocarse en la lógica de la aplicación en lugar de en los detalles de bajo nivel del formato de datos.