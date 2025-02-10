## Overview
**Exam 1:**
Chapters 2, 3, and 4

- Convert decimal↔binary↔hexadecimal
- Integers
    - Know the difference between signed & unsigned integers
    - Determine if a signed value is positive or negative
    - Given x, determine the bit pattern for −x
    - Add and subtract integers
        - Detect overflow
    - Multiply and divide an integer by 2n
- IEEE 754 Floating Point
    - Know the difference between normal, subnormal, and special values
    - Convert binary fixed point→decimal
    - Convert binary fixed point↔“scientific notation”↔quarter-precision floating point (only for normal values)
    - Rounding

**Exam 2:**
Chapters 5, 6, 7 and the first part of 11

- Differences between CISC & RISC instruction set architectures
- Read simple x86-64 assembly
    - Compute memory address based on addressing modes
        - D(Rb,Ri,S) and variations
    - Recognize simple instructions (movq, subq, incq, etc.)
        - Know where operands’ data is and where the result goes
- Given an x86-64 assembly arithmetic (addition/subtraction) instruction
    - Identify where the operands’ data is stored
    - Pull operands’ data from registers/memory
    - Compute the result
    - Identify where the result will be stored
- Compiler “recipes”
    - Structured programming (take it as far as “goto-style” C code): if, do-loop, while-loop, switch, conditional assignment
    - x86 Procedure calls: push/pop, call/ret, arguments
    - Structured data: 1D array, nested array, struct
- Buffer overflow: how to protect against buffer overflow attacks (system-level protections, compiler-level protections, programming-level protections)
- Concurrency
    - Process-based vs Thread-based concurrency
    - Valid/invalid interleavings

**Final Exam Part 1:**
Chapters 8, 9, and 10

- Simple processor architecture datapath
    - What each component does for each instruction
    - Control signals
- Data dependency hazards (review x86 assembly code if you need to)
- Pipeline performance: minimum clock cycle, throughput, latency
- Pipeline penalties: average penalties for various types of instructions, and the total average penalty
- Memory-mapped I/O (review data structures and constructing bit-vectors if you need to)
- Exceptional Control Flow: interrupt handling, context switches (review processes if you need to)
- Memory hierarchy: relative speed, size, and cost of memory tiers (ordinal, not exact numbers) and the concept of locality
- Direct-mapped cache and set-associative cache: determine the size, determine how many bits are needed for the block offset and set index, identify the block offset, the set index, and the tag, handling hits and misses

**Everything should be filled in except 6, 7, some parts of chapter 9 (reference example exam), and SRAM vs DRAM in chapter 10**

## Chapter 2 - Binary
You know how bit operations and binary works

In a big endian system, the least significant bit is stored in the highest address. Opposite for little endian
## Chapter 3 - Integers
OVERFLOW:
For unsigned integers:
If and only if the carry-out from adding the most significant bit is 1, overflow occurred
For signed integers:
1. If you add two positive numbers together and the result is negative, it overflowed. Vice versa with positive
2. Procedurally, you can compare the MSB carry-in and carry-out value.
	1. If one of these bits is 1 and the other is 0, overflow occurred
	2. If they're both 1 or both 0 then overflow did not occur

For two's complement: pad 0's and keep sign bit. To convert from negative decimal to binary, put it into binary form, flip everything, add 1
## Chapter 4 - Floating Point
To convert from fixed-point form to decimal, calculate the binary value of above the ., that is the whole number. Then, calculate the binary value of below the . and divide it by $2^{NumOfBits}$
	Example: 110.111 in binary to decimal
	110 is 6 in binary
	111 is 7 in binary
	there are 3 spaces after the ., 
	which is 2^3 which is 8, so 7/8 = 0.875
	Answer: 6 and 7/8ths or 6.875

The bias is $2^{w-1}-1$ where w is the number of bits in the exponent field

From floating to binary:
2. Sign bit: The first bit will be the sign
3. Exp bits: Take the exponent of the 2 and ADD the bias to it to get the value. Convert this value to binary
5. Frac bits: It's just the bits to the right of the .
Example: Convert -1.011 x 2^2 to binary
1. first bit is 1 from the negative sign
2. 2 is the exponent, 2 + 7 = 9, 9 in binary is 1001
3. Last 3 bits are 011
4. Answer is 1100 1011

From floating to decimal:
1. Sign: What is the sign bit?
2. Fraction: Sum everything to the right of the decimal point with decreasing negative exponents. Example: 2^-1 + 2^-2 + 2^-3
3. Exponent bits: Calculate the exponent value of 2^E
4. Multiply frac by exp and apply sign
Example: What is the value of 1.101 x 2^4 in decimal?
1. Not negative
2. To get frac: 2^-1 + 2^-3 = 1.625
3. 2^4 is 16
4. 16 x 1.625 = 26 (not negative)

From binary to floating:
1. First bit is sign
2. Next bits are the exponent. Convert to decimal and SUBTRACT the bias
3. The last bits are the fraction
Will follow the form: (sign)1.frac x 2^{exp}
	Example: 0100 0111 is 1.111 x 2^1 

## Chapter 5 - Assembly Instructions
CISC vs RISC
1. Complex Instruction Set Computers (CISC)
	1. Earlier era of computing with less processing power and space. Very few registers available (some only had one the accumulator)
	2. Designed to be written directly in assembly by programmers with as few instructions as possible to take up as few bytes as possible
	3. Fit multiple machine instructions into one command. Variable-length machine code
2. Reduced Instruction Set Computers (RISC)
	1. Developed to reduce circuitry size and increase the availability of general-purpose registers. Requires less power
	2. Generally require multiple instructions for the same functionality achieved by one CISC instruction
		1. Even though there were more instructions, it was faster than CISC
	3. Fixed-length instructions (usually 4 bytes)
	4. Only have load/store instructions to access memory

() around a memory address will dereference it like a *
$num is used to input literal values

An addressing mode is a way to describe a memory location
The common modes are all special cases of the general form:
$$D(R_b,R_i,S)$$where Rb is the base register, Ri is the index register, S is the scale, and D is the displacement

| Instruction           | What It Does                                     |
| --------------------- | ------------------------------------------------ |
| mov     src, dst      | dst=src                                          |
| lea       addr, dst   | dst=addr                                         |
| add      src, dst     | dst+=src                                         |
| sub      src, dst     | dst-=src                                         |
| imul      src, dst    | dst*=src                                         |
| neg      dst          | dst=-dst                                         |
| idivq     S           | divides rdx by S                                 |
| sal        count, dst | dst<<=count                                      |
| sar       count, dst  | dst>>=count (arith shift)                        |
| shr       count, dst  | dst>>=count (logical shift)                      |
| and      src, dst     | dst&=src                                         |
| or         src, dst   | dst\|=src                                        |
| xor       src, dst    | dst^=src                                         |
| not       dst         | dst = ~dst                                       |
| cmp     a, b          | b-a, set flags                                   |
| test      a,  b       | a&b, set flags                                   |
| set       dst         | sets byte to 1 when condition holds, o otherwise |
| jmp      label        | jump to label (unconditional)                    |
| je         label      | =                                                |
| jne       label       | !=                                               |
| js         label      | jump if negative                                 |
| jns       label       | jump if not negative                             |
| jg         label      | >     (signed)                                   |
| jge       label       | >=   (signed)                                    |
| jl          label     | <     (signed)                                   |
| jle        label      | <=   (signed)                                    |
| ja         label      | >      (unsigned)                                |
| jae       label       | >=   (unsigned)                                  |
| jb         label      | <      (unsigned)                                |
| jbe       label       | <=   (unsigned)                                  |
## Chapter 6 - Assembly Structures
Literally just arrays, do-while, nested arrays, if/else, and structs in assembly
I do not know how to do this

While loops and if/else can be pretty common sense. Pick the labels and conditions that make sense

I do not understand arrays but you'll need to know how to find the addresses of array indexes

How many bytes for a struct object?
## Chapter 7 - Threading
I also don't know how to do this :)

Learn how fork() and thread() works

Produce interleavings in the form:
( ) AA BB CC DDEEF1 F2

## Chapter 8a - Addresses and Control Signals
For simple 1 cycle-per-instruction ARM architecture, to determine source1, source2, and destination, just read the instruction.
1. Source1 is always the x in [x, 20]
2. Source2 is where it is getting the data from
3. Destination is where it's going

The instruction str x7, [x6, 20] will produce control signals. See table. 

|                               | Reg2Sel | Src2Sel | ALUop                         | WriteMem | ReadMem | WriteSel | WriteReg | Branch | Jump |
| ----------------------------- | ------- | ------- | ----------------------------- | -------- | ------- | -------- | -------- | ------ | ---- |
| Register-register arithmetic  | 0       | 0       | Add, subtract, multiply, etc. | 0        | 0       | 1        | 1        | 0      | 0    |
| Register-immediate arithmetic | x       | 1       | Add, subtract, multiply, etc. | 0        | 0       | 1        | 1        | 0      | 0    |
| ldr                           | x       | 1       | Add                           | 0        | 1       | 0        | 1        | 0      | 0    |
| str                           | 1       | 1       | Add                           | 1        | 0       | x        | 0        | 0      | 0    |
| cmp                           | 0       | 0       | Subtract                      | 0        | 0       | x        | 0        | 0      | 0    |
| beq                           | x       | x       | x                             | 0        | 0       | x        | 0        | 1      | 0    |
| br /<br>blr / ret             | x       | x       | x                             | 0        | 0       | x        | 0        | 0      | 1    |
- `0`: Signal is inactive.
- `1`: Signal is active.
- `2`: Signal depends on specific conditions.
- `x`: Signal is a "don't care" (unused for this instruction).

When branching, after finishing the branch instruction it will return to the PC + address offset for the next instruction. The address offset is instructions * 4 because each instruction is 4 bytes. You take the immediate field after instruction encoding and multiply it by 4 then add it do PC address
$$\text{next instruction address}=PC\ Address+(Immediate\ Field)(0x4)$$

If we're not branching, then
$$\text{next instruction address}=PC\ Address + 0x4$$
Each instruction is just 4 bytes

ARM processors testq performs an and operation

## Chapter 8b - Hazards and Latency
$$GIPS=\frac{1000}{min\ clock\ cycle}$$
$$min\ clock\ cycle=longest\ propagation\ delay+register\ delay$$
$$throughput_{(in\ GIPS)}=\frac{1000}{min\ clock\ cycle}$$
$$latency=min\ clock\ cycle*number\ of\ stages$$

For hazards:
A data hazard is when one of the sources for an ALU operation is the result of an earlier instruction. This requires a data dependency. So is a RAW
A read-after-write, or RAW, dependencies is when we must ensure that the value read is the value written
To find a RAW hazard:
1. Find operations that write then access data (will need two instructions most likely)
2. Is the address the first operation writes to the address the second operation reads from? Than hazard

| Instruction        | Instruction Frequency | Condition Frequency | Bubbles (stall/flush) | Average Penalty |
| ------------------ | --------------------- | ------------------- | --------------------- | --------------- |
| Load               | $x_1$                 | $y_1$               | $z_1$                 | $x_1*y_1*z_1$   |
| Conditional Branch | $x_2$                 | $y_2=1-accuracy$    | $z_2$                 | $x_2*y_2*z_2$   |
| Return             | $x_3$                 | $y_3$               | $z_3$                 | $x_3*y_3*z_3$   |
|                    |                       |                     | Total Penalty         | sum             |
$$CPI=1.0+load\ penalty+misprediction\ penalty+return\ penalty$$

## Chapter 9 - Exception Flow
Synchronous exceptions:
- Trap : Intentional
- Fault : Unintentional, possibly recoverable
- Abort : Unintentional, not recoverable

Context switches:
- All of the old process’s registers are saved to memory, and all of the new process’s registers are restored from memory.
- There is no direct way for a process to determine if or when it has experienced a context switch

After an interrupt handler finishes control always returns to the application’s next instruction, as though nothing had happened.

## Chapter 10 - Caching
| $2^n$ | $\log_2(2^n)$ |
| ----- | ------------- |
| 1     | 0             |
| 2     | 1             |
| 4     | 2             |
| 8     | 3             |
| 16    | 4             |
| 32    | 5             |
| 64    | 6             |

To calculate average bubbles per instruction, it's:
bubbles per success x success rate + bubbles per fail x fail rate

In general, a cache’s organization can be described by three characteristics:
1. S = num rows. The number of set bits, $\log_2(S)$
2. The number of lines per set (E) aka whatever the x-way is
3. B = num bytes per block or like 64-byte blocks. The number of bits of a block = $\log_2(B)$
The cache size is S(in bytes)×E×B(in bytes). Given a lot of this info usually
![[Pasted image 20241218122646.png]]

Block offset bits, where B is the number of columns:
$$b=\log_2B$$
Set index bits, where S is the number of rows:
$$s=\log_2S$$
The tag bits, where w is the memory address in bits. Everything else basically:
$$t=w-s-b$$Convert the base address to binary, section off the bits according to the sizes you just calculated, convert bits to hex
1. Does the tag at row s match the t you just calculated?
	1. If yes:
		1. Is valid? -> Hit
		2. Else -> Miss
	2. If no: -> Miss
2 way just check both tag columns
To find the value of a hit, the value will be located a row t col b (tag and block offset)

Example:
0x2974
0010 1001 0111 0100
b = log 8 = 3
s = log 16 = 4

| Form   | t           | s     | b   |
| ------ | ----------- | ----- | --- |
| Binary | 0010 1001 0 | 111 0 | 100 |
| Hex    | 0x52        | 0xE   | 0x4 |
Miss
## Chapter 11a - Attacks
Which of these are actions that the operating system and/or the processor may take to prevent buffer overflow attacks?
- Introduce a randomized stack offset
- Mark some memory segments as non-executable

Which of these are actions that the compiler may take to prevent buffer overflow attacks?
- Introduce stack canaries
- Warn the programmer when their code uses standard functions that do not limit the size of strings

Which of these are actions that you, as a programmer, can do to prevent buffer overflows?
- Use functions that limit the size of strings
- Use a programming language that allows unlimited string length
- Use a programming language that does not allow access beyond a string’s bounds

Return-Oriented Programming involves placing the return address of an existing function onto the stack -> FALSE