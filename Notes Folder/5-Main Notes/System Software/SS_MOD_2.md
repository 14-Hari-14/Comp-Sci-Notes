

2024-10-26 13:26

Tags:

# SS_MOD_2


![[Pasted image 20241027132635.png]]


There are 2 types of assemblers:
1. **1 pass** scans the complete code in 1 pass 
2. **Multi pass** takes multiple passes to create object code



## Basic Assembler Functions

- convert **symbolic operands** to equivalent **machine address** ex (**RETADR**  to 1033)
- convert **mnemonic operation codes** to equivalent **machine language** ex (**STL**  to 14)
- Convert the **data constants** in the file to **internal machine representations** ex(**EOF** TO 454F46)

### Assembler Directive
An assembler directive is a set of instructions provided to the assembler to perform certain actions during the assembly of the program.
It doesn't indicate the amount of memory to be used or where to store the data. It provides info crucial to the functioning of the assembler
Ex: **START, END BYTE , WORD, RESW, RESB**

#### START
Specify the name and the location of the starting address of the program

Ex: COPY        START        2000 (copy is the name and 2000 is the address)

#### END
Specify the termination point of the program and optionally specify the first executable instruction of the program

Ex:             END          FIRST


#### 4 Methods of Storing Data
1. BYTE
2. WORD
3. RESB
4. RESW


**BYTE:**
Generate char or hexadecimal constant of occupying as many bytes as needed to represent data

Ex: CHARZ         BYTE            C'Z'


**WORD:**
Generate one word integer constant

Ex: FIVE WORD 5


**RESB:** 
Reserve the indicated amount of bytes for a data area

Ex: C1            RESB          1

**RESW:**
Reserves the indicated amount of words for a data area

Ex:  C1            RESW              1



## Forward Reference 
In assemblers a forward reference occurs when an instruction is trying to refer to a label which hasn't been defined yet

```asm
   JMP NEXT   ; Forward reference to label 'NEXT'
   MOV AX, 1
NEXT:
   MOV BX, 2
```

In the instruction JMP NEXT, the assembler doesnt know where next is defined yet so this is an example of forward reference

To handle Forward Reference the assemblers use a **2 PASS METHOD**

**First Pass(Define Symbols):** 
- Assign address to all statements
- saves the value(address) assigned to all labels for use in pass 2
- Performs some processing of assembler directives( includes calculating the area required by statements like RESW and RESB)

**Second Pass(Assemble instructions and generate object code):** 
- Assemble instructions(translating opcodes and looking up addresses)
- generate data values defined by BYTE AND WORD
- Perform processing of assembler directives not done in pass 1
- write the object code and **assembly listing(optional)**


![[flow-diagram-assembler.png]]

![[2pass-assember-process.png]]

## Assembler Output Format
The assembler will write the generated object code into some output device. From there it will be loaded into memory for execution

The simple output format uses **3 HEADERS**
1. **Header Record**: Contains program name, starting address and length
2. **Text Record** : contains machine code(instructions and data of the program) together with an address for where they are to be loaded
3. **End Record**: marks the end of the object code and specifies the address of the program where the execution begins

![[Assembler-Output-Format.png]]

![[pass1and2.png]]

Here the red line shows the working of pass 1 and the blue line shows the working of pass 2
At line 10 we reference RETADR of which we don't know the location of. By the end of pass 1 we are able to provide it with a memory address. Which is then used as input for pass 2

Here’s a quick summary of inputs and outputs for each pass in a two-pass assembler:

### Pass 1
- **Inputs**: Source code with instructions and labels + **OPTAB**.
- **Outputs**:
  - **Symbol Table**: Stores addresses of all labels and symbols.  -->**(DATA STRUCTURE)**
  - **Intermediate Code**: Partial code with placeholders for unresolved addresses (forward references).
  - **Location Counter**: Updated addresses for each line of code.


#### OPTAB
OPTAB is used to look up mnemonic operation codes and translate them to machine language equivalents. 
- Contains at least the machine language equivalents of opcodes 
- Could also contain the information about instruction format and length

In SIC/XE its used to increment the LOCCTR with the instruction length
Its arranged like a hash table with opcode as key and machine equivalent as value. 
Its a static table

#### SYMTAB
Its used to store the values(addresses) assigned to the labels.
Contains the name and value for each label in the source program with flags to indicate error conditions
Implemented like a hash table 

#### LOCCTR
Location Counter(LOCCTR) is a variable used to help the assignment of the addresses its initialised to the address given at START. The length of the instruction is added to LOCCTR to get the address of the next instruction
### Pass 2
- **Inputs**: Intermediate code and symbol table from Pass 1.
- **Outputs**:
  - **Machine Code**: Final assembled code with all addresses resolved.
  - **Listing File** (optional): Detailed report showing source code with corresponding machine code and addresses.


**For Example**

```asm
START 1000
FIRST  LDA   ALPHA
       ADD   BETA
       STA   GAMMA
ALPHA  RESW  1
BETA   WORD  5
GAMMA  RESW  1
       END   FIRST
```

**Sample Output** 
This is the header record with name, starting address and length of the program
**H ^ PROGRAM ^ 001000 ^ 00100A**

001000 --> Starting  address, 00100A --> Length of the program

This is the text record with the starting address for this segment 
**T ^ 001000 ^ 0006 ^00 ^ 140033 ^ 280036^ 0C0039**

001000 --> Starting address of this segment
0006 --> Length of segment in bytes(In this ex its 6)
00 --> OPCODE for LDA
140033 --> OPCODE For ADD BETA
280036 --> OPCODE For STA GAMMA
0C0039 --> Assumed OPCODE for instruction if any

This is the end record with the address of the first executable instruction
**E^001000**


### Assembler Algorithm

The source code and the OPTAB are provided as input for the first pass

![[Input-demo-assembler.png]]

![[OPTAB-demo-assembler.png]]


In the first pass we read through the source code(input.txt) and create an intermediate file with the location of each instruction. The symtab is also made for faster and efficient retrieval

![[Intermediate-demo-assembler.png]]

![[SYMTAB-demo-assembler.png]]


Join the OPCODE and the location of the operand to get the object code 

![[ObjectCode-demo-assembler.png]]


### Algorithms for 2 pass assembler

#### Pass 1:
![[pass 1 algo assembler.png]]

#### Pass 2:
![[pass 2 algo assembler.png]]


Main difference between SIC & SIC/XE is 
- use register-register instructions whenever possible 
- syntax difference like (COMPR ZERO is changed to COMP A, S & TIX MAXLEN is changed to TIXR T)
- Register-register instructions are faster than register-memory


## Hand Assembly Of SIC/XE 

### Addressing Modes
 - Immediate 
 - Indirect
 - PC relative or Base Relative
 - Indexed addressing 
 - Register to Register instructions
 - 

# References
---


	