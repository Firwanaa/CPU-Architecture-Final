# CPU Architecture Final
# Week 8
## He was flying, this what i was able to write down.

### CPU: Three sub-units:
	- Control Unit
	- Memeroy Unit
	- Aritmitic Logical Unit 
		  - Arithmitic operations: + , -, *, /
		  - Logical: >, < , <=, <=, !=

### MCQ: Cash memory and RAM
	- Ram is the Primary storage. Volatile storage, temporary storage. 

-Written: Define Voltile Memory
- ROM, Permenanent Storage, BIOS

- Firmware
- Freeware
- sharewareT

- System Bus:
  - MCQ
  - Written

- Define software: Computer prgrams that are when executed provides desired function and performance
                   , data structures that manipulate information and documents that describe the operation
                    and use the program. 

- System software:
  - OS
  - Utility
    - Compiler: Converts the Whole program from high-level language into assebly language
    - Interpreter: Converts and excute high-level program one line at a time (line by line)
    - Assembler

- System software -> System request
- Application -> user request

- CPU only process information in RAM 
- 1945 - 1955 no operating system, no translation programs needed because we were using machine language
  to write programs 

- Monoprogramming: loads ONE instruction to CPU, have to SWAP each time need to process new instruction
- Multiprogramming: can have many processes at a time, CPU can SWITCH to a different instructions. 

- Batch processing: Group of similar jobs

- Network operating system
  - share of data
  - share of resources 

- Distributed: Divide work between multiple processes

----------------------------------------------------------

- User mode: no IO operations allowed
- Kernal mode: (privileged, OS mode, Supervised)
  - IO operations
  - File operations 
  - Memory operations
- System call: user ask OS to switch from user mode to kernal mode (TRAP instruction)

- Types of System calls:
  - Process control
  - File management
  - Device management
  - Inforamtion maintenance
  - Communications

- Semantics of System call execution:
  1- The user process calls a library function
  2- The library function sets system call parameters (including arguments, return, address, and call number) 
     in designated location like register or stack
  3- A trap instruction shifts the mode form user mode to kernal mode, transfaring control to the OS.
  4- The OS identifies the system call by examining the call number parameter received from the library function
  5- Using the call number, the kernal access a dispatch table containing pointers to service routines for various system calls.
  6- The relevant service routine executes, control returns to the user program after the trap instructions, and the mode swtiches back to user from system. 
  7- The library function processes the instruction after the trap, interprets kernal return value, and return to the user process.

- Summery for the 7 steps by ChatGpt:
 1- User process calls a library function.
 2- Library function prepares system call parameters.
 3- Trap instruction switches mode to kernel, yielding control to the OS.
 4- OS identifies the system call based on the provided call number.
 5- Kernel accesses a table with service routine pointers using the call number.
 6- Service routine executes, control returns, and mode switches back to user.
 7- Library function interprets results, returns to user process.

 - Week 8- Slide (36)

 - Stack-based operations
  - LIFO ?
  - Push and POP ?
-> example ?

- RISC and CISC <- MCQ

- Example week 8 slide (49)
- All models week 8 - slide (56)



