
### 🔹 Relaciones en Diagramas de Casos de Uso UML

Los diagramas de casos de uso son herramientas clave para modelar la interacción entre un sistema y sus usuarios (actores). Las relaciones entre casos de uso permiten expresar dependencias y comportamientos compartidos de manera clara.

1.  **Generalización (Herencia)**
    *   Similar a la herencia de clases en programación orientada a objetos.
    *   Un caso de uso "padre" define un comportamiento general, y los casos de uso "hijos" especializan ese comportamiento.
    *   **Ejemplo:** "Realizar pago" (padre) puede generalizarse en "Pagar con tarjeta de crédito", "Pagar con PayPal" o "Pagar con transferencia bancaria" (hijos). Cada hijo implementa una forma específica de pago, pero todos comparten la idea general de realizar un pago.

2.  **Include (<<include>>)**
    *   Se utiliza cuando dos o más casos de uso comparten un comportamiento en común.
    *   El comportamiento compartido se extrae y se factoriza en un nuevo caso de uso "incluido".
    *   El caso de uso incluido no se activa directamente por un actor; siempre se ejecuta como parte de otro caso de uso.
    *   La relación es explícita, lo que significa que la dependencia es clara y directa.
    *   **Ejemplo:**
        *   "Reservar vuelo" incluye "Verificar disponibilidad".
        *   "Comprar seguro de viaje" también incluye "Verificar disponibilidad".
        *   En este caso, "Verificar disponibilidad" es un caso de uso reutilizable que asegura que los recursos estén disponibles antes de continuar con la reserva o la compra.

3.  **Extend (<<extend>>)**
    *   El caso de uso base puede ser extendido con un comportamiento adicional, pero solo bajo ciertas condiciones específicas.
    *   El caso de uso extendido sí es un caso de uso normal y puede ser activado directamente por un actor.
    *   La relación es implícita, lo que significa que la dependencia no es directa y depende de ciertas condiciones.
    *   **Ejemplo:**
        *   "Gestionar pedido" puede extenderse con "Aplicar descuento" si el cliente tiene un cupón válido.
        *   Aquí, "Aplicar descuento" no siempre ocurre, sino que depende de si se cumplen ciertas condiciones (tener un cupón).

### 🔹 Ejemplos en un Sistema de Gestión de Biblioteca

*   **Prestar libro**: Incluye la verificación de la disponibilidad del libro y la validez de la membresía del usuario.
*   **Devolver libro**: Puede extenderse con "Cobrar multa por retraso" si el libro se devuelve fuera de la fecha límite.
*   **Registrar nuevo socio**: Flujo básico que incluye datos personales y documento. Puede incluir "Enviar email de bienvenida" para mejorar la experiencia del usuario.

### 🔹 Suposiciones (Assumptions)

*   Son estados que deben cumplirse antes de ejecutar un caso de uso, pero no son precondiciones directas del caso de uso.
*   **Ejemplo:** En un sistema de comercio electrónico, se asume que el usuario tiene una conexión a Internet activa antes de "Realizar compra", aunque la conexión no sea parte del flujo del caso de uso actual.

*   **Diferencias clave:**
    *   **Precondición**: Debe ser verdadera antes de ejecutar el caso de uso (ej., el usuario debe estar logueado).
    *   **Postcondición**: Debe cumplirse al finalizar la ejecución del caso de uso (ej., el pedido se registra en la base de datos).
    *   **Suposición**: Se asume que es cierta sin necesidad de verificarla dentro del caso de uso (ej., el sistema de pago funciona correctamente).

