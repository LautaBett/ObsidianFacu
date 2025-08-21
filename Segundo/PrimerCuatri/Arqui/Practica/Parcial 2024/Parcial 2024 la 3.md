  
- Banco de registro *flanco descendente*, registro segmentacion ascendente  => Dos burbujas en los riesgos de datos   
- Banco de registro *flanco ascendente*, registro segmentacion ascendente  => Tres burbujas en los riesgos de datos  

**3)** Un procesador _original_ segmentado tipo Von Neumann ejecuta las instrucciones en 5 etapas:  
**CI**, _Captura instrucciones_: lectura de la instrucción.  
**D**, _Decodificación_: se decodifica la instrucción y detección de riesgos de control.  
**OP**, _Acceso a operandos_: lectura de operandos del banco de registros, cálculo de dirección efectiva para instrucciones de memoria y dirección efectiva para saltos.  
**EJ**, _Ejecución_: cálculo de la operación aritmético/lógica, lectura en memoria en instrucciones LOAD y resolución de la condición de salto.  
**W**, _Escritura_: almacenamiento en banco de registros o almacenamiento en memoria para instrucciones STORE.

El procesador no tiene _forwarding_ para eliminación de riesgos de datos y el banco de registro escribe en **flanco descendente**. Las instrucciones de punto flotante requieren 3 ciclos de cálculo. Respecto de los riesgos de control se detiene la CPU hasta resolver el riesgo. *El compilador elimina dependencias RAW entre los LOAD y la instrucción siguiente mediante reordenamiento de instrucciones*, pero no soluciona ocurrencias de STORE seguidos de LOAD, que en el programa de prueba se dan en el 30% de los casos para igual cantidad de LOADs y STOREs y tampoco resuelve dependencias RAW para las instrucciones aritmético-lógicas.

El porcentaje de instrucciones empleadas para un programa dado es el siguiente:

| Load/Store | Saltos | Aritmética de enteros | Pto Flotante |
| ---------- | ------ | --------------------- | ------------ |
| 30%        | 10%    | 35%                   | 25%          |

Se diseña un procesador **nuevo** incluyendo varias mejoras:

1. se implementa una arquitectura tipo Harvard,
2. se incorpora una unidad de _forwarding_,
3. se implementa una unidad de predicción de saltos con predicción a no efectivo,
4. se modifica el compilador para separar los STORE y el LOAD siguiente,
5. se reduce el tiempo de cálculo de Punto Flotante a 2 ciclos.

En estas condiciones calcule la aceleración del procesador **nuevo** respecto del **original** para los siguientes 2 casos.  
**A)** Para el análisis suponga siempre la **peor** condición de trabajo para los riesgos de saltos.  
**B)** Para el análisis suponga la **mejor** condición de trabajo.

---
### Load/Store

*Riesgo estructural*

|     | 1   | 2   | 3   | 4   | 5   |
| --- | --- | --- | --- | --- | --- |
| CI  | LW  | N   | N+1 | n+2 | n+2 |
| D   |     | LW  | N   | N+1 | n+1 |
| OP  |     |     | LW  | N   | nop |
| EJ  |     |     |     | LW  | N   |
| W   |     |     |     |     | LW  |

*Riesgo de datos*


|     | 1   | 2   | 3   | 4   | 5       | 6       |
| --- | --- | --- | --- | --- | ------- | ------- |
| CI  | LW  | ADD | SUB | N   | N       | N+1     |
| D   |     | LW  | ADD | SUB | SUB     | N       |
| OP  |     |     | LW  | ADD | **NOP** | SUB     |
| EJ  |     |     |     | LW  | ADD     | **NOP** |
| W   |     |     |     |     | LW      | ADD     |


*SW seguido de LW*

|     | 1   | 2   | 3   | 4   | 5       |
| --- | --- | --- | --- | --- | ------- |
| CI  | SW  | LW  | N   | N+1 | N+1     |
| D   |     | SW  | LW  | N   | N       |
| OP  |     |     | SW  | LW  | LW      |
| EJ  |     |     |     | SW  | **NOP** |
| W   |     |     |     |     | SW      |

$CPI_{Condicionales}= T_{ejecucion} + NOPS = 1 + 2 + 1  = 4$

Calculo: ==1x0,3== + 0,3x3 + (0,3x0,3x1)

---
### Saltos

**CPU parado**

|     | 1   | 2   | 3       | 4       | 5       | 5       |
| --- | --- | --- | ------- | ------- | ------- | ------- |
| CI  | BEQ | N   | N       | N       | T       | N+1     |
| D   |     | BEQ | **NOP** | **NOP** | **NOP** | N       |
| OP  |     |     | BEQ     | **NOP** | **NOP** | **NOP** |
| EJ  |     |     |         | BEQ     | **NOP** | **NOP** |
| W   |     |     |         |         | BEQ     | BEQ     |
$CPI_{Condicionales}= T_{ejecucion} + NOPS = 1 + 3 = 4$


**Prediccion efectiva**

|     | 1   | 2   | 3   | 4   | 5       | 5       |
| --- | --- | --- | --- | --- | ------- | ------- |
| CI  | BEQ | N   | N+1 | T   | T+1     | N+2     |
| D   |     | BEQ | N   | N+1 | T       | **NOP** |
| OP  |     |     | BEQ | N   | **NOP** | N+1     |
| EJ  |     |     |     | BEQ | **NOP** | N       |
| W   |     |     |     |     | BEQ     | BEQ     |

**Prediccion no efectiva**

|     | 1   | 2   | 3   | 4   | 5       | 6   |
| --- | --- | --- | --- | --- | ------- | --- |
| CI  | BEQ | N   | N+1 | N+2 | T       | N+3 |
| D   |     | BEQ | N   | N+1 | **NOP** | N+2 |
| OP  |     |     | BEQ | N   | **NOP** | N+1 |
| EJ  |     |     |     | BEQ | **NOP** | N   |
| W   |     |     |     |     | BEQ     | BEQ |

---
### Aritmetica de enteros

*sin forwarding*

|     | 1   | 2   | 3   | 4       | 6       | 7       |
| --- | --- | --- | --- | ------- | ------- | ------- |
| CI  | ADD | SUB | N+1 | N+1     | N+1     | N+2     |
| D   |     | ADD | SUB | SUB     | SUB     | N+1     |
| OP  |     |     | ADD | **NOP** | **NOP** | SUB     |
| EJ  |     |     |     | ADD     | **NOP** | **NOP** |
| W   |     |     |     |         | ADD     | **NOP** |
$CPI_{Condicionales}= T_{ejecucion} + NOPS = 1 + 2 = 3$


---

### Pto flotante

|     | 1   | 2   | 3   | 4       | 5       | 6       | 7   |
| --- | --- | --- | --- | ------- | ------- | ------- | --- |
| CI  | N   | N+1 | N+2 | N+2     | N+2     | N+3     | N+4 |
| D   |     | N   | N+1 | N+1     | N+1     | N+2     | N+3 |
| OP  |     |     | N   | N       | N       | N+1     | N+2 |
| EJ  |     |     |     | **NOP** | **NOP** | N       | N+1 |
| W   |     |     |     |         | **NOP** | **NOP** | N   |

$CPI_{Condicionales}= T_{ejecucion} + NOPS = 1 + 2 = 3$


---

$CPI_{original} = CPI_{Load/Store} + CPI_{Condicional} + CPI_{Enteros} + CPI_{Flotantes}$

Datos que no cambian

*Original:*
$CPI_{Load/Store} = (4*0,3) + (0,3*0,3*1)$
$CPI_{Enteros} = (3*0,35)$
$CPI_{Flotantes} = (3*0,25)$

*Mejora:*
$CPI_{Load/Store} = (4*0,3) + (0,3*0,3*1) \rightarrow (1*0,3)$ 
$CPI_{Enteros} = (3*0,35) \rightarrow (1*0,35)$ 
$CPI_{Flotantes} = (3*0,25) \rightarrow (2*0,25)$ 

---

**A) Peor caso**

$CPI_{Condicional} = (4*0,1)$

$CPI_{original} = (4*0,3) + (0,3*0,3*1) + (4*0,1) + (3*0,35) + (3*0,25) = 3,49$

$CPI_{nuevo} = (1*0,3) + (4*0,1) + (1*0,35) + (2*0,25) = 1.55$

$a_{cc} = \frac{CPI_{original}}{CPI_{nuevo}} = \frac{3,49}{1.55} = 2.25..$

---

**B) Mejor caso**

$CPI_{Condicional} = (3*0,1)$
$CPI_{CondicionalNuevo} = (3*0,1)  \rightarrow (1*0,1)$  

$CPI_{original} = (4*0,3) + (0,3*0,3*1) + (3*0,1) + (3*0,35) + (3*0,25) = 3,39$

$CPI_{nuevo} = (1*0,3) + (1*0,1) + (1*0,35) + (2*0,25) = 1.25$

$a_{cc} = \frac{CPI_{original}}{CPI_{nuevo}} = \frac{3,39}{1.25} = 2.712$