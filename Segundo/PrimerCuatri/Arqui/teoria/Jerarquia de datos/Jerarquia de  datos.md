Este documento explica cómo las computadoras manejan la memoria para que funcionen rápido y de manera eficiente, a pesar de que hay diferentes tipos de memoria con distintas velocidades y costos. Se le llama "jerarquía de memoria"[cite: 5, 8].

Aquí te lo resumo de forma sencilla:

### 1. ¿Por qué necesitamos una jerarquía de memoria?
* **El problema**: Los programas usan memoria tanto para su código como para sus datos, y la CPU (el "cerebro" de la computadora) necesita acceder a ellos muy rápido[cite: 2]. El problema es que la memoria más rápida es mucho más cara[cite: 2].
* **La solución**: Se organiza la memoria en varios niveles, como una pirámide[cite: 9]. Cada nivel es más pequeño, más caro y más rápido que el anterior[cite: 9]. Los datos que están en un nivel superior también están en el nivel inferior[cite: 10].
* **Principio de localidad**: Los programas suelen usar las mismas partes de la memoria una y otra vez[cite: 5]. Esto se llama "localidad" y tiene dos tipos[cite: 6]:
    * **Temporal**: Si accedes a algo, es probable que lo vuelvas a necesitar pronto[cite: 6].
    * **Espacial**: Si accedes a algo, es probable que también necesites cosas que están cerca[cite: 7].

### 2. Tipos de memoria (y sus características) [cite: 4]
* **SRAM (RAM estática)**: Muy rápida (0.5 a 2.5 nanosegundos), muy cara ($100 USD/GB$). Se usa en la memoria caché[cite: 4].
* **DRAM (RAM dinámica)**: Más lenta (50 a 70 nanosegundos), más barata ($20 USD/GB$). Es la que usamos como memoria principal (RAM)[cite: 4].
* **Flash**: Más lenta aún (5 a 50 microsegundos), más barata ($1 USD/GB$)[cite: 4].
* **SSD (Disco de estado sólido)**: Más lenta (0.2 milisegundos), más barata ($0.2 USD/GB$)[cite: 4].
* **HDD (Disco rígido)**: La más lenta (5 a 20 milisegundos), la más barata ($0.1 USD/GB$)[cite: 4].

### 3. Conceptos clave
* **Bloque**: Es la unidad mínima de información que se mueve entre los niveles de memoria[cite: 14].
* **Acierto (Hit)**: Cuando la información que busca la CPU ya está en el nivel de memoria más rápido (el "superior")[cite: 18].
* **Fallo (Miss)**: Cuando la información no está en ese nivel y hay que buscarla en un nivel más lento (el "inferior")[cite: 18].
* **Tasa de aciertos/fallos**: Es el porcentaje de veces que hay un acierto o un fallo[cite: 18].
* **Tiempo de acierto**: Lo que tarda en encontrar la información si ya está en el nivel superior[cite: 19].
* **Penalización por fallo**: Es el tiempo extra que se pierde cuando hay un fallo, porque hay que ir a buscar el bloque al nivel inferior y traerlo[cite: 20]. Esto incluye el tiempo para acceder la primera palabra y el tiempo para transferir el resto del bloque[cite: 21].
* **Tiempo de acceso promedio**: Es el tiempo total promedio que tarda la CPU en acceder a la memoria, teniendo en cuenta aciertos y fallos[cite: 23].

### 4. Memoria caché (el primer nivel) [cite: 17]
* Es una memoria muy rápida y pequeña que está entre la CPU y la memoria principal (RAM)[cite: 17].
* **Cómo se guarda la información (ubicación del bloque)**:
    * **Correspondencia directa**: Cada bloque de memoria principal solo puede ir en un lugar específico de la caché[cite: 27, 28].
    * **Totalmente asociativa**: Un bloque puede ir en cualquier lugar de la caché[cite: 27, 28].
    * **Asociativa por conjuntos**: Es un punto intermedio, un bloque puede ir en un grupo específico de lugares dentro de la caché[cite: 27, 28].
* **Cómo se sabe qué bloque está**: Junto a cada bloque en la caché, se guarda una "etiqueta" (tag) que es parte de la dirección original en la RAM, y un "bit de validez" para saber si esa línea tiene datos válidos[cite: 32].
* **Direccionamiento**: Una dirección de memoria se divide en tres partes para la caché: la etiqueta (tag), el índice (para saber en qué línea de la caché buscar, si no es totalmente asociativa) y el desplazamiento (para saber qué palabra dentro del bloque)[cite: 36].
* **Tamaño del bloque**: Aumentar el tamaño del bloque puede reducir los fallos (por la localidad espacial), pero si es demasiado grande, puede aumentar la competencia en la caché y el tiempo de penalización por fallo[cite: 47].

### 5. Estrategias de reemplazo (cuando la caché está llena y hay un fallo) [cite: 48]
Si la caché está llena y llega un nuevo bloque, hay que sacar uno viejo.
* **Aleatorio**: Se elige un bloque al azar para reemplazar[cite: 51, 52].
* **Pseudo aleatorio**: Similar al aleatorio, pero con una secuencia predecible, útil para depuración[cite: 51, 53].
* **LRU (Least Recently Used - Menos usado recientemente)**: Se reemplaza el bloque que lleva más tiempo sin usarse[cite: 51, 54]. Es una buena estrategia, pero puede ser complicada de implementar en cachés grandes[cite: 85].

### 6. Estrategias de escritura
* **Escritura directa (Write-Through)**: Cuando se escribe un dato, se actualiza tanto en la caché como en la memoria de nivel inferior al mismo tiempo[cite: 90]. Es más sencilla y mantiene la coherencia entre niveles[cite: 93].
* **Postescritura (Write-Back)**: La información se escribe solo en la caché y se actualiza en la memoria inferior solo cuando ese bloque de la caché es reemplazado[cite: 91, 92]. Es más rápida porque las escrituras se hacen a velocidad de la caché[cite: 93].
* **Fallo de escritura**: Si se intenta escribir en un bloque que no está en la caché:
    * **Ubicar en escritura (Write Allocate)**: Se carga el bloque en la caché y luego se escribe[cite: 94].
    * **No ubicar en escritura (Write Around)**: Se modifica directamente en la memoria inferior sin cargarlo en la caché[cite: 95].

### 7. Rendimiento de la caché
El tiempo total que la CPU tarda en ejecutar un programa depende de los ciclos de ejecución de las instrucciones y los ciclos de espera por accesos a memoria (aciertos o penalizaciones por fallos)[cite: 97].

* **Tipos de fallos**:
    * **Forzosos (o "arranque en frío")**: El primer acceso a un bloque, que por fuerza no está en la caché[cite: 100, 101, 102].
    * **Capacidad**: La caché no es lo suficientemente grande para contener todos los bloques que el programa necesita, y algunos se descartan y luego se vuelven a necesitar[cite: 103].
    * **Conflicto**: En cachés de mapeo directo o asociativas por conjuntos, si muchos bloques quieren ir al mismo lugar, se descartan y se vuelven a necesitar[cite: 104].

* **Cachés de datos/instrucciones separadas vs. unificadas**:
    * **Separadas (arquitectura Harvard)**: Tienen una caché para datos y otra para instrucciones. Aumenta el ancho de banda y permite optimizar cada una de forma independiente[cite: 108].
    * **Unificadas (arquitectura Von Neumann)**: Una sola caché para todo. Es más simple y no limita el espacio máximo para datos o instrucciones[cite: 109].

### 8. Memoria virtual (el segundo nivel) [cite: 112]
* La memoria principal (RAM) funciona como una caché para el disco duro[cite: 113].
* Es gestionada por el hardware y el sistema operativo[cite: 113].
* **Beneficios**: Permite que varios programas compartan la memoria, separa los espacios de direcciones y protege los programas entre sí[cite: 113].
* **Diferencias con la caché de CPU**:
    * Los bloques (llamados "páginas" o "segmentos") son mucho más grandes (4KB-64KB)[cite: 115].
    * La penalización por fallo es muchísimo mayor (porque implica acceder al disco)[cite: 115].
    * La tasa de fallos es mucho más baja[cite: 115].
    * El sistema operativo controla el reemplazo de bloques, no solo el hardware[cite: 155].
    * El nivel más bajo (los discos) se comparte con el sistema de archivos del sistema operativo[cite: 157].

### 9. Aspectos físicos de la RAM
* **SRAM**: Más rápida, más cara, menor capacidad. Se usa en las cachés[cite: 118, 119].
* **DRAM**: Más lenta, más barata, mayor capacidad. Se usa en la memoria principal[cite: 120]. Usa un capacitor para guardar la información y tiene doble direccionamiento (RAS y CAS)[cite: 120].
* **Modos de DRAM**: Hay diferentes modos (Page Mode, EDO, SDRAM, DDR) que buscan mejorar la velocidad de acceso, especialmente para datos secuenciales[cite: 128]. Por ejemplo, las DDR (Double Data Rate) transfieren el doble de datos por ciclo de reloj que las SDRAM[cite: 149].

### 10. Rendimiento del sistema global
El tiempo total de la CPU se ve afectado por los ciclos de ejecución, los aciertos de caché y las penalizaciones por fallos de caché. La memoria virtual también impacta el rendimiento a través de cosas como los fallos del TLB (Translation Lookaside Buffer) y los tiempos de acceso al disco[cite: 177, 178].

El documento termina con un **ejemplo práctico** de cómo calcular el tiempo de ejecución y la mejora de rendimiento con una caché. En este ejemplo, se demuestra que una caché mal configurada puede hacer que el rendimiento sea peor que no tener caché[cite: 189, 190].