**Resumen de los Componentes VHDL:**

1. **`ProcessorTB` (Testbench):**
    
    - Configura el entorno de simulación.
    - Instancia la unidad principal a probar: `Processor`.
    - Instancia **dos** memorias (`Memory`):
        - `Instruction_Mem`: Para instrucciones, carga el archivo `"program1"`, tamaño 1024 bytes, opera en **flanco descendente** (`C_FUNC_CLK = '0'`).
        - `Data_Mem`: Para datos, carga el archivo `"data"`, tamaño 1024 bytes, opera en **flanco ascendente** (`C_FUNC_CLK = '1'`).
    - Genera una señal de reloj (`Clk`) con período de 50 ns.
    - Genera una señal de reset (`Reset`) activa durante 120 ns al inicio.
    - Conecta el `Processor` a las memorias y señales de control.
2. **`data` (Archivo):**
    
    - Contiene los datos iniciales (en hexadecimal) para la `Data_Mem`.
3. **`program1` (Archivo):**
    
    - Contiene las instrucciones MIPS (en hexadecimal) que se cargarán en la `Instruction_Mem`.
4. **`program2` (Archivo):**
    
    - Otro conjunto de instrucciones MIPS (en hexadecimal). Para usarlo, necesitarías cambiar `C_ELF_FILENAME` en la instancia `Instruction_Mem` del testbench a `"program2"`.
5. **`NOMBRE` (Entidad ALU):**
    
    - Realiza operaciones aritméticas y lógicas (AND, OR, ADD, SUB, SLT, LUI-like) sobre operandos de 32 bits (`a`, `b`) según una señal `control` de 3 bits.
    - Genera un resultado (`result`) de 32 bits y una bandera `zero`.
    - Usa `std_logic_unsigned` para la aritmética.
6. **`Memory` (Entidad Memoria):**
    
    - Modelo de memoria genérico (RAM).
    - Configurable en tamaño (`C_MEM_SIZE`), archivo de inicialización (`C_ELF_FILENAME` - lee hexadecimal de texto), y flanco de reloj activo (`C_FUNC_CLK`).
    - Almacena por bytes pero accede por palabras de 32 bits.
    - Realiza lecturas (`RdStb`) y escrituras (`WrStb`) síncronas.
7. **`Processor` (Entidad Procesador):**
    
    - Implementa un **procesador MIPS de ciclo único**.
    - Tiene interfaces separadas para memoria de instrucciones (`I_*`) y datos (`D_*`) (Arquitectura Harvard).
    - Instancia los componentes `ALU` y `Registers`.
    - Contiene:
        - Unidad de Control (`E_UC`): Decodifica opcodes (R-type, lw, sw, beq, j) y genera señales de control.
        - Control de ALU (`E_CtlALU`): Genera la señal `ALU_control` específica basada en `ALUOp` y `funct code`.
        - Datapath: Muxes para seleccionar operandos de ALU (`ALUSrc`), registro destino (`RegDst`), dato a escribir en registro (`MemtoReg`). Extensión de signo.
        - Lógica de PC: Cálculo de PC+4, dirección de branch (`pc_branch`), dirección de jump (`pc_jump`), y selección de siguiente PC (`next_reg_pc`). Actualización síncrona del PC (`E_PC`) en flanco ascendente.
        - Interfaz con memorias: Controla `RdStb`/`WrStb` y direcciones (`I_Addr`, `D_Addr`).
8. **`registers` (Entidad Banco de Registros):**
    
    - Banco de 32 registros de 32 bits.
    - Dos puertos de lectura combinacionales (`data1_rd`, `data2_rd`).
    - Un puerto de escritura síncrono (`data_wr`) en **flanco descendente** (`falling_edge(clk)`).
    - Reset asíncrono (`rst` - ¡Ojo! el puerto se llama `reset`).
    - Registro 0 (`"00000"`) está cableado a cero (no se puede escribir, siempre se lee cero).