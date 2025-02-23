
2024-08-28 14:39


Status: 

Tags: #ss #types_of_ss

# SS_MOD_1

Basic Terminologies and components that make up the low level part of the computers

Software is divided into 2 categories 
- Application Software 
- System Software

**Application software** is software created by users to perform various tasks that are required by them . Examples:  MS Word, Excel ,etc

**System Software** is software required by the computer to properly function. This is the software that acts as backbone of helping a computer function without user intervention. All the process happens automatically and the user can focus on their tasks.

## Different Types of System Software
- OS 
- Device Drivers
- Text Editors 
- Macro Processors 
- Language Translators
	- Assembler 
	- Compiler
	- Interpreter
	- Loader
	- Linker 
	- Debugger


### OS
Refer to this: [[Basic Functionality of OS]]

### Device Drivers
Its the glue between the OS and the I/O devices. It acts as a translator between OS and the devices by converting the generic instructions from the operating systems to device specific instructions that can be executed

### Text Editor
Allows users to create and device documents based on the output received we can classify text editors into 4 types:
- Line Editor (used in msdos)
- Stream Editor
- Screen Editor
- Word processor (visual studio )

### Macro Processors
Macro Processors are programs that copy streams of text from one place to another making a systematic set of replacement.

Basically what it does is it substitutes a predefined sequence of code called macros with a more extensive set of instructions during compilation or assembly of the program

### Language Translators 
Computers can only understand primitive instructions and therefore all the code written in high or low level languages need to be translated to machine code. 
- Assembler
- Compiler
- Interpreter

#### Assembler

SOURCE PROGRAM --> ASSEMBLER --> MACHINE CODE

The job of the assembler is to convert source program in assembly language to machine code which the computer can understand

There are 2 classifications to an assembler
- Self Assembler (runs on the computer itself and generates machine code for it)
- Cross Assembler (runs on another system and generates machine code for a computer)

### Compiler:

- **Translation**: A compiler translates the entire source code of a program into machine code or an intermediate code (like bytecode) in one go.
- **Execution**: After compilation, the generated machine code is executed. This means the translation and execution are separate phases.
- **Speed**: Compiled programs generally run faster because the entire code is translated before execution.
- **Error Detection**: A compiler checks for errors during the entire compilation process and reports them all at once. This means you must fix all syntax errors before running the program.
- **Output**: The output of a compiler is an executable file, which can be run independently of the original source code.
- **Example**: C, C++, and Rust are languages typically compiled.

### Interpreter:

- **Translation**: An interpreter translates source code line-by-line or statement-by-statement into machine code, executing each line as it goes.
- **Execution**: The translation and execution happen simultaneously. The code is interpreted on the fly.
- **Speed**: Interpreted programs usually run slower than compiled programs because the translation occurs during execution.
- **Error Detection**: Errors are detected and reported line-by-line as the code runs. This allows for immediate feedback but can interrupt program execution as soon as an error is encountered.
- **Output**: No separate executable is produced; the source code is needed each time to run the program.
- **Example**: Python, JavaScript, and Ruby are languages typically interpreted.


# References
---

[]
