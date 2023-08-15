# CPU Architecture Final - Part 2 - Sheridan College - SYST27198
# Week 8
> #### He was flying, this what i was able to write down.

### CPU: Three sub-units:
- Control Unit
- Memory Unit
- Arithmetic Logical Unit 
	  - Arithmetic operations: + , -, *, /
	  - Logical: >, < , <=, <=, !=

--------------------------------------------------
### MCQ: Cash memory, ROM and RAM
- RAM is the Primary storage. Volatile storage, temporary storage. 
- ROM: Read-only memory, permanent, BIOS. 
- Cache memory <- I have nothing so far.
 
### Define Volatile Memory <- nothing in week 8:
But it's a type of memory that maintain its data only while it's powered. If power is interrupted the data is lost. 

--------------------------------------------------
### He mentioned this during the review for the first time. No clue what is the context. Have fun.. 
- Firmware
- Freeware
- shareware
### ChatGPTeed it:
- **Firmware**: Firmware refers to software that is permanently programmed into a hardware device. It provides low-level control over the hardware and is typically not easily changeable by the end user.
    
- **Freeware**: Freeware refers to software that is available for use at no cost. Users can download and use freeware without having to pay a license fee.
    
- **Shareware**: Shareware is software that is distributed with the intention that users can try it before purchasing a license. Users often get a trial period or limited functionality for free, and if they decide to continue using the software with full features, they are usually required to purchase a license.

#### These terms describe different ways in which software is distributed and accessed by users.

--------------------------------------------------
### System Bus:
	MCQ
	Written
**Control bus**: control and coordinating activities of the two other buses.  
**Address bus**: Carry memory address
**Data bus**: Carry data 

### Define software: 
Computer programs that are when executed provides desired function and performance data structures that manipulate information and documents that describe the operation and use the program. 

#### System software:
- OS
- Utility
	- Compiler: Converts the Whole program from high-level language into assembly language
	- Interpreter: Converts and execute high-level program one line at a time (line by line)
	- Assembler

--------------------------------------------------
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
-------------------------------------------------------------------
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
 
--------------------------------------------------
### Levels of Computer Architecture - Slide (36)
- Level 6: User - Executable programs 
- Level 5: High-Level Programming - C++, Java, FORTRAN, etc. 
- Level 4: Assembly Language - Assembly code 
- Level 3: System Software - Operating system, library code 
- Level 2: Machine - Instruction Set Architecture 
- Level 1: Control - Microcode or Hardwired 
- Level 0: Digital Logic - Circuits, gates, etc.
--------------------------------------------------

### Programming Models

- The **programming model** is determined by how the processor architecture manages internal (CPU registers) and external (RAM) memory during program execution.
- It defines how instructions access operands and how instructions are described in the processor's assembly language.

### Programming Models: Stack-Based and GPR Architectures

There are two primary programming models :

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

##### Advantages of Stack-Based Architectures

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

##### Advantages of GPR Architectures

- GPR compilers provide better performance.

--------------------------------------------------
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

### Example: A = A * B Slide (49)

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

--------------------------------------------------
## All models week 8 - slide (54-59)
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

// Example form W9 - Slide(8)
// A=B+(C*D)
load C
mul D
add B
store A
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

--------------------------------------------------
--------------------------------------------------

# Week 9
### Infix and Postfix
> Not sure: but i think he said will provide tree and ask us to write infix or postfix 
![](Pasted%20image%2020230814194710.png)

### B -> Byte and b -> bit

### Slide(14) -> MCQ: the backward compatibility thingy 

### Slide(16) 
![](Pasted%20image%2020230815064346.png)
##### 8-byte word in little-endian memory. (a) aligned (b) not aligned
##### (b) have separate spaces for instructions and data. 

### Slide(17) -> special-purpose registers 
- Program Counter (PC)
- Stack pointer
#### Available only for kernel mode. They are used by the OS only, to control memory, I/O devices and hardware. 

### Slide(18) -> Flags and PSW registers are hybrid (kernel/user modes)
	-mcq
	N -> Negative
	Z -> Zero
	V -> oVerflow
	C -> Carry of the leftmost bit
	A -> Carry out of bit 3.
	P -> even Parity

### Slide(20)
		-mcq
- 80386 first 32-bit machine in intel family. 
- All subsequent CPUs have essentially same 32-bit architecture called `IA-32`.
- The only major change after that bad boy (80386) was the introduction of `MMX` MultiMedia Extensions, `SSE` Streaming SIMD (Single Instruction Multiple Data)
> From last quiz+W10: 
> SIMD allows multiple data to be processed simultaneously 
> SIMD exploits data-level parallelism 
> Same instruction stream to multiple streams
> High processing rate
> Data-intensive 
> Commonly used in multimedia applications (e.g.: )
`side note: Data-level paralism when data is splitted and processed at same time, instruction level parallism is when the program itslef splitted and executed spererattly at the same time`
`Not sure: Data must be homegenous`
```
//16-bit
AX, BX, CX

//32-bit
EAX, EBX
```

### Slide(21)
- Pentium 4 three operating modes:
	- Real mode
	- Protected mode
		- Four privilege levels
		- `mcq` **Level 0- kernel mode**
		- `mcq` **Level 3- User mode**
		- Level 1 and 2 rarely used
	- System management mode (SMM)
### Slide(25)
- `mcq`**Byte Addressing** (Pentium 4): memory organised and accessed as sequence of bytes
- `mcq`Byte address used to locate byte or bytes 
- `mcq`The range of memory called **Address space**
- `mcq`processor also supports **segmented addressing** this is a form of addressing where program have independent spaces called **segments**
`He loves this example: How computer can handle program needs more memory than the available RAM?? answer is Virtual Memory 🤯 `

### Slide(28):
| Type of re         | Register used | Segment used                  | Default selection rule            |
|--------------------|---------------|-------------------------------|-----------------------------------|
| Instruction        | CS            | code segment                  | Instruction fetch                 |
| `mcq`Stack         | SS            | stack segment                 | stack ops. PUSH/PULL              |
| Local Data         | DS            | Data segment                  | Data references                   |
| Destination String | ES            | Data segment pointed to by ES | Destination of string instruction |

### Slide(29)
`not sure: probably AX is 16-bit (AH,AL) vs EAX which is 16-bit`
### Slide(30)
- In Pentium 4: **EIP** Extended instruction pointer
- In RISC it's called **PC** (program counter)
### Slide(32)
#### Interrupts and Exceptions 
- Two mechanisms for interrupting program execution:
	- **Interrupts**: ***Asynchronous*** -> triggered by I/O device
	- **Exception**: ***Synchronous*** -> generated when detect predefined condition, has 3 types:
		- Faults
		- Traps
		- Aborts
`Processor respond to interrups and exceptions in essentially the same way. When intterupt of exception is signalled, the processor halts execution of current program and switches to handler procedure that has been written specifically to handle the the interrupt or exception`
- The processor accesses the handler procedure through and entry in the **interrupt descriptor table (IDT) ❤️**
- When the handler complete handling, control returned to the interrupted program. 
### Slide(34)
`conflict` `mcq` `FYI`
- Intel Architecture defines `16` predefined interrupts and exceptions and `224` user defined interrupts, which are associated with entries in the IDT ❤️, identified with a number called vector. 
### Side(40)
- `mcq`UltraSPARC III architecture is LOAD/STORE architecture 

### Side(42)
#### JVM ISA level
- `mcq`Byte order is `big-endian`
- `mcq`JVM contains extra region in memory, `the heap`, used by runtime storage allocator 🐊 for storage of dynamic and large object. 

### Side(52)
- `mcq` UltraSPARC has 31 different instruction formats. 


### Side(56)
#### Addressing modes: `written question`
- **Immediate**: The address part contains the value of the operand itself
`add r1, #5` `r1 <- r1+5`
- **Direct**: address field contains the actual full address memory of the operand
`add r1, (0x200)`  `r1 <- r1 + M[0x200]`
- **Register Addressing**: Same as direct but it specifies the register instead of memory location 
`add r1, r2`  `r1 <- r1 + r2`
- **Register Indirect**: Instruction refers to the address contained in the register (pointer)
`add r1, (r2)`  `r1 <- r1 + M[r2]`
- **Displacement**
`add r1, 100(r2)` `r1 <- r1 + M[r2+100]`
- **Indexed**:
`add r1, (r2+r3)`  `r1 <- r1 + M[r1+r3]`

### Slide(65)
- `not important but I have it written muliple times`
- Pentium 4: `Mov R1, R2 --> MOV DES, SRC`

### Slide(72)
#### Flow of control: `written question`
![](Pasted%20image%2020230815083626.png)
- Not sure what kind of questions here !!! 🤷🏽
- (a) program counter: sequential without branches, means no jumps
- (b) program counter with branches, means with jumps 

### Slide(73)
 🫤 `written question`
> I added the code blocks, not from his notes

> I assume he means Subroutines vs Coroutines 
#### Procedures: function or subroutine
```python

def add_numbers(a, b):
    return a + b

```

![](Pasted%20image%2020230815084404.png)
- When procedure called, execution of procedure always begins at the first statement of the procedure.
#### Coroutines

```python
import asyncio

async def hello_world():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(hello_world())
```
![](Pasted%20image%2020230815084418.png)
When coroutine is resumed, execution begins at the statement where it left off the previous time not the beginning. 


### Slide(75)
- Trap is an automatic procedure call initiated by some conditions caused by the program.
- The flow of control switched to procedure called `Trap handler`

### Slide(76)
- `mcq` interrupts are change in the flow of control caused by event, usually related to I/O.

### Slide(77) 
`not marked as potential question`
- Taps are `Syncronus` <- mentioned before as one type of exceptions
- Interrupts are `Asyncronus`


### Slide(78)
`conflict` `FYI` `Question`
- Each interrupt has priority (vector), I assume it's defined in the lovely IDT table. 