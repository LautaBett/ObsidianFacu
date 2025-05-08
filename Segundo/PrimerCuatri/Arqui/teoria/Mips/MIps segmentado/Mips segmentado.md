## Segmentación del MIPS: Resumen y Explicación

A continuación, se presenta un resumen y explicación del PDF "M4_MIPS Segmentado", enfocado en la técnica de segmentación (pipelining) aplicada a la arquitectura MIPS.

### Introducción a la Segmentación (Pipelining)

La segmentación es una técnica utilizada para optimizar el tiempo de ejecución de procesos que se realizan mediante la repetición de una secuencia básica de pasos. Su objetivo principal es mejorar la productividad, es decir, la cantidad de procesos completados por unidad de tiempo.

**Principios Clave:**

- **División en Etapas:** El proceso se divide en etapas más pequeñas.
- **Ejecución en Paralelo:** Cada etapa se ejecuta en un recurso independiente, permitiendo que múltiples procesos estén en diferentes etapas de ejecución simultáneamente.
- **Flujo Continuo:** Cuando una etapa finaliza, el recurso que ocupaba se libera y puede comenzar a procesar la misma etapa del siguiente proceso.

**Analogías para Entender la Segmentación:**

- **Lavado de Ropa:** Se compara un funcionamiento secuencial (lavar, secar, planchar y guardar una tanda de ropa antes de comenzar con la siguiente) con un funcionamiento segmentado (mientras una tanda se está secando, otra puede estar lavándose, y una tercera planchándose). Esto reduce significativamente el tiempo total para completar múltiples tandas.
- **Línea de Ensamblaje (Henry Ford):** Popularizó la producción en cadena, donde cada operario realiza una parte del trabajo sobre diferentes unidades (automóviles en su caso) de forma simultánea. Las tareas se planean para que tarden aproximadamente lo mismo, y la velocidad de producción la limita la etapa más lenta.
- **Sistema Educativo:** Se asemeja a una "producción en serie" de egresados, donde cada año escolar es una etapa y diferentes promociones de alumnos avanzan por estas etapas en paralelo.

**Conceptos Importantes en Segmentación:**

- **Aceleración (Speedup):** Es la ganancia en velocidad obtenida al usar segmentación comparada con la ejecución secuencial. La aceleración aumenta con la cantidad de procesos a realizar. La aceleración máxima teórica es igual al número de etapas del pipeline, siempre que todas las etapas tarden lo mismo.
- **Latencia:** Es el tiempo que tarda un proceso individual en completarse desde que comienza hasta que finaliza. En un sistema segmentado, la latencia de un proceso individual puede ser igual o incluso ligeramente mayor que en un sistema no segmentado debido a la sobrecarga de los registros de segmentación. Sin embargo, el rendimiento global (throughput) mejora.
- **Throughput (Productividad):** Es la cantidad de procesos completados por unidad de tiempo. En un pipeline balanceado (etapas de igual duración), el throughput es idealmente uno por ciclo de la etapa más lenta, una vez que el pipeline está lleno.
- **Etapas de Diferente Duración:** Si las etapas no tardan lo mismo, la etapa más lenta determina la velocidad del pipeline (el "cuello de botella"). La aceleración máxima ya no será igual al número de etapas.

### El Microprocesador MIPS como un Pipeline de Instrucciones

La ejecución de una instrucción en un procesador como MIPS puede dividirse en varias etapas. Observar el procesador como una "tubería" de instrucciones permite aplicar los principios de segmentación. Cada instrucción pasa por una secuencia de etapas.

**Las 5 Etapas Clásicas del Pipeline MIPS:**

El datapath del MIPS se divide comúnmente en cinco etapas para la segmentación:

1. **IF (Instruction Fetch):** Búsqueda de la instrucción. Se obtiene la instrucción desde la memoria de programa utilizando la dirección apuntada por el Contador de Programa (PC).
2. **ID (Instruction Decode):** Decodificación de la instrucción y lectura de registros. Se decodifica la instrucción obtenida y se leen los valores de los registros fuente del banco de registros.
3. **EX (Execute):** Ejecución o cálculo de dirección.
    - Para instrucciones aritmético-lógicas: la ALU realiza la operación especificada.
    - Para instrucciones de carga/almacenamiento (load/store): la ALU calcula la dirección efectiva de memoria.
    - Para instrucciones de salto (branch): la ALU puede usarse para evaluar la condición de salto y calcular la dirección de destino.
4. **MEM (Memory Access):** Acceso a memoria.
    - Para instrucciones de carga: se lee el dato desde la memoria de datos.
    - Para instrucciones de almacenamiento: se escribe el dato en la memoria de datos.
    - Para instrucciones de salto: se actualiza el PC si la condición de salto se cumple.
5. **WB (Write Back):** Escritura del resultado. El resultado de la operación (ya sea de la ALU o el dato leído de memoria) se escribe de nuevo en el banco de registros.

Entre cada etapa, se utilizan **registros de segmentación** (pipeline registers) como IF/ID, ID/EX, EX/MEM, MEM/WB. Estos registros almacenan los datos y señales de control que necesita la siguiente etapa, permitiendo que cada etapa trabaje en una instrucción diferente de forma concurrente.

**Comparación Ciclo Único vs. Segmentado:**

- **Ciclo Único:** Todas las instrucciones tardan el tiempo de la instrucción más lenta para completarse.
- **Segmentado:** Aunque la latencia de una instrucción individual es la suma de todas las etapas (y puede ser similar o mayor que en ciclo único debido a los registros de pipeline), se puede finalizar una instrucción por ciclo de reloj (idealmente) una vez que el pipeline está lleno. Esto lleva a un mayor throughput.

### Riesgos del Pipeline (Pipeline Hazards)

En un pipeline ideal, el CPI (Ciclos Por Instrucción) sería 1. Sin embargo, existen situaciones, denominadas **riesgos (hazards)**, que impiden que la siguiente instrucción se ejecute en el siguiente ciclo de reloj, disminuyendo el rendimiento (CPI > 1).

Hay tres tipos principales de riesgos:

1. **Riesgos Estructurales:**
    
    - **Causa:** Ocurren cuando dos o más instrucciones intentan utilizar el mismo recurso hardware al mismo tiempo, y el hardware no puede soportar ese uso concurrente. Un ejemplo clásico sería si la memoria de instrucciones y la de datos fueran una sola (arquitectura Von Neumann) y una instrucción `lw` (en su etapa MEM) intentara acceder a memoria al mismo tiempo que la etapa IF de otra instrucción intenta buscar la siguiente instrucción.
    - **Soluciones:**
        - **Duplicar Recursos:** Por ejemplo, usar memorias separadas para instrucciones y datos (arquitectura Harvard), que es común en MIPS.
        - **Insertar Esperas (Stalls/Bubbles):** Detener el pipeline hasta que el recurso esté disponible.
2. **Riesgos de Datos:**
    
    - **Causa:** Ocurren cuando una instrucción depende del resultado de una instrucción anterior que aún no ha completado su ejecución y, por lo tanto, el dato necesario no está disponible. Hay tres tipos de dependencias de datos:
        - **RAW (Read After Write):** Una instrucción intenta leer un operando antes de que una instrucción anterior lo escriba. Este es el tipo más común y problemático en pipelines simples como el de MIPS.
        - **WAW (Write After Write):** Una instrucción intenta escribir un operando antes de que una instrucción anterior escriba sobre el mismo operando. (Menos común en pipelines MIPS simples con escritura en la etapa WB).
        - **WAR (Write After Read):** Una instrucción intenta escribir un destino antes de que una instrucción anterior lo haya leído como fuente. (Generalmente no es un problema en pipelines MIPS que leen operandos en ID y escriben en WB).
    - **Alcance del Conflicto RAW:** Una escritura en un registro puede afectar a las siguientes dos o tres instrucciones si intentan leer ese registro antes de que el valor se haya escrito en el banco de registros (etapa WB).
    - **Soluciones:**
        - **Adelantamiento (Forwarding/Bypassing):** Consiste en tomar el resultado de una etapa anterior (por ejemplo, la salida de la ALU en la etapa EX, o el dato leído de memoria en la etapa MEM) y enviarlo directamente como entrada a la ALU o a la unidad de datos de una instrucción posterior que lo necesita, sin esperar a que se escriba en el banco de registros. Esto se implementa con multiplexores y una "Unidad de Adelantamiento" (Forwarding Unit) que detecta estas dependencias.
        - **Detención del Pipeline (Stalling) + NOPs:** Hay casos donde el adelantamiento no es suficiente, como una instrucción de carga (`lw`) seguida inmediatamente por una instrucción que usa el resultado cargado. El dato de memoria solo está disponible después de la etapa MEM. En esta situación, el pipeline debe detenerse por un ciclo (insertar una "burbuja" o `nop` - no operation). Esto lo maneja una "Unidad de Detección de Riesgo" (Hazard Detection Unit).
3. **Riesgos de Control (o de Salto):**
    
    - **Causa:** Ocurren con las instrucciones de salto (condicionales o incondicionales). La decisión de si se toma el salto o no, y la dirección de destino del salto, no se conocen hasta etapas tardías del pipeline (por ejemplo, EX o MEM). Mientras tanto, el pipeline ya ha comenzado a buscar y procesar las instrucciones secuencialmente siguientes al salto. Si el salto se toma, estas instrucciones cargadas incorrectamente deben ser descartadas.
    - **Soluciones:**
        - **Esperar (Stall):** Detener el pipeline hasta que se resuelva el salto. Esto es simple pero ineficiente.
        - **Predecir que el Salto No se Toma (Predict Not Taken):** Continuar ejecutando secuencialmente. Si la predicción es incorrecta (el salto sí se toma), las instrucciones incorrectamente cargadas deben ser invalidadas ("flusheadas" o vaciadas del pipeline) y se pierde el trabajo realizado en ellas. Se carga una instrucción `nop` en el registro IF/ID para anular la instrucción incorrecta.
        - **Predecir que el Salto Se Toma (Predict Taken):** Similar al anterior, pero se asume que el salto se toma.
        - **Salto Retardado (Delayed Branch):** Se define que una o más instrucciones inmediatamente después de la instrucción de salto (en el "slot de retardo de salto" o delay slot) siempre se ejecutan, independientemente de si el salto se toma o no. El compilador intenta llenar estos slots con instrucciones útiles (que deberían ejecutarse de todas formas, o que no afectan el resultado si el salto no se toma, o `nop`s).
        - **Adelantar el Cálculo de la Condición y Dirección del Salto:** Mover la lógica de cálculo de la condición y la dirección de destino del salto a etapas más tempranas del pipeline (por ejemplo, a la etapa ID). Esto reduce el número de ciclos perdidos.
        - **Predicción Dinámica de Saltos:** Utilizar hardware adicional (como un buffer de predicción de saltos o Branch Target Buffer - BTB, y/o máquinas de estados) para predecir el comportamiento de los saltos basándose en su historial de ejecución. Si la predicción es incorrecta, se vacía el pipeline.

### Pipelining y Paralelismo a Nivel de Instrucción (ILP)

La segmentación es una forma de explotar el **Paralelismo a Nivel de Instrucción (Instruction-Level Parallelism - ILP)**, permitiendo que múltiples instrucciones estén en diferentes fases de ejecución al mismo tiempo.

- **Procesador Escalar con Pipeline (como el MIPS descrito):** Intenta lograr un CPI de 1, aunque los riesgos lo dificultan. Las instrucciones se "lanzan" (inician) una por ciclo de reloj.
- **Mejoras - Múltiple Issue (Lanzamiento Múltiple):** Para mejorar aún más el rendimiento (lograr CPI < 1), se pueden replicar componentes del procesador para permitir "lanzar" más de una instrucción por ciclo de reloj.
    - **Multiple Issue Estático (VLIW - Very Long Instruction Word):** Las decisiones sobre qué instrucciones lanzar juntas las toma el compilador.
    - **Multiple Issue Dinámico (Superescalar):** Las decisiones sobre qué instrucciones lanzar juntas las toma el hardware durante la ejecución.

Este resumen cubre los conceptos fundamentales presentados en el documento PDF sobre la segmentación en procesadores MIPS.