Un procesador *A* implementa las instrucciones de salto condicional para comparar 2 registros y realizar el salto por igualdad (BEQ), desigualdad (BNE), mayoría (BGT) o minoría (BST). Estadísticamente, las cargas de programa que se ejecutan en ese procesador tienen un *15% de instrucciones de salto condicional, de las cuales las de comparación por igualdad o desigualdad son un **60% del total de saltos*.

Se rediseña el procesador en una versión *B, en la que se sustituyen los saltos **BEQ y BNE* por las versiones *BEQZ y BNEZ* que realizan el salto según un flag de zero que genera el procesador si la operación de resta previa al salto da 0. También se diseña una variante del compilador que, para cada salto *BEQ y BNE* genera, ahora, una secuencia *SUB, BEQZ o SUB, BNEZ, según corresponda. En estas condiciones, el **CPI de salto para las nuevas instrucciones se reduce a la mitad* ya que no deben realizar la resta en esas operaciones, pero el tiempo de ciclo de reloj se incrementa un *7%* debido a la reorganización interna de la arquitectura.

Sabiendo que estadísticamente el porcentaje de instrucciones empleadas para un programa dado y sus CPI respectivos son:

|Instr.|Load/Store|Saltos|Aritmética de enteros|Pto Flotante|
|---|---|---|---|---|
|Porcentaje|25%|15%|35%|25%|
|CPI|2|3|1|4|

¿Mejora el procesador B realmente al procesador A? ¿Por cuánto?
(Suponga un programa original para A de 1000 instrucciones)

BEQ y BEN => son el 60% de los saltos
BEQ y BEN => BEQZ y BENZ => (SUB, BEQZ) o (SUB, BENZ) => CPI/2

original
$RI_{original}=1000$

$CPI_{original} = (2*0,25) + (3*0,15) + (1*0,35) + (4*0,25) = 2.3$  

nuevo
$RI_{nuevo} = 1000 + (1000*0,15*0,6) = 1090$
$Load/Store = (1000*0,25)/1090 = 0,229 = 23$%
$Saltos = (1000*0,15)/1090 = 0,137 = 13,7$%
$Enteros = ((1000*0,35)+90)/1090 = 0,403 = 40,3$%
$Flotantes = (1000*0,25)/1090 = 0,321 = 23$%

$CPI_{salto-nuevo} = 3 - (3*0,6)/2 = 2,1$

$CPI_{nuevo} = (2*0,23) + (2,1*0,137) + (1*0,403) + (4*0,23) = 2,07$

$T_{a} = 1000*2,3 = 2300$
$T_{b} = 1090*2,07*1,07 = 2414,241$

$a_{cc} = \frac{2414,241}{2300} = 1,04967$

RTA:  B es un 4,9% mas lento que A