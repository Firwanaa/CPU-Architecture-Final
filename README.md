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
![](Pasted%20image%2020230814000847.png)
### Summery for the 7 steps by ChatGpt :
- 1- User process calls a library function.
- 2- Library function prepares system call parameters.
- 3- Trap instruction switches mode to kernel, yielding control to the OS.
- 4- OS identifies the system call based on the provided call number.
- 5- Kernel accesses a dispatch table with service routine pointers using the call number.
- 6- Service routine executes, control returns, and mode switches back to user.
- 7- Library function interprets results, returns to user process.

 - Week 8- Slide (36)
### Levels of Computer Architecture 
- Level 6: User - Executable programs 
- Level 5: High-Level Programming - C++, Java, FORTRAN, etc. 
- Level 4: Assembly Language - Assembly code 
- Level 3: System Software - Operating system, library code 
- Level 2: Machine - Instruction Set Architecture 
- Level 1: Control - Microcode or Hardwired 
- Level 0: Digital Logic - Circuits, gates, etc.

### Programming Models

- The **programming model** is determined by how the processor architecture manages internal (CPU registers) and external (RAM) memory during program execution.
- It defines how instructions access operands and how instructions are described in the processor's assembly language.

### Programming Models: Stack-Based and GPR Architectures

There are two primary programming models:

1. **Stack-Based Architectures:**
   - Internal CPU register set is hidden from the program.
   - Instructions read operands from and write results to a stack in memory (LIFO data structure).
   - Basic operations include PUSH and POP.

   ### Stack Operations:
   - **PUSH:** Adds an argument to the top of the stack.
   - **POP:** Removes the top value from the stack and returns it to the CPU.

   ### Stack Implementation:
   - Operates as a last-in-first-out (LIFO) data structure.
   - Values are added to the top of the stack.
   - Data can only be removed from the top of the stack.
   - Implemented using memory buffers.
   - May lead to stack overflow error if data exceeds allocated space.

### Advantages of Stack-Based Architectures

- Instructions require fewer bits to encode.
- Register management is automatic.
- Instruction set remains unchanged.

   **Example: Compute 3*7+2**
```assembly
   PUSH 2
   PUSH 7
   PUSH 3
   MUL
   ADD
```

```
After PUSH 2:
-----
|  2  |
-----
After PUSH 7:
-----
|  7  |
-----
|  2  |
-----
After PUSH 3:
-----
|  3  |
-----
|  7  |
-----
|  2  |
-----
After MUL:
-----
| 21  |
-----
|  2  |
-----
After ADD:
-----
| 23  |
-----

```

2. **General-Purpose Register (GPR) Architectures:**
   - Instructions access operands from and write results to a random-access register set in the CPU.
   - Operands and results are specified by referencing register addresses.

### Advantages of GPR Architectures

- GPR compilers provide better performance.

## ISA and CPU Design Styles

### Different ISA for Different CPUs

- Different CPUs implement distinct sets of instructions.
- Examples include ARM, Intel x86, IBM/Motorola PowerPC (Macintosh), MIPS, and Intel IA32.

### Two CPU Design Styles

1. **RISC (Reduced Instruction Set Computing):**
   - Involves a small set of highly optimized instructions.
   - Instructions typically perform simple tasks.
   - Focuses on executing instructions quickly.

2. **CISC (Complex Instruction Set Computing):**
   - Features a larger, more complex set of instructions.
   - Some instructions can perform complex tasks directly.
   - Emphasizes code compactness.

### Historical Comparison: RISC vs. CISC

### Complex Instruction Set Computing (CISC)
- Examples: x86 architecture.
- Larger instruction set with intricate instructions built into hardware.
- Variable length instructions.
- Multiple clock cycles per instruction.

### Reduced Instruction Set Computing (RISC)
- Examples: ARM architecture.
- Smaller, highly optimized set of instructions.
- Specific memory access instructions.
- One instruction executed per clock cycle.
- Instructions are of the same size and fixed.

### Example: A = A * B

### RISC

```assembly
LOAD A, eax
LOAD B, ebx
PROD eax, ebx
STORE ebx, A
```
1. **LOAD A, eax**
   - Load the value of A into register eax.

2. **LOAD B, ebx**
   - Load the value of B into register ebx.

3. **PROD eax, ebx**
   - Multiply the values in registers eax and ebx.

4. **STORE ebx, A**
   - Store the result from register ebx into variable A.

### CISC
```assebly
MULT B, A
```
1. **MULT B, A**
   - Multiply the values of A and B to generate the result.

- All models week 8 - slide (56)
	- **Sequential Model**: The program counter (PC) defines total order on dynamic instruction 
	- **Memory Only**: ***Slides are screenshots***
		> Slide(55) where (other than memory) can operands come from? and how are they specified? **No Clue!!!*
		> Example A = B + C
		> Several options 
		- memory only:
```
Add B, C, A                  mem[A] = mem[B] + mem[C]
```

- **Accumulator**: Implicit single element storage
```
load B                       ACC = mem[B]
add  C                       ACC = ACC + mem[C]
storage A                    mem[A] = ACC
```

- **Stack** : TOC implicit in instructions
```
push B                        stk[TOS++] = mem[B]
push C                        stk[TOS++] = mem[C]
add                           stk[TOS++] = stk[--TOS] + stk[--TOS]
pop A                         mem[A]     = stk[--TOS] 
```

- **General-purpose register**: multiple explicit accumulator
```
load  B, R1               R1 = mem[B]
add   C, R1               R1 = R1 + mem[C]
store R1, A               mem[A] = R1
```

- **Load-store**: GPR and only load/stores access memory
```
load  B, R1               R1 = mem[B]
add   C, R1               R1 = R1 + mem[C]
add   R1, R2, R1          R1 = R1 + R2
store R1, A               mem[A] = R1
```

## Operands Models Pros and Cons:
### Metric  I: Static code size
- Number of instructions needed to represent program, size of each
- Wants many implicit operands
- **Rank Good -> Bad**: memory, accumulator, stack, load-store
###  Metric  II: Data memory traffic
- Number of bytes move to and from memory
- Wants as many long-lived operands in on-chip storage
- **Rank Good -> Bad**: load-store, stack, accumulator, memory
### Metric  II: Cycles per instructions 
- Want short (1 cycle), little variability, few nearby dependences
- **Rank Good -> Bad**: load-store, stack, accumulator, memory

**Upshot**: most new ISAs are load-store or hybrids.  