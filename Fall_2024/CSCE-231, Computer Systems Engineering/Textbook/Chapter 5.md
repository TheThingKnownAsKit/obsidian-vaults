Common should knows:
() around a memory address will dereference it like a *
$num is used to input literal values
Don't forget addressing modes
[[x86-64-cheat-sheet.pdf]]

## Instruction Set Architectures
An <mark style="background: #ADCCFFA6;">instruction set architecture (ISA)</mark> is the lowest level of abstraction you can get without thinking in terms of hardware. It is the collection of assembly language instructions

An <mark style="background: #ADCCFFA6;">assembler</mark> translates assembly language instructions into machine code (also known as object code)

There are two categories:
1. <mark style="background: #ADCCFFA6;">Complex Instruction Set Computers (CISC)</mark>
	1. Earlier era of computing with less processing power and space. Very few registers available (some only had one the accumulator)
	2. Designed to be written directly in assembly by programmers with as few instructions as possible to take up as few bytes as possible
	3. Fit multiple machine instructions into one command. Variable-length machine code
2. <mark style="background: #ADCCFFA6;">Reduced Instruction Set Computers (RISC)</mark>
	1. Developed to reduce circuitry size and increase the availability of general-purpose registers. Requires less power
	2. Generally require multiple instructions for the same functionality achieved by one CISC instruction
		1. Even though there were more instructions, it was faster than CISC
	3. Fixed-length instructions (usually 4 bytes)
	4. Only have load/store instructions to access memory

## Representative CISC Instruction Set (x86)
x86 is 16-bits
x86 IA32 is 32-bits
x86 ISA is 64-bits

### Registers
![[Pasted image 20241009121630.png]]
![[Pasted image 20241009121644.png]]
![[Pasted image 20241009121247.png]]

<mark style="background: #ADCCFFA6;">Virtual registers</mark> made use of some of the spare space (upper 8 and lower 8 bits) of some of the physical registers

### Addressing Modes
For x86 ISA specifically

An <mark style="background: #ADCCFFA6;">addressing mode</mark> is a way to describe a memory location
The common modes are all special cases of the general form:
$$D(R_b,R_i,S)$$ where Rb is the base register, Ri is the index register, S is the scale, and D is the displacement

Displacement usually uses hex displacement, so like 0x10(%rax), which adds 0x10 to the memory address contained in %rax (ie 0x84E8 becomes 0x84F8)
	If whole number, bytes
Displacement is mostly used to access the elements of a struct or access memory relative to the stack pointer
Note: If the base address is omitted, than D represents an absolute address instead of a displacement. Index a comma before the index register so that the assembler can easily detect that the register isn't the base -> 0x84E0(,%r9,8)

You add Ri to Rb to get the current address

S can only be 1, 2, 4, or 8. It is essentially (Rb+Ri) * S. Usually indicated as the size of elements in an array
	1 for chars
	2 for shorts
	4 for ints or floats
	8 for longs, doubles, or pointers

### Move Instructions
MOV copies the data from one location and places the copy in another. Could be memory locations or registers
You can also place the source datum in the instruction itself; so that it becomes an <mark style="background: #ADCCFFA6;">immediate value</mark> -> essentially a constant value

In the form
$$movq\text{ }\text{ }\text{ }source,destination$$
Where q is the number of bites using a keyword b, w, l, q, word, long-word, quad-word (reference cheat sheet)

### Arithmetic and Logical Instructions
![[Pasted image 20241009123917.png]]
![[Pasted image 20241009135536.png]]
![[Pasted image 20241009135549.png]]

## Representative RISC Instruction Set
ARM original had 32-bit architecture with 16 general-purpose registers
A64 is 64-bit architecture and 32 general purpose

Memory addressing mode form:
$$[R_b,\Delta]$$
Where Rb is the base register and Delta is the displacement

General form of a load instruction:
$$ldr\text{ }\text{ }\text{ }R_{t,}addr$$
Where Rt is the target register and addr is the source memory

![[Pasted image 20241009141127.png]]

General form of a store instruction:
$$str\text{ }\text{ }\text{ }R_s,addr$$
Where Rs is the source register and addr is the target memory

Data processing general form:
$$Instruction\text{ }\text{ }\text{ }R_t,R_s,Source2$$
Where Rt is the target register, Rs is the register containing the operand being operated on, and Source2 is either a register or an immediate value to be used to operate on value in Rs

![[Pasted image 20241009141342.png]]
![[Pasted image 20241009141353.png]]
![[Pasted image 20241009141407.png]]

## Reality Check?
Now people just use pipelines like Pentium Pro to create a "wrapper" that translates each x86 <mark style="background: #ADCCFFA6;">macro-operation</mark> into one or more of the RISC core's <mark style="background: #ADCCFFA6;">micro-operations</mark>

Get to enjoy the performance benefits while also enjoying the increased programming functionality

RISC also added more complex operations over time and is more CISC