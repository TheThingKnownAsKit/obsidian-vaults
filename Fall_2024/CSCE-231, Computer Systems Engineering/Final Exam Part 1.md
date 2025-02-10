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

## Chapter 8.1 - Addresses and Control Signals
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

## Chapter 8.2 - Hazards and Latency
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
