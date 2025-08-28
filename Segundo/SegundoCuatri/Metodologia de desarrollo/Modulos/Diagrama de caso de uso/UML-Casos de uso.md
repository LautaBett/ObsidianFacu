### 🔹 UML en general

- **UML (Unified Modeling Language)** → es un lenguaje estándar para **visualizar, especificar, construir y documentar** sistemas de software.
    
- Combina ideas de distintos enfoques:
    
    - **Data modeling** (diagramas entidad-relación).
        
    - **Business modeling** (workflow).
        
    - **Object modeling**.
        
    - **Component modeling**.
        

Se usa durante **todo el ciclo de vida del software**.

### 🔹 Tipos de diagramas UML

1. **Estructurales**: clase, objeto, componente, despliegue.
    
2. **De comportamiento**: casos de uso, secuencia, colaboración, statecharts, actividad.
    

### 🔹 Casos de Uso

- **Definición**: describen **qué hace el sistema** (funcionalidad) desde el punto de vista de un actor externo, sin detallar cómo lo hace.
    
- **Elementos principales**:
    
    - **Use case**: la funcionalidad.
        
    - **Actor**: persona, sistema u objeto externo que interactúa.
        
    - **Activación**: la interacción entre actor y sistema.
        
    - **Relaciones**: include, extend, generalización.
        

### 🔹 Actores

- Representan **roles** en la interacción.
    
- Pueden ser humanos, dispositivos o incluso otro sistema.
    
- Se clasifican en:
    
    - **Primario**: inicia el caso de uso.
        
    - **Secundario**: colabora o recibe resultados.
        
- Existe un actor especial: **el reloj**, que dispara acciones por tiempo.
    

### 🔹 Ejemplo “El Renacuajo”

El caso práctico describe un sistema para administrar un club con pileta cubierta:

- Registrar socios.
    
- Abrir cursos de natación (profesor, horarios, andariveles).
    
- Inscribir socios a cursos.
    
- Controlar modalidad (curso o pileta libre).
    

### 🔹 Estructura de un Caso de Uso

- **Nombre**.
    
- **Descripción breve**.
    
- **Actor primario/secundario**.
    
- **Trigger** (evento que lo dispara).
    
- **Curso básico** (flujo normal).
    
- **Cursos alternativos** (excepciones).
    
- **Precondiciones y postcondiciones**.
    
- **Suposiciones** (cosas que se asumen ya validadas).
    
- **Casos extendidos o incluidos**.