
2024-10-20 23:19

Tags:

# Addressing Modes 8051

Instruction format 

Instruction: Is any task that needs to be performed by the microcontroller 

Two parts of instruction are:
1. Opcode
2. Operand

MOV A, R0
MOV - Opcode
A, R0 - Operand

The method of specifying the data to be operated by the instruction is called addressing
So addressing modes are the ways in which it access memory or registers  to retrieve  or store data

3 types of data operands
### 1. **8-bit Operands**:

- Most instructions work with **8-bit data** because the 8051 is an 8-bit microcontroller. For example:

**Examples**: 
**Registers** (like `A`, `R0-R7`, `B`, etc.) are 8-bit.
MOV A, #55H  ; Move the 8-bit immediate value 55H into A
ADD A, R0    ; Add the 8-bit value in R0 to A

### 2. **16-bit Operands**:

- Certain instructions work with **16-bit operands**, especially when dealing with memory addresses or larger values like the **DPTR (Data Pointer)** and the **PC (Program Counter)**.

**Examples**:
MOV DPTR, #1234H  ; Move the 16-bit immediate value 1234H into the DPTR


### 3. **1-bit Operands**:

- Some instructions operate on **single bits**, especially when dealing with flags like the **carry flag (C)** or **bit-addressable memory**.

**Examples**:
SETB C   ; Set the carry flag (1-bit operand)
CLR P1.0 ; Clear the bit 0 of Port 1 (1-bit operand)


## 7 types of Addressing modes
1. Immediate Addressing 
2. Register Addressing 
3. Direct Addressing 
4. Indirect Addressing 
5. Index Addressing
6. Bit Addressing 
7. Absolute Addressing


### Immediate Addressing
Directly specify a constant or immediate value as the operand for an instruction
Example: MOV A, #25H

### Register Addressing
Registers commonly used in 8051 are
A, B, R0-R7
A- accumulator
B- multiplication / division
R0-R7 -  general purpose register

Example: MOV A, R0


### Direct Addressing Mode
Direct Addressing mode allows accessing data from internal RAM of the microcontroller 
Specifies the memory location directly allowing efficient access

Example: 
MOV A, 30H
MOV 30H, A


Point out the difference between immediate (uses #) and direct addressing modes

### Indirect/ Register Indirect Addressing Mode
Indirect Addressing Mode enables accessing memory locations indirectly through a register pair

8051 microcontroller supports 2 register pairs 
- DPTR
- R0 and R1


Its used for performing table look ups or accessing large data arrays
Example:
MOV A, @R0
@ is used to indicate that R0 stores another address which contains the actual data required

R0--->30H ---> 05H ---> A
- MOV DPTR, #8000H   ; Load 16-bit external memory address into DPTR
- MOVX A, @DPTR      ; Move data from external memory (pointed by DPTR) into A
- this is absolute addressing mod


### Indexed/Relative Addressing Mode
It allows accessing memory locations by adding an offset to the base address 

Example: 
MOVC A, @A+PC

Address in A + Address in PC = Address of the required item 
Now since there is an @ present. We retrieve the data from the address and store that in A. 


### Bit Addressing Mode
Used to access the bits inside the SPECIAL FUNCTION REGISTER ( **SFR** ) of the 8051 microcontroller. 

Example 
1. SETB P1.2 
	- SETB is used to set whatever port to 1 
	- P1 is port 1 (it has 8 bits from P1.0 to P1.7) 
	- So in this example we are setting the 2nd bit of port 1 to 1 
2. CLR P1.0 
	- Clears the 0th bit of port 1 
3. CPL C
	- C is the carry flag and in this instruction we are inverting the value in the carry flag



### Absolute Addressing Mode 
Is a specialised mode for used for accessing the external memory directly. Requires 16bit addressing mode so uses DPTR
Example: 
MOVX A, @DPTR


**PC**
- The 8051 has internal ROM (often called **Program Memory**) where the program code is stored. This internal ROM is typically accessed using the **Program Counter (PC)**, not the DPTR.

**DPTR**
- The **DPTR** is a 16-bit register used to access **external memory**. It can be used to address external data memory or external program memory if the microcontroller is configured to use external ROM or RAM.
- The **MOVX** instruction, for instance, uses the DPTR to move data between the accumulator and external memory. **MOVX** transfers data between accumulator and external memory. The X stands for extended to show its used specifically for external memory transfer

- MOV DPTR, #8000H   ; Load 16-bit external memory address into DPTR
- MOVX A, @DPTR      ; Move data from external memory (pointed by DPTR) into A
- this is absolute addressing mode. 


# References
---


	