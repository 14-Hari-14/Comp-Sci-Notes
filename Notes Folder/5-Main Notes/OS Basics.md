
2024-08-28 14:43

Tags:

# OS Basics

Operating System: Its an interface between the hardware components and the software applications.

Different Examples of Operating System:
- Windows 
- Linux Distros
- Mac 
- Android 
- IOS
- RTOS

Difference between Program, Process, Threads

**Program** is a set of instructions written in a programming language that performs specific tasks or set of tasks. Its stored on the disk and can be seen as an executable entity 

**Process** is a specific instance of the program in  execution. When a program is loaded and executed in the memory its called a process. A process is an independent entity with its own memory space, execution context and resources.
- A process also has **PCB(Process control block)** this contains all the data regarding a process 
- Communication between process happens through **IPC(Inter Process Communication)**

### Process Communication

Refers to methods or mechanism by which process are executing instances of programs, exchange data and coordinate their activities

**Methods of Process Communication:**
	- IPC(Inter Processing Communication)
		- **Pipes:** Unidirectional communication channel between 2 processes where 1 writes to the pipes & other reads
		- Named Pipes: 
		- Message Queues
		- **Shared Memory**
		- Sockets
	- Signals 
	- File Systems
	- Shared Resources

**Definition:** The current activity of the process is called the state of the process
As the process executes there might occur changes in the state of the process 

### States of the process
1. **New:** The process has just been created
2. **Running:** Instructions are currently being executed
3. **Waiting:** The process is waiting for some event to occur
4. **Ready:** The process is waiting to be assigned to CPU
5. **Terminated:** The process has finished execution
![[ProcessState.png]]

Each process is represented by a process / task controlling block (**PCB**). It contains info about the state of the process and the contents of the PC(address of the next instruction to be executed)
It stores this data using registers
It also the saves the state of the process if it has been **swapped**.

# References
---


