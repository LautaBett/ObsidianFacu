Se tiene un sistema ordenador con un procesador segmentado en 4 etapas. 
1) Captura instrucciones (*CI*): se lee la instrucción a ejecutar. 
2) Decodificación (*DE*): se decodifica la instrucción, se leen los operandos de los registros internos, se calcula la dirección efectiva en las instrucciones con memoria y en su caso se calcula la dirección de salto. 
3) Ejecución (*EJ*): se ejecuta la operación aritmética o lógica, se ejecuta la lectura en memoria y se determina si los saltos son o no efectivos. La fase de ejecución de las instrucciones se realiza en un ciclo para todas las instrucciones excepto las de coma flotante, que necesitan 4 ciclos. En este caso la ALU queda ocupada durante los cuatro ciclos y se producen las detenciones pertinentes. 
4) Escritura (*W*): se escribe el resultado en un registro interno o, en su caso, se almacena el dato en memoria. Suponer que no existen riesgos de datos y que con respecto a los riesgos de control la estrategia es detener la CPU hasta resolver el riesgo. Estadísticamente, el porcentaje de instrucciones empleadas en un programa se indica en la tabla adjunta.


| Tipo          | Load/Store Saltos | condicionales | Aritmética con<br>Enteros | Aritmética<br>pto. flotante |
| ------------- | ----------------- | ------------- | ------------------------- | --------------------------- |
| Porcentaje    | 20%               | 15%           | 45%                       | 20%                         |
| CPI calculado | 2                 | 3             | 1                         | 4                           |

*NOTA*: Para calcular las distintas mejoras, no tener en cuenta el tiempo de llenado del procesador y cuando corresponda, suponer que el 100% de los saltos son efectivos (el peor caso posible).
Se realizan dos mejoras consecutivas:

a) Se duplica el bus y de tener un bus común para instrucciones y datos se diseña una arquitectura tipo Harvard.

b) Se rediseña la unidad de coma flotante, de tal forma que se reduce a al mitad el tiempo de ejecución para estas instrucciones. Se pide, aplicando necesariamente la ley de Amdahl definir la ganancia obtenida tras las dos mejoras.

### Load/Store

|     | 1   | 2   | 3       | 4       |
| --- | --- | --- | ------- | ------- |
| CI  | LW  | N   | *NOP* | N+1     |
| DE  |     | LW  | N       | *NOP* |
| EJ  |     |     | LW      | N       |
| W   |     |     |         | LW      |


$CPI_{Load/Stores}= T_{ejecucion} + NOPS = 1 + 1 = 2$

### Condicionales

==No prediccion==

|     | 1   | 2       | 3       | 4       |
| --- | --- | ------- | ------- | ------- |
| CI  | BEQ | *NOP* | *NOP* | T/N     |
| DE  |     | BEQ     | *NOP* | *NOP* |
| EJ  |     |         | BEQ     | *NOP* |
| W   |     |         |         | BEQ     |

$CPI_{Condicionales}= T_{ejecucion} + NOPS = 1 + 2 = 3$

### Aritmética con Enteros

==Sin riesgo==

|     | 1   | 2   | 3   | 4   |
| --- | --- | --- | --- | --- |
| CI  | N   | N+1 | N+2 | N+3 |
| DE  |     | N   | N+1 | N+2 |
| EJ  |     |     | N   | N+1 |
| W   |     |     |     | N   |

$CPI_{enteros} = T_{ejecucion} + NOPS = 1$

### Aritmética pto. flotante

|     | 1   | 2   | 3   | 4       | 5       | 6       | 7       | 8       |
| --- | --- | --- | --- | ------- | ------- | ------- | ------- | ------- |
| CI  | N   | N+1 | N+2 | N+2     | N+2     | N+2     |         |         |
| DE  |     | N   | N+1 | N+1     | N+1     | N+1     | N+2     |         |
| EJ  |     |     | N   | N       | N       | N       | N+1     | N+2     |
| W   |     |     |     | *NOP* | *NOP* | *NOP* | N       | N+1     |
|     |     |     |     |         | *NOP* | *NOP* | *NOP* | N       |
|     |     |     |     |         |         | *NOP* | *NOP* | *NOP* |

$CPI_{enteros} = T_{ejecucion} + NOPS = 3 + 1 = 4$ 


$CPI_{original} = (2*0,2) + (3*0.15) + (1*0,45) + (4*0,20) = 2,1$

a)

$CPI_{nuevo} = (1*0,2) + (3*0.15) + (1*0,45) + (4*0,20) = 1,9$

b)

$CPI_{nuevo} = (2*0,2) + (3*0.15) + (1*0,45) + (2*0,20) = 1.7$


*Ambas* *mejoras*

$CPI_{nuevo} = (1*0,2) + (3*0.15) + (1*0,45) + (2*0,20) = 1.5$

$a_{cc} = \frac{CPI_{original}}{CPI_{nuevo}} = \frac{2,1}{1,5} = 1,4$

con amdhal

$f_{m1} = \frac{0,2*2}{2.1} = \frac{4}{21}$
$a_{m1} = 2$

$f_{m2} = \frac{0,2*4}{2.1} = \frac{8}{21}$
$a_{m2} = 2$


$a_{cc} = \frac{1}{(1-(\frac{4}{21}+\frac{8}{21}))+(\frac{4}{21}/2+\frac{8}{21}/2)}$

Primero, simplificamos los términos:

*   $\frac{4}{21} + \frac{8}{21} = \frac{12}{21}$
*   $\frac{4}{21} / 2 = \frac{4}{42} = \frac{2}{21}$
*   $\frac{8}{21} / 2 = \frac{8}{42} = \frac{4}{21}$

Sustituyendo estos valores en la fórmula:

$a_{cc} = \frac{1}{(1-\frac{12}{21})+(\frac{2}{21}+\frac{4}{21})}$

$a_{cc} = \frac{1}{(\frac{21-12}{21})+(\frac{6}{21})}$

$a_{cc} = \frac{1}{\frac{9}{21}+\frac{6}{21}}$

$a_{cc} = \frac{1}{\frac{15}{21}}$

$a_{cc} = \frac{21}{15} = \frac{7}{5} = 1.4$

Entonces, la aceleración combinada ($a_{cc}$) es 1.4.
