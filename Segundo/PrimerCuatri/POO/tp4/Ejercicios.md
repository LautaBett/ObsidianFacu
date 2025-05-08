¡Entendido! Empecemos por el principio, implementando la solución para el **Centro de Cómputos** en Java.

```markdown
### 1. Centro de Cómputos

Aquí está la implementación en Java Orientada a Objetos para el Centro de Cómputos.

**Clase `Proceso`**

Representa un proceso con su requerimiento de memoria.
```java
import java.util.Objects;

public class Proceso {
    private String id; // Identificador opcional
    private double requerimientoMemoria;

    public Proceso(String id, double requerimientoMemoria) {
        this.id = id;
        this.requerimientoMemoria = requerimientoMemoria;
    }

    public double getRequerimientoMemoria() {
        return requerimientoMemoria;
    }

    public String getId() {
        return id;
    }

    @Override
    public String toString() {
        return "Proceso{" +
               "id='" + id + '\'' +
               ", memoria=" + requerimientoMemoria +
               '}';
    }

    // Es buena práctica implementar equals y hashCode si se usan en colecciones
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Proceso proceso = (Proceso) o;
        return Double.compare(proceso.requerimientoMemoria, requerimientoMemoria) == 0 &&
               Objects.equals(id, proceso.id);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, requerimientoMemoria);
    }
}
```

**Clase `Computadora`**

Representa una computadora con su velocidad y el proceso que ejecuta (si alguno).
```java
import java.util.Objects;

public class Computadora {
    private String id; // Identificador opcional
    private double velocidad; // Un valor numérico, mayor es más rápido
    private Proceso procesoAsignado;

    public Computadora(String id, double velocidad) {
        this.id = id;
        this.velocidad = velocidad;
        this.procesoAsignado = null; // Empieza libre
    }

    public double getVelocidad() {
        return velocidad;
    }

    public String getId() {
        return id;
    }

    public boolean estaLibre() {
        return procesoAsignado == null;
    }

    public void asignarProceso(Proceso p) {
        if (estaLibre()) {
            this.procesoAsignado = p;
        } else {
            // Manejar el error o lanzar una excepción si se intenta asignar a una PC ocupada
            System.err.println("Error: Computadora " + id + " ya está ocupada.");
        }
    }

    public Proceso finalizarProceso() {
        Proceso procesoTerminado = this.procesoAsignado;
        this.procesoAsignado = null; // La computadora queda libre
        return procesoTerminado; // Devuelve el proceso que terminó, por si se necesita
    }

    public Proceso getProcesoAsignado() {
        return procesoAsignado;
    }

    @Override
    public String toString() {
        return "Computadora{" +
               "id='" + id + '\'' +
               ", velocidad=" + velocidad +
               ", libre=" + estaLibre() +
               '}';
    }

    // Es buena práctica implementar equals y hashCode
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Computadora that = (Computadora) o;
        return Double.compare(that.velocidad, velocidad) == 0 &&
               Objects.equals(id, that.id);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, velocidad);
    }
}
```

**Clase `CentroComputos`**

Gestiona las colas y la asignación. Utiliza `PriorityQueue` para mantener el orden especificado.
```java
import java.util.Comparator;
import java.util.PriorityQueue;

public class CentroComputos {

    // Cola de procesos esperando: ordenados por memoria (mayor primero)
    private PriorityQueue<Proceso> colaProcesosEspera;

    // Cola de computadoras libres: ordenadas por velocidad (más rápida primero)
    private PriorityQueue<Computadora> colaComputadorasLibres;

    public CentroComputos() {
        // Comparator para procesos: compara por memoria descendente
        Comparator<Proceso> comparadorProcesos = Comparator
                .comparingDouble(Proceso::getRequerimientoMemoria)
                .reversed(); // reversed() para que el de mayor memoria tenga mayor prioridad

        // Comparator para computadoras: compara por velocidad descendente
        Comparator<Computadora> comparadorComputadoras = Comparator
                .comparingDouble(Computadora::getVelocidad)
                .reversed(); // reversed() para que la más rápida tenga mayor prioridad

        this.colaProcesosEspera = new PriorityQueue<>(comparadorProcesos);
        this.colaComputadorasLibres = new PriorityQueue<>(comparadorComputadoras);
    }

    /**
     * Añade una nueva computadora al pool de computadoras libres.
     * Solo se añade si está realmente libre.
     * @param computadora La computadora a añadir.
     */
    public void agregarComputadora(Computadora computadora) {
        if (computadora.estaLibre()) {
            colaComputadorasLibres.offer(computadora);
            System.out.println("Computadora agregada: " + computadora.getId());
            intentarAsignarProceso(); // Intentar asignar si hay procesos esperando
        } else {
             System.out.println("No se puede agregar la computadora " + computadora.getId() + " porque está ocupada.");
        }
    }

    /**
     * Añade un nuevo proceso a la cola de espera.
     * @param proceso El proceso a añadir.
     */
    public void agregarProceso(Proceso proceso) {
        colaProcesosEspera.offer(proceso);
        System.out.println("Proceso agregado a la cola: " + proceso.getId() + " (Mem: " + proceso.getRequerimientoMemoria() + ")");
        intentarAsignarProceso(); // Intentar asignar si hay computadoras libres
    }

    /**
     * Intenta asignar el proceso de mayor prioridad (más memoria)
     * a la computadora libre de mayor prioridad (más rápida).
     */
    public void intentarAsignarProceso() {
        if (!colaProcesosEspera.isEmpty() && !colaComputadorasLibres.isEmpty()) {
            // Obtener el proceso con más memoria (sin quitarlo aún, por si falla algo)
            Proceso procesoAAsignar = colaProcesosEspera.peek();
            // Obtener la computadora más rápida (sin quitarla aún)
            Computadora computadoraDisponible = colaComputadorasLibres.peek();

            // Si ambos existen, proceder a la asignación
            if (procesoAAsignar != null && computadoraDisponible != null) {
                // Ahora sí, los quitamos de las colas
                colaProcesosEspera.poll();
                colaComputadorasLibres.poll();

                // Asignar el proceso a la computadora
                computadoraDisponible.asignarProceso(procesoAAsignar);
                System.out.println("--> Proceso " + procesoAAsignar.getId() + " asignado a Computadora " + computadoraDisponible.getId());

                // La computadora ya no está libre, NO se vuelve a añadir a colaComputadorasLibres
            }
        } else {
             if (colaProcesosEspera.isEmpty()) {
                 System.out.println("No hay procesos en espera.");
             }
             if (colaComputadorasLibres.isEmpty()) {
                 System.out.println("No hay computadoras libres.");
             }
        }
    }

    /**
     * Se invoca cuando una computadora ha terminado de ejecutar su proceso.
     * La computadora vuelve a estar disponible.
     * @param computadoraQueTermino La computadora que finalizó su tarea.
     */
    public void finalizarEjecucion(Computadora computadoraQueTermino) {
        Proceso procesoTerminado = computadoraQueTermino.finalizarProceso();
        if (procesoTerminado != null) {
            System.out.println("<- Proceso " + procesoTerminado.getId() + " finalizado en Computadora " + computadoraQueTermino.getId());
            // La computadora ahora está libre, la volvemos a añadir a la cola de libres
            agregarComputadora(computadoraQueTermino);
        } else {
             System.out.println("Advertencia: Se intentó finalizar en una computadora ("+ computadoraQueTermino.getId() +") que ya estaba libre.");
             // Podríamos verificar si ya está en la cola de libres para evitar duplicados
             if (!colaComputadorasLibres.contains(computadoraQueTermino)) {
                 agregarComputadora(computadoraQueTermino);
             }
        }
    }

    // Método para ver el estado (opcional)
    public void mostrarEstado() {
        System.out.println("\n--- Estado del Centro ---");
        System.out.println("Procesos en espera (" + colaProcesosEspera.size() + "):");
        // PriorityQueue no garantiza orden en la iteración, solo en poll/peek
        // Para ver el orden, tendríamos que sacar y volver a meter, o copiar a otra estructura
        colaProcesosEspera.forEach(p -> System.out.println("  - " + p));

        System.out.println("Computadoras libres (" + colaComputadorasLibres.size() + "):");
        colaComputadorasLibres.forEach(c -> System.out.println("  - " + c));
        System.out.println("-------------------------\n");
    }

    // --- Main para probar ---
    public static void main(String[] args) {
        CentroComputos centro = new CentroComputos();

        // Crear computadoras
        Computadora c1 = new Computadora("C01", 100.0); // Rápida
        Computadora c2 = new Computadora("C02", 50.0);  // Lenta
        Computadora c3 = new Computadora("C03", 120.0); // Más rápida

        // Crear procesos
        Proceso p1 = new Proceso("P1", 256); // Menos memoria
        Proceso p2 = new Proceso("P2", 1024); // Más memoria
        Proceso p3 = new Proceso("P3", 512);  // Memoria intermedia
        Proceso p4 = new Proceso("P4", 1024); // Misma memoria que P2

        // Agregar elementos al centro
        centro.agregarComputadora(c1);
        centro.agregarComputadora(c2);
        centro.mostrarEstado();

        centro.agregarProceso(p1); // Se asigna a C1 (la más rápida libre)
        centro.mostrarEstado();

        centro.agregarProceso(p2); // Se asigna a C2 (la única libre)
        centro.mostrarEstado();

        centro.agregarProceso(p3); // Queda en espera
        centro.agregarProceso(p4); // Queda en espera (detrás de p3 si llegó después, o junto si la memoria es el único criterio)
                                   // La PriorityQueue puede desempatar de forma no especificada si la prioridad es igual
        centro.mostrarEstado();

        // Llega una computadora más rápida
        centro.agregarComputadora(c3); // Se asigna P2 (el de más memoria en espera) a C3
        centro.mostrarEstado();

        // Una computadora termina
        centro.finalizarEjecucion(c1); // C1 queda libre, se asigna P3 (siguiente en memoria)
        centro.mostrarEstado();

        // Termina otra
        centro.finalizarEjecucion(c2); // C2 queda libre, no hay procesos, queda libre
        centro.mostrarEstado();

         // Termina otra
        centro.finalizarEjecucion(c3); // C3 queda libre, no hay procesos, queda libre
        centro.mostrarEstado();

         // Termina la última que estaba ocupada
        centro.finalizarEjecucion(c1); // C1 queda libre, no hay procesos, queda libre
        centro.mostrarEstado();
    }
}
```

**Resumen del Diseño:**

1.  **Objetos:** `Proceso`, `Computadora`, `CentroComputos`.
2.  **Estado:**
    *   `Proceso`: `id`, `requerimientoMemoria`.
    *   `Computadora`: `id`, `velocidad`, `procesoAsignado`.
    *   `CentroComputos`: `colaProcesosEspera` (PriorityQueue de Proceso), `colaComputadorasLibres` (PriorityQueue de Computadora).
3.  **Comportamiento:**
    *   `Proceso`: Getters.
    *   `Computadora`: Getters, `estaLibre()`, `asignarProceso()`, `finalizarProceso()`.
    *   `CentroComputos`: `agregarComputadora()`, `agregarProceso()`, `intentarAsignarProceso()`, `finalizarEjecucion()`.
4.  **Relaciones:**
    *   `CentroComputos` **tiene** dos `PriorityQueue` (una de `Proceso`, una de `Computadora`).
    *   `Computadora` **puede tener asignado un** `Proceso`.
    *   Se usan `Comparator` para definir el orden específico de las colas de prioridad.

Este código implementa la lógica descrita para el Centro de Cómputos. ¿Continuamos con el Puerto de Cereales?