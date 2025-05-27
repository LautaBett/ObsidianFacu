creo que habla sobre el forwarding pero no se 
al tenes q esperar a una instruccion anteiror genera q tarde mas
deja q la instruccion interactur con un valor r1 equivoacado, porque el real lo tine la ejecucion anteriorespera a que el valor correcto este en el write backing par mandarlo a donde si tiene q ir, hay una instruccion que escribe un resultado en el banco de registros?  si escribve, el regristro en el que escribe es iugla al sregistro priemero o segunod  que lee una o otra, si es asi amdno el valor ese a la entrada correspondiente de la alu, esto se llama dependenia con la instruccion inmediantamente siguiente y a la otra con la de 2 lugares abajo, a la alu le doy una entrada primra si no hya problema/riesgo, siexiste el  problema voy a tener q cambiar la entrada uno que es la que viene de ex mem, exmem es el registro entre e y m  , dentro del banco de registrso en maestro ecribe flanco de bajada y el esclavo en flanco de subida, eltiempo del clock esta asociaod a la etapa que mas tarde,  que el cpi sea 1 significa que no hay riesgo de datos, eso quiere decir que el cpi va a ser uno para la dependecia de datos si tengo ford wanring, el cpi es un promedio, que me de el cpi distinto de 1 significa que hay riessgo, toda instruccion viendolo desde la salida al final simere tarda un ciclo de relog, pero si esta cuasa conflicco con otra, los ciclos de reduccion asosiados se los encajo a siguiente,osea se ven reeflejodo en el segnod pero son a causa del primero, cpi de datos es sumar todos los datos dividido cantidad de instrucciones, ej un add tarda un ciclo pero por conflicots hace tardar 2 ciclos mas a un mul siguiente se dice que el add tiene 1 +2 ciclos, y el mul 1 ciclo, banco de registro tiene master y algo mas q no llegeu a escuchar, la solucoin que usamos es la de inversion del banco de registros, si leo y escrubi en r1 al mismo tiempo, lo que hacemos es preguntamos si el rs es igual al rd me genera un boolean, con ese controlu un mux, si da cero mando por rs a la salida,si da uno son iguales y entonces directamnete le hago un bypas y lo que se esta escribiendo lo mando al mux y de ahi a la saldia, que esto tmb es fordwading ya que adelante un ciclo, otra solucion es ak banco de registros le pongo un relog inverso, entoces funciona iguak pero lo estoy adelantando medio ciclo, esta es mas dificil de ver, las funciones solo lon lectura de memoria y escritura de memoria, en el salto particular de los saltos hay que enfrentarse a resolver riesgos de control , necesito saber que ocurren 4 cossa con los saltos 0 donde meter un salto, usualmente en la decodificacion, 1  reconocer el salto, 2 calcular la direccion de salto, osea calcular el target, cuando la instruccion de salto este en, osea calcula t, 3 etapa de ejecucuoin evalua la condicion, osea calcula la condicion ,  if r1 == r2 entonces pc + target, else pc +4, 4 actualizar pc susamente lo hacemos en el ciclo siguiente al calulo de la condicion, hasta los mux tardan , las memoria pueden ser cache, q son mas rapidas, que no ha fordwading sigin¡fica quenno tenemos deteccion de fordwading pero si deteccion de riesgos, sin forwading hya comlictos en los procesos que hacen q se tarde mas ciclos lo que genera un mayor cpi, el forwading el cpi es siemrre uno ya q pone hardward para que no haya conflictos entoces, los porcesos son simepre de un ciclo, si yo le doy prioridad al fetching ,    si el procesar es hardvard se que el cpi es 1 y si es flonormad o omo se llame el cpi es 2, en el procesador de 6 etapas hay otro problema mas, si es hardarv y tiene fordwading solo afecta un loadword, ya q genera un problema inevitable por harvard, 


¡Claro! Parece que tus notas de la [[Clase 13-5]] son un buen resumen de los conceptos clave sobre **riesgos de datos (data hazards)**, **forwarding (adelantamiento)** y **riesgos de control (control hazards)** en arquitecturas segmentadas (pipelined).

Voy a intentar corregir y expandir la información basándome en lo que has escrito:

---

### Correcciones y Aclaraciones sobre [[Clase 13-5]]

#### **1. Riesgos de Datos y la Necesidad de Esperar**

*   **Tu nota:** "al tenes q esperar a una instruccion anteiror genera q tarde mas"
*   **Corrección/Expansión:** Correcto. Cuando una instrucción necesita el resultado de una instrucción anterior que aún no ha completado su escritura en el banco de registros (etapa WB - Write Back), se produce un **riesgo de datos** (específicamente, un RAW - Read After Write). Si no se maneja, la instrucción actual leería un valor incorrecto. La solución más simple es **detener (stall)** el pipeline, insertando burbujas (ciclos NOP), lo que efectivamente hace que el programa tarde más.

#### **2. Forwarding (Adelantamiento)**

*   **Tu nota:** "deja q la instruccion interactur con un valor r1 equivoacado, porque el real lo tine la ejecucion anteriorespera a que el valor correcto este en el write backing par mandarlo a donde si tiene q ir, hay una instruccion que escribe un resultado en el banco de registros? si escribve, el regristro en el que escribe es iugla al sregistro priemero o segunod que lee una o otra, si es asi amdno el valor ese a la entrada correspondiente de la alu, esto se llama dependenia con la instruccion inmediantamente siguiente y a la otra con la de 2 lugares abajo, a la alu le doy una entrada primra si no hya problema/riesgo, siexiste el problema voy a tener q cambiar la entrada uno que es la que viene de ex mem, exmem es el registro entre e y m"
*   **Corrección/Expansión:**
    *   El **forwarding** (o adelantamiento/bypass) es una técnica para resolver muchos riesgos de datos sin necesidad de detener el pipeline.
    *   En lugar de esperar a que el resultado se escriba en el banco de registros (etapa WB), si el resultado ya está disponible en la salida de la ALU (al final de la etapa EX) o en el registro de segmentación MEM/WB (después de la etapa MEM), se puede "adelantar" directamente a la entrada de la ALU para la instrucción dependiente que está en su etapa EX.
    *   **Lógica de Detección de Forwarding:**
        *   Se compara el registro destino (rd) de instrucciones previas (que están en etapas EX/MEM o MEM/WB) con los registros fuente (rs, rt) de la instrucción actual (en etapa ID, a punto de pasar a EX).
        *   **Ejemplo de forwarding EX/MEM a EX:**
            *   `ADD R1, R2, R3` (R1 es el destino, resultado disponible al final de EX de ADD)
            *   `SUB R4, R1, R5` (SUB necesita R1 en su etapa EX)
            *   El resultado de ADD (que estaría en el registro de segmentación EX/MEM) se reenvía a la entrada de la ALU para SUB.
        *   **Ejemplo de forwarding MEM/WB a EX:**
            *   `LW R1, 0(R2)` (R1 es el destino, resultado disponible al final de MEM de LW)
            *   `NOP` (o una instrucción que no dependa de R1)
            *   `ADD R4, R1, R5` (ADD necesita R1 en su etapa EX)
            *   El dato leído de memoria por LW (que estaría en el registro de segmentación MEM/WB) se reenvía a la entrada de la ALU para ADD.
    *   Se utilizan **multiplexores (MUX)** en las entradas de la ALU para seleccionar si el operando proviene del banco de registros o de una ruta de forwarding.
    *   `EX/MEM` es el registro de segmentación entre la etapa de Ejecución (EX) y la etapa de Acceso a Memoria (MEM).

#### **3. Banco de Registros: Escritura y Lectura en el Mismo Ciclo**

*   **Tu nota:** "dentro del banco de registrso en maestro ecribe flanco de bajada y el esclavo en flanco de subida"
*   **Corrección/Expansión:** Esto se refiere a una técnica para manejar la situación donde una instrucción escribe en un registro en la etapa WB y otra instrucción lee el *mismo* registro en la etapa ID, ¡todo en el mismo ciclo de reloj! Para asegurar que la instrucción en ID lea el valor *nuevo* (que se está escribiendo) y no el viejo:
    *   Una solución común es diseñar el banco de registros para que **la escritura se complete en la primera mitad del ciclo de reloj y la lectura ocurra en la segunda mitad**. Esto asegura que la lectura siempre vea el resultado de la escritura si ocurren en el mismo ciclo al mismo registro.
    *   La mención de "maestro-esclavo" y flancos de subida/bajada es una forma de implementar esta lógica temporal dentro del ciclo.

*   **Tu nota:** "la solucoin que usamos es la de inversion del banco de registros, si leo y escrubi en r1 al mismo tiempo, lo que hacemos es preguntamos si el rs es igual al rd me genera un boolean, con ese controlu un mux, si da cero mando por rs a la salida,si da uno son iguales y entonces directamnete le hago un bypas y lo que se esta escribiendo lo mando al mux y de ahi a la saldia, que esto tmb es fordwading ya que adelante un ciclo"
*   **Corrección/Expansión:** Esto describe un **forwarding interno al banco de registros** o la técnica de "escribir primero, leer después" dentro del mismo ciclo. Si la instrucción en WB está escribiendo en `Rd` y la instrucción en ID está leyendo de `Rs` (y `Rd == Rs`), el valor que se está escribiendo se puede "bypassear" directamente a la salida de lectura del banco de registros para la instrucción en ID. Esto evita un ciclo de stall.

*   **Tu nota:** "otra solucion es ak banco de registros le pongo un relog inverso, entoces funciona iguak pero lo estoy adelantando medio ciclo, esta es mas dificil de ver"
*   **Corrección/Expansión:** Esto es otra forma de referirse a la estrategia de temporización dentro del ciclo de reloj (escribir en una mitad, leer en la otra) para asegurar que la lectura obtenga el dato actualizado si hay una escritura concurrente al mismo registro.

#### **4. CPI (Ciclos Por Instrucción)**

*   **Tu nota:** "el tiempo del clock esta asociaod a la etapa que mas tarde"
*   **Corrección/Expansión:** Correcto. La duración del ciclo de reloj ($T_{clk}$) está determinada por la etapa más lenta del pipeline, más el overhead de los registros de segmentación.

*   **Tu nota:** "que el cpi sea 1 significa que no hay riesgo de datos, eso quiere decir que el cpi va a ser uno para la dependecia de datos si tengo ford wanring"
*   **Corrección/Expansión:** Un CPI ideal de 1 significa que, en promedio, se completa una instrucción por ciclo de reloj. El forwarding ayuda a acercarse a este ideal al eliminar la mayoría de los stalls por riesgos de datos. Sin embargo, hay un caso particular, el **riesgo de datos por carga (load-use hazard)**, donde incluso con forwarding se necesita 1 ciclo de stall.
    *   Ej: `LW R1, 0(R2)` seguido inmediatamente por `ADD R3, R1, R4`. El dato de `LW` está disponible al final de la etapa MEM, pero `ADD` lo necesita al inicio de su etapa EX. Esta diferencia de un ciclo no puede ser completamente resuelta por forwarding estándar y requiere un stall.

*   **Tu nota:** "el cpi es un promedio, que me de el cpi distinto de 1 significa que hay riessgo"
*   **Corrección/Expansión:** Correcto. CPI es el promedio de ciclos por instrucción. Un CPI > 1 indica la presencia de stalls (debido a riesgos de datos, control o estructurales).

*   **Tu nota:** "toda instruccion viendolo desde la salida al final simere tarda un ciclo de relog, pero si esta cuasa conflicco con otra, los ciclos de reduccion asosiados se los encajo a siguiente,osea se ven reeflejodo en el segnod pero son a causa del primero"
*   **Corrección/Expansión:** Cada instrucción pasa por cada etapa del pipeline, y cada etapa toma (idealmente) un ciclo de reloj. La latencia total de una instrucción es N ciclos (para N etapas). Si una instrucción causa un stall, ese stall retrasa a la instrucción misma y a todas las que vienen detrás. El "costo" del stall se asocia a la instrucción que lo causó, aunque el efecto visible es un retraso en la finalización de las instrucciones subsiguientes.

*   **Tu nota:** "cpi de datos es sumar todos los datos dividido cantidad de instrucciones, ej un add tarda un ciclo pero por conflicots hace tardar 2 ciclos mas a un mul siguiente se dice que el add tiene 1 +2 ciclos, y el mul 1 ciclo"
*   **Corrección/Expansión:** El CPI se calcula como: $CPI = \frac{\text{Ciclos totales}}{\text{Número de instrucciones}}$. Si un `ADD` causa 2 ciclos de stall, esos 2 ciclos se suman al total de ciclos del programa. El `ADD` efectivamente "cuesta" $1 + 2 = 3$ ciclos en términos de su impacto en el tiempo total, y el `MUL` comenzará 2 ciclos más tarde.

#### **5. Riesgos de Control (Saltos)**

*   **Tu nota:** "en el salto particular de los saltos hay que enfrentarse a resolver riesgos de control , necesito saber que ocurren 4 cossa con los saltos 0 donde meter un salto, usualmente en la decodificacion, 1 reconocer el salto, 2 calcular la direccion de salto, osea calcular el target, cuando la instruccion de salto este en, osea calcula t, 3 etapa de ejecucuoin evalua la condicion, osea calcula la condicion , if r1 == r2 entonces pc + target, else pc +4, 4 actualizar pc susamente lo hacemos en el ciclo siguiente al calulo de la condicion"
*   **Corrección/Expansión:** Muy bien descrito. Los riesgos de control ocurren con las instrucciones de salto (branches) y bifurcaciones.
    1.  **Detección del Salto:** Generalmente en la etapa ID (Decodificación). Se reconoce que la instrucción es un salto.
    2.  **Cálculo de la Dirección de Salto (Target Address):** Para saltos condicionales relativos al PC (ej. `BEQ`, `BNE`), el offset se suma al PC. Esto puede comenzar en ID y completarse en EX.
    3.  **Evaluación de la Condición de Salto:** Para saltos condicionales, la condición (ej. `R1 == R2`) se evalúa en la etapa EX.
    4.  **Actualización del PC:** Si el salto se toma (condición verdadera), el PC se actualiza con la dirección de destino. Si no se toma, PC = PC + 4 (o el tamaño de la instrucción). Esta decisión se toma al final de EX o en MEM.
    *   **Problema:** Para cuando se sabe si el salto se toma o no y cuál es la dirección destino (final de EX), ya se han cargado (fetched) varias instrucciones incorrectas en el pipeline (las que seguían secuencialmente).
    *   **Soluciones Comunes:**
        *   **Stall (Detener):** Congelar el pipeline hasta que se resuelva el salto. Ineficiente.
        *   **Predecir No Tomado (Predict Not Taken):** Continuar cargando instrucciones secuenciales. Si el salto se toma, anular las instrucciones incorrectas (flush) y cargar desde el destino.
        *   **Predecir Tomado (Predict Taken):** Similar, pero se asume que el salto se toma.
        *   **Salto Retardado (Delayed Branch):** Se ejecuta una o más instrucciones después del salto (en el "delay slot") independientemente de si el salto se toma o no. El compilador intenta llenar estos slots con instrucciones útiles.
        *   **Branch Target Buffer (BTB) y Branch History Table (BHT):** Hardware para predecir la dirección y el resultado de los saltos.

#### **6. Otros Puntos Importantes**

*   **Tu nota:** "hasta los mux tardan"
*   **Corrección/Expansión:** Correcto. Todos los componentes lógicos, incluyendo multiplexores, tienen retardos de propagación que contribuyen al tiempo total de una etapa del pipeline.

*   **Tu nota:** "memoria pueden ser cache, q son mas rapidas"
*   **Corrección/Expansión:** Sí, las memorias caché son memorias más pequeñas y rápidas que almacenan copias de los datos/instrucciones más frecuentemente usados de la memoria principal, reduciendo la latencia de acceso.

*   **Tu nota:** "que no ha fordwading sigin¡fica quenno tenemos deteccion de fordwading pero si deteccion de riesgos, sin forwading hya comlictos en los procesos que hacen q se tarde mas ciclos lo que genera un mayor cpi"
*   **Corrección/Expansión:** Exacto. Si no hay hardware de forwarding, **aún se necesita la detección de riesgos (hazard detection unit)**. Cuando se detecta un riesgo de datos, la única opción es insertar stalls, lo que incrementa el CPI.

*   **Tu nota:** "el forwading el cpi es siemrre uno ya q pone hardward para que no haya conflictos entoces, los porcesos son simepre de un ciclo"
*   **Corrección/Expansión:** El forwarding reduce significativamente los stalls, acercando el CPI a 1. Sin embargo, como se mencionó, el **load-use hazard** típicamente requiere 1 ciclo de stall incluso con forwarding. Por lo tanto, el CPI no será *siempre* 1 si existen estas dependencias. Cada instrucción sigue tardando N ciclos en atravesar el pipeline (latencia), pero el *throughput* (instrucciones completadas por ciclo) se acerca a 1.

*   **Tu nota:** "si el procesar es hardvard se que el cpi es 1 y si es flonormad o omo se llame el cpi es 2"
*   **Corrección/Expansión:**
    *   **Arquitectura Harvard:** Tiene buses y memorias separadas para instrucciones y datos. Esto puede eliminar **riesgos estructurales** al permitir buscar la siguiente instrucción y acceder a datos para la instrucción actual simultáneamente. No garantiza CPI=1 por sí solo, ya que los riesgos de datos y control aún deben manejarse.
    *   "flonormad" probablemente es una mala transcripción de **Von Neumann**, que usa una única memoria y bus para instrucciones y datos. Esto puede llevar a riesgos estructurales si una instrucción necesita acceder a memoria para datos mientras otra necesita acceder para ser fetched, si no se gestiona adecuadamente (usualmente con cachés separadas L1I y L1D aunque la memoria principal sea unificada).
    *   El CPI depende de la frecuencia de los hazards y cómo se manejan (stalls, forwarding, predicción de saltos), no directamente de si es Harvard o Von Neumann, aunque Harvard puede facilitar un menor CPI al reducir un tipo de hazard.

*   **Tu nota:** "en el procesador de 6 etapas hay otro problema mas, si es hardarv y tiene fordwading solo afecta un loadword, ya q genera un problema inevitable por harvard"
*   **Corrección/Expansión:** Un pipeline de 6 etapas podría cambiar la dinámica de cuándo los datos están disponibles y cuándo se necesitan, lo que podría alterar la penalización por load-use hazard o introducir nuevos puntos de forwarding. El problema del load-use hazard (donde una instrucción de carga es seguida inmediatamente por una instrucción que usa su resultado) es inherente a la latencia de la memoria en un pipeline estándar de 5 etapas (IF, ID, EX, MEM, WB) y requiere un stall. La arquitectura Harvard no *causa* este problema, sino que la latencia de la etapa MEM es la clave.

---

¡Espero que esta revisión y expansión te sea útil para entender mejor los conceptos de tu clase de arquitectura de computadoras! Has capturado muchos de los puntos esenciales.