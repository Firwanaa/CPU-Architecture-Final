# CPU Architecture Final - Part 2 - Sheridan College - SYST27198
# ![](helmt.png)
# 🚧 🏗️
### ⚠️️️ This repo still under construction, Use with high caution, Wear Safety Helmet 👷 ⛔
# 🚧 🏗️
# Week 8
> #### He was flying, this what i was able to write down.

### Slide(6)
#### CPU: Three sub-units:
- Control Unit
- Memory Unit
- Arithmetic Logical Unit 
	  - Arithmetic operations: + , -, *, /
	  - Logical: >, < , <=, <=, !=

--------------------------------------------------
### Slide(8)
#### MCQ: Cash memory, ROM and RAM
- RAM is the Primary storage. Volatile storage, temporary storage. 
- ROM: Read-only memory, permanent, BIOS. 
- Cache memory <- I have nothing so far.
### From Carrie
![](Pasted%20image%2020230815212334.png)
### Define Volatile Memory <- nothing in week 8:
But it's a type of memory that maintain its data only while it's powered. If power is interrupted the data is lost. 

### Slide(9)
#### System Bus:
	MCQ
	Written
**Control bus**: control and coordinating activities of the two other buses.  
**Address bus**: Carry memory address
**Data bus**: Carry data 
### Slide(10)
`written question`
### Define software: 
Computer programs that are when executed provides desired function and performance data structures that manipulate information and documents that describe the operation and use the program. 

--------------------------------------------------
### Slide(11)
#### He mentioned this during the review for the first time. No clue what is the context. Have fun.. 
- Firmware
- Freeware
- shareware
### ChatGPTeed it:
- **Firmware**: Firmware refers to software that is permanently programmed into a hardware device. It provides low-level control over the hardware and is typically not easily changeable by the end user.
    
- **Freeware**: Freeware refers to software that is available for use at no cost. Users can download and use freeware without having to pay a license fee.
    
- **Shareware**: Shareware is software that is distributed with the intention that users can try it before purchasing a license. Users often get a trial period or limited functionality for free, and if they decide to continue using the software with full features, they are usually required to purchase a license.

#### These terms describe different ways in which software is distributed and accessed by users.

--------------------------------------------------
#### System software:
- OS
- Utility
	- Compiler: Converts the Whole program from high-level language into assembly language and then **machine language**
	- Interpreter: Converts and execute high-level program one line at a time (line by line)
	- Assembler

--------------------------------------------------
## Slide(random(1-78))
`Tried to orgnize it as much as I can, he was jumping around`
- System software -> System request
- Application -> user request

- CPU only process information in RAM, means It doesn't read from hard-drive or any secondary storage.(u know read/write speed and some other stuff). 
### Slide(13)
- 1945 - 1955 no operating system, no translation programs needed because we were using machine language to write programs.
- No Utility software: Because we were programming in machine language babe, compilers for noobs.  

### Slide(17)
- Monogramming: loads ONE instruction to CPU, have to SWAP each time need to process new instruction
- Multiprogramming: can have many processes at a time, CPU can SWITCH to a different instructions. 

- Batch processing: Group of similar jobs

- Network operating system
  - share of data
  - share of resources 

- Distributed: Divide work between multiple processes
### Slide(25)
- User mode: no IO operations allowed
- Kernel mode: (privileged, OS mode, Supervised)
  - IO operations
  - File operations 
  - Memory operations
- System call: user ask OS to switch from user mode to kernal mode (TRAP instruction)
### Slide(28)
- Types of System calls:
  - Process control
  - File management
  - Device management
  - Information maintenance
  - Communications
-------------------------------------------------------------------
### Slide(29-31)
#### Semantics of System call execution: 100% in the final 
- 1- The user process calls a **library function**
- 2- The library function sets **system call parameters** (including arguments, return, address, and call number) in designated location like register or stack
- 3- A **trap instruction shifts** the mode form user mode to kernel mode, transferring control to the OS.
- 4- The OS identifies the system call by examining the **call number** parameter received from the library function
- 5- Using the call number, the kernel access a **dispatch table** containing pointers to service routines for various system calls.
- 6- The relevant **service routine executes**, control returns to the user program after the trap instructions, and the mode switches back to user from system. 
- 7- The library function processes the instruction after the trap, interprets kernel return value, and **return to the user** process.
![](Pasted%20image%2020230814000847.png)
#### Summery for the 7 steps by ChatGpt :
- 1- User process calls a library function.
- 2- Library function prepares system call parameters.
- 3- Trap instruction switches mode to kernel, yielding control to the OS.
- 4- OS identifies the system call based on the provided call number.
- 5- Kernel accesses a dispatch table with service routine pointers using the call number.
- 6- Service routine executes, control returns, and mode switches back to user.
- 7- Library function interprets results, returns to user process.
 
--------------------------------------------------
### Slide(36)
`mcq`
#### Levels of Computer Architecture - Slide (36)
- Level 6: User - Executable programs 
- Level 5: High-Level Programming - C++, Java, FORTRAN, etc. 
- Level 4: Assembly Language - Assembly code 
- Level 3: System Software - Operating system, library code 
- Level 2: Machine - Instruction Set Architecture 
- Level 1: Control - Microcode or Hardwired 
- Level 0: Digital Logic - Circuits, gates, etc.
--------------------------------------------------
### Slide(39)
`no mark`
#### Programming Models

- The **programming model** is determined by how the processor architecture manages internal (CPU registers) and external (RAM) memory during program execution.
- It defines how instructions access operands and how instructions are described in the processor's assembly language.

### Slide(39-45)
#### Programming Models: Stack-Based and GPR Architectures

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
## Slide(43) `written question`
   **Example: Compute $3*7+2$**
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
#### ISA and CPU Design Styles

#### Different ISA for Different CPUs

- Different CPUs implement distinct sets of instructions.
- Examples include ARM, Intel x86, IBM/Motorola PowerPC (Macintosh), MIPS, and Intel IA32.

#### Two CPU Design Styles

1. **RISC (Reduced Instruction Set Computing):**
   - Involves a small set of highly optimized instructions.
   - Instructions typically perform simple tasks.
   - Focuses on executing instructions quickly.

2. **CISC (Complex Instruction Set Computing):**
   - Features a larger, more complex set of instructions.
   - Some instructions can perform complex tasks directly.
   - Emphasizes code compactness.

#### Historical Comparison: RISC vs. CISC

#### Complex Instruction Set Computing (CISC)
- Examples: x86 architecture.
- Larger instruction set with intricate instructions built into hardware.
- Variable length instructions.
- Multiple clock cycles per instruction.

#### Reduced Instruction Set Computing (RISC)
- Examples: ARM architecture.
- Smaller, highly optimized set of instructions.
- Specific memory access instructions.
- One instruction executed per clock cycle.
- Instructions are of the same size and fixed.
### Slide(49)
`important`
#### Example: A = A * B Slide (49)

#### RISC

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

#### CISC
```assebly
MULT B, A
```
1. **MULT B, A**
   - Multiply the values of A and B to generate the result.
### Slide(52)
- `mcq`What makes good ISA?
	- Programmability
	- Implementability
	- Compatibility

--------------------------------------------------
### All models week 8 - slide (54-59)
`important`
- **Sequential Model**: The program counter (PC) defines total order on dynamic instruction 
- **Memory Only**: ***Slides are screenshots***
> Slide(55) where (other than memory) can operands come from? and how are they specified? **No Clue!!!*
		> Example A = B + C
		> Several options 
		- memory only:
```
Add B, C, A                  mem[A] = mem[B] + mem[C]
```

`Exam question`
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
add   C, R2               R1 = R1 + mem[C]
add   R1, R2, R1          R1 = R1 + R2
store R1, A               mem[A] = R1
```


### Slide(59)
`most important`
#### Operands Models Pros and Cons:
#### Metric  I: Static code size
- Number of instructions needed to represent program, size of each
- Wants many implicit operands
- **Rank Good -> Bad**: memory, accumulator, stack, load-store
####  Metric  II: Data memory traffic
- Number of bytes move to and from memory
- Wants as many long-lived operands in on-chip storage
- **Rank Good -> Bad**: load-store, stack, accumulator, memory
#### Metric  II: Cycles per instructions 
- Want short (1 cycle), little variability, few nearby dependences
- **Rank Good -> Bad**: load-store, stack, accumulator, memory

**Upshot**: most new ISAs are load-store or hybrids.  

--------------------------------------------------
--------------------------------------------------

# Week 9
### Week 8 Slide (71)
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
`He loves this example: How computer can handle a program needs more memory than the available RAM?? answer is Virtual Memory 🤯 `

### Slide(28):
| Type of re         | Register used | Segment used                  | Default selection rule            |
|--------------------|---------------|-------------------------------|-----------------------------------|
| Instruction        | CS            | code segment                  | Instruction fetch                 |
| `mcq`Stack         | SS            | stack segment                 | stack ops. PUSH/PULL              |
| Local Data         | DS            | Data segment                  | Data references                   |
| Destination String | ES            | Data segment pointed to by ES | Destination of string instruction |

### Slide(29)
`not sure: probably AX is 16-bit (AH,AL) vs EAX which is 32-bit`
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

--------------------------------------------------
--------------------------------------------------

# Week 10

### Slide(3)
`mcq + written`
#### Data-level Parallelism DLP: 
many data items that can be operated at the same time.
#### ILP Instruction-level Parallelism: Function or Control parallelism
tasks "instructions" can be operate independently and largely in parallel. 
`multiprocessor`

### Slide(10)
#### ISA `mcq`
- Operations:
	- Data transfer
	- arithmetic logical
	- control and floating point
- Control flow instructions:
	- All ISAs support
		- Conditional jumps
		- Unconditional jumps
		- Procedure calls
		- returns
- Encoding:
	- Two basic choices on encoding 
		- fixed length and variable length
		- All MIPS instructions are 32 bit long
### Slide(12)
`mcq`
- Consider two different computers X and Y
- Performance
$$
n = \frac {Execution time_y}{Execution time_x} = \frac{\frac{1}{Performance_y}}{\frac{1}{Performance_X}} =\frac{performance_x}{performance_y} 
$$
### Slide(13)
- `mcq`Execution time
	- Wall-clock time
	- response time
	- elapsed time <- which is the latency to complete a task `seen by the user not the CPU time`


### Slide(21)
## Pipelining
- A technology of decomposing a sequential process into suboperation, with each suboperation completed dedicated in segment. 
- Pipe lining doesn't help latency of single task, it helps throughput of entire workload. 
- Pipeline rate limited by slowest pipeline stage.
- Unbalanced length of pipe stages reduces speed-up. 
- Time to "fill" and "drain" reduce the speed-up.
- Stall for Dependence 
### Slide(26)
`mcq`
- In computing a pipeline is a set of data processing elements connected in series, so that the output of one element is the input of the next one. 
- Elements of pipeline are often executed in parallel or in time-sliced fashion. 
- Today, pipelining is the key implementation technique used to make fast CPUs.
- Conventional microprocessors are **synchronous** circuits that used buffered synchronous pipelines
- Pipeline Registers are inserted in-between pipeline stages, and are clocked synchronously. 
- There is **Asynchronous Pipelines** with pipeline registers clocked Asynchronously
- **unbuffered pipelines** called "wave pipelines"
- 
- **Pipelining** is an implementation technique whereby multiple instructions are overlapped in execution. 
- `mcq`**Pipelining** increases the CPU instruction throughput, but it does not reduce the execution of an individual instruction. 
- `mcq` In fact it usually slightly increases the execution time of each instruction due to overhead in the control of the pipeline.
- `mcq`The increase in instruction throughput means that the program runs faster and has lower total execution time, even thought no single instruction runs faster. 
- `mcq` imbalance among pipeline stages reduce performance. 
## Mrinal notes /// start
#### Example question: (with traditional pipeline)
|      | 30   | 30   | 30     | 30     | 30     | 30     |
|------|------|------|--------|--------|--------|--------|
| Car1 | wash | dry  | polish |        |        |        |
| Car2 |      | wash | dry    | polish |        |        |
| Car3 |      |      | wash   | dry    | polish |        |
| Car4 |      |      |        | wash   | dry    | polish |

- Total Time $= 3 hours$
- Without pipeline = 1.5 (total of 3 stages) x # of cars = 6 hours
- $Pipelined=\frac{6}{3}=2$
- (a) If the time b/w pipelines is same then:
$pipelinedTime =\frac{TimePerInstruction}{NumOfPipeStages}$

- #### (b) Example Question: 
	- 5 stages each take 1 ns, how much time would 100 instructions take pipelined & unpipelined & what is the speedup?
	- stages=5, time per stage= 1 ns, # of instruction = 100. 
	- $Unpipelined=5ns*100=500ns$ 
	- $Pipelined=\frac{500}{5}=100ns$
	- $speedUp=\frac{Unpiplined}{Pipelined}=\frac{500}{100}=5 times$
- #### (c) Show how pipeline occurs in RISC for 5 instructions if each takes 1 ns, calculate total time:
|        | 1  | 2  | 3  | 4   | 5   | 6   | 7   | 8   | 9  |
|--------|----|----|----|-----|-----|-----|-----|-----|----|
| ins#1  | IF | ID | Ex | MEM | WB  |     |     |     |    |
| int#2  |    | IF | ID | Ex  | MEM | WB  |     |     |    |
| ins#3  |    |    | IF | ID  | Ex  | MEM | WB  |     |    |
| ins#4  |    |    |    | IF  | ID  | Ex  | MEM | WB  |    |
| inst#5 |    |    |    |     | IF  | ID  | EX  | MEM | WB |
- Total time = 9 ns. 
#### RISC
- RISC takes at most 5 clock Cycles
- Instruction Fetch (IF)
- Instruction Decode (ID)
- Execution (Ex)
- Memory access (MEM)
- Write-back cycle (WB)
### Slide(37)
- Pipeline overhead arises from combination of ***pipeline register delay*** and ***clock skew.*** 
- Pipeline Overhead = pipeline register delay + clock skew. 
- Once clock cycle is as small as the sum of the clock skew and latch overhead. NO further pipelining is useful. 

### Slide(38,39) cont' Mrinal Notes
![](Pasted%20image%2020230815191341.png)
$AvgInstruction=ClockCycle*AvgCPI$
$AvgIns=1ns*(\frac{4*40}{100} + \frac{4*20}{100} +\frac{5*40}{100})$
$Unpipelined=1ns*(4.4)=4.4ns$
$Pipelined=1+0.2ns=1.2ns$

>note: In pipelined stage, the clock must run at the speed of the slowest stage plus overhead

$speedup=\frac{Unpipelined}{pipelined}=\frac{4.4}{1.2}=3.7 times$


## Mrinal notes /// end

### Slide(41)
#### Pipeline Hazards: Situation prevents next instruction from executing during its designated clock cycle. 
- Structural Hazard: **resource conflict**,when hardware can not support all possible combinations simultaneously
	- solved by:
	  - Renaming
	  - stalling: Stall the pipeline for 1 clock cycle. A stall commonly called a pipeline bubble or just bubble.
	  - bubbling
- `written`Data Hazards: **Instruction depends** on the result of a previous instruction because of overlapping
	- Data Hazard occur when the pipeline changes the order of read/write accesses to operands so that the order differs from the order seen by sequentially executing instructions on unpipelined processor. 
	- solved by:
		- Forwarding also called bypassing or short-circuiting
		- Stalling
```arm
DADD R1, R2, R3
DSUB R4, R1, R5
AND  R6, R1, R7
OR   R8, R1, R9
XOR  R10, R1,R11
```

- All instructions after the `DADD` use the result of `DADD`
- The `DADD` write value to `R1` at `WB` stage
- `DSUB` reads the value during `ID`


- `no mark`Control Hazard: arise from the **pipelining of branches** and another instructions that change the PC.  
	- Can cause greater performance loss for MIPS pipeline than data hazard

### Slide(59)
- If all instructions take the same number of cycles, which must also equal the number of pipeline stages:
  $speedup=\frac{pipelineDepth}{1+pipelineStallCyclePerInstruction}$

### Slide(68)
- Simplest and most common way to exploit parallelism among iterations of loop, which is called loop-level parallelism. 
`mcq`
```python
for(i=0; i<= 999; i=i+1)
	x[i] = x[i]+y[i];
```
- Every iteration of the loop can overlap with any other iteration
- Unrolling the loop statically by the compiler or dynamically by the hardware. 
### Slide(69)
- Important alternative to loop-level parallelism is use of **SIMD** 

### Slide(70)
#### SMID
`mcq + written`SMID machine are capable of applying the exact same instructions stream to multiple streams of data simultaneously. 
- High processing rate

### Slide(73)
`no mark`
- Data dependence
- Name dependence
- Control dependence

### Slide(74)
- `mcq`Data Dependence
	- Data dependence conveys three things:
		- The possibility of hazard
		- The order in which results must be calculated and
		- An upper bound on how much parallelism can be exploited. 
   - `written`A data dependence can be overcomed in two ways:
	   - Maintaining the dependence but avoiding the hazard (Forwarding)
	   - Eliminating dependence by transforming the code.

### Slide(75)
- Name dependence
	- when two instructions use the same register of memory location called `name`

- `mcq`An Antidependence: when instruction j writes a register or memory location that instruction i read. 
- An output dependence: when instruction i and instruction j write the same register or memory location. 
### Slide(78)
- Data Hazards
	- RAW (Read After Write)
	- WAW (Write After Write)
	- WAR (Write After Read)
`RAR (Rread After Read) case is not a hazard`

### Slide(80) <- read it, no energy to type anymore.
`mcq`
- example
```python
if p1{
	  s1;
	  };
if p2 {
	 s2;   
};
```



--------------------------------------------------
--------------------------------------------------

# Week 12

### Slide(4)
## `MCQ`
- #. of transistors doubles appox. every two years
### Slide(7)
- Superscalar CPU design complex:
	- Instruction dependencies 
	- Resource allocation 
### Slide(9)
- Virtual Memeroy
	- Paging and Segmentation 
### Slide(10)
- Multicore CPU
	- Video Rendering
	- Scientific simulations
### Slide(12)
- Hyperthreading
	- Video editing
	- Gaming
### Slide(15)
- Vector Processing
	- Scientific simulation 
	- computer graphics 
### Slide(16)
- SIMD
	- Homogeneous data
