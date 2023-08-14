# CPU Architecture Final - Part 2 - Sheridan College - SYST27198
# Week 8
> #### He was flying, this what i was able to write down.

### CPU: Three sub-units:
- Control Unit
- Memory Unit
- Arithmetic Logical Unit 
	  - Arithmetic operations: + , -, *, /
	  - Logical: >, < , <=, <=, !=

### MCQ: Cash memory, ROM and RAM
- RAM is the Primary storage. Volatile storage, temporary storage. 
- ROM: Read-only memory, permanent, BIOS. 
- Cache memory <- I have nothing so far.
 
### Define Volatile Memory <- nothing in week 8:
But it's a type of memory that maintain its data only while it's powered. If power is interrupted the data is lost. 

### He mentioned this during the review for the first time. No clue what is the context. Have fun.. 
- Firmware
- Freeware
- shareware
### ChatGPTeed it:
- **Firmware**: Firmware refers to software that is permanently programmed into a hardware device. It provides low-level control over the hardware and is typically not easily changeable by the end user.
    
- **Freeware**: Freeware refers to software that is available for use at no cost. Users can download and use freeware without having to pay a license fee.
    
- **Shareware**: Shareware is software that is distributed with the intention that users can try it before purchasing a license. Users often get a trial period or limited functionality for free, and if they decide to continue using the software with full features, they are usually required to purchase a license.
    

These terms describe different ways in which software is distributed and accessed by users.
## System Bus:
	MCQ
	Written
Control bus: control and coordinating activities of the two other buses.  
    - Address bus: Carry memory address
    - Data bus: Carry data 

#### Define software: Computer programs that are when executed provides desired function and performance data structures that manipulate information and documents that describe the operation and use the program. 

#### System software:
- OS
- Utility
	- Compiler: Converts the Whole program from high-level language into assembly language
	- Interpreter: Converts and execute high-level program one line at a time (line by line)
	- Assembler

- System software -> System request
- Application -> user request

- CPU only process information in RAM, means It doesn't read from hard-drive or any secondary storage.(u know read/write speed and some other stuff). 
- 1945 - 1955 no operating system, no translation programs needed because we were using machine language to write programs.
- No Utility software: Because we were programming in machine language babe, compilers for noobs.  

- Monogramming: loads ONE instruction to CPU, have to SWAP each time need to process new instruction
- Multiprogramming: can have many processes at a time, CPU can SWITCH to a different instructions. 

- Batch processing: Group of similar jobs

- Network operating system
  - share of data
  - share of resources 

- Distributed: Divide work between multiple processes

- User mode: no IO operations allowed
- Kernel mode: (privileged, OS mode, Supervised)
  - IO operations
  - File operations 
  - Memory operations
- System call: user ask OS to switch from user mode to kernal mode (TRAP instruction)

- Types of System calls:
  - Process control
  - File management
  - Device management
  - Information maintenance
  - Communications

#### Semantics of System call execution: 100% in the final 
- 1- The user process calls a **library function**
- 2- The library function sets **system call parameters** (including arguments, return, address, and call number) in designated location like register or stack
- 3- A **trap instruction shifts** the mode form user mode to kernel mode, transferring control to the OS.
- 4- The OS identifies the system call by examining the **call number** parameter received from the library function
- 5- Using the call number, the kernel access a **dispatch table** containing pointers to service routines for various system calls.
- 6- The relevant **service routine executes**, control returns to the user program after the trap instructions, and the mode switches back to user from system. 
- 7- The library function processes the instruction after the trap, interprets kernel return value, and **return to the user** process.

### Summery for the 7 steps by ChatGpt:
- 1- User process calls a library function.
- 2- Library function prepares system call parameters.
- 3- Trap instruction switches mode to kernel, yielding control to the OS.
- 4- OS identifies the system call based on the provided call number.
- 5- Kernel accesses a dispatch table with service routine pointers using the call number.
- 6- Service routine executes, control returns, and mode switches back to user.
- 7- Library function interprets results, returns to user process.

 - Week 8- Slide (36)
## Levels of Computer Architecture 
- Level 6: User - Executable programs 
- Level 5: High-Level Programming - C++, Java, FORTRAN, etc. 
- Level 4: Assembly Language - Assembly code 
- Level 3: System Software - Operating system, library code 
- Level 2: Machine - Instruction Set Architecture 
- Level 1: Control - Microcode or Hardwired 
- Level 0: Digital Logic - Circuits, gates, etc.


## Programming model
- Determined by how processor, architecture deals with internal (CPU registers) and external RAM memory management during program execution.
- Defines how instructions access their operands and how instructions are described in the processor's assembly language./


 - Stack-based operations
  - LIFO ?
  - Push and POP ?
-> example ?

- RISC and CISC <- MCQ

- Example week 8 slide (49)
- All models week 8 - slide (56)



