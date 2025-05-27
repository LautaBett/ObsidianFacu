Jerarquia de datos
tamaño de arreglo puede ser tamaño d bloque, mientras mas abajo este el fallo, aumentarn los ciclos de reloj, si cache l1 tiene un fallo y tiene q ir a chache l2 , el procesador espera, si el procesador tiene q estar esperando un prgrama , la cpu es interrempida miebtras se soporta este fallo, y se sigue con otro programa, si conectamos un acble interrumpcion al cou m nbuestera cpu deende del exteriror, 
jerarquia en dos niveles y tres compoentes,  usuario,ram,disco o nivel superiro q es mas rapdio y no entra todo, un nivel inferiror que entra todo pero ed mal lento , y el usuario, en la memorai tenesmos espacio para bloque, puede estar lleno o no, se indica con un bit, 0 para mugre, 1 para bloque, mugre porque en su vacio vacio no esta nunca, espacio para bloque se puede llamar como frame,
ademas, tiene otro bit q indica si el bloque esta modificado o no, para ver si tiene discrepancia con la ram, yo indico los bloques con modulo 4 osea todos lo de resto 3, ej bloque 3, 7, 11,15,etc, para saber a q bloque de modulo 4 se refiere hay un bit q te lo indica, .si mi cache tiene la misma cantidad de bloques que mi ram no hay necesidad de indentificar, pero eso no se puede dar, nuestra ram tiene 128 bloques de 8 palabras cada una, 
	ejemplo           ram de 0  a 1023   
				blq = 296 div 8 = 37
				ofs = 296 mod 8 = 0
				de la ram arranca en la 296 hasta 37 lugares mas adelante, pero es la primera palabra
				cache de 0  a 15
				linea = 37 mod 16 = 5
				tag = 37 div 16 = 2
				del cache  toma la 5 y  le pone el tag 2

duda diferencia entre asosiatica de directa, 
otri ejemlo si chaceh es de 512 b que es 2 a la 9 bytes, yel bloque 16 bytes que es 2 a la 4, si divido 2 a la 9 sobre 2 a la 4, da 2 a la 5 q es 32 que es la cantidad de bloques,
0d0a es pasar de linea, 
chache 4a significa 4 espacios para bloques asosiativos,
el tiempo de la estrategia de optimiaxcin early restart on miss, es la mitad de lo normal

