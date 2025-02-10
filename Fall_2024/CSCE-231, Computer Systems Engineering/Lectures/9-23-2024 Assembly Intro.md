## Missed slides
![[Pasted image 20240923143550.png]]
![[Pasted image 20240923143608.png]]
![[Pasted image 20240923143744.png]]
![[Pasted image 20240923143908.png]]

## Assembly Data Types
Only integers and floating points
* Ints have sizes of 1, 2, 4, 8 bytes
* Floats have 4, 8, 10, 16 bytes

## Instruction Set Architecture
  Complex Instruction Set Computer (CISC)  
• Driven by limitations of early computers  

Reduced Instruction Set Computer (RISC)  
• Driven by advances in semiconductor technology
![[Pasted image 20240923144041.png]]
![[Pasted image 20240923144124.png]]

## CISC Philosophy
Give programmers what they need

* Retronym for pre-RISC ISAs  
* Common programming actions typically require 1 assembly instruction
	* Many instructions can access memory  Few registers  
* Few registers $\iff$ smaller processor
* Most common instructions require few bytes; rare instructions require more – results in more-compact programs

## x86 Processors
Binary-backwards compatible from 8086. Assembly-backwards compatible from 8080
Added more features as time goes on. Preserved legacy features for backwards-compatibility

![[Pasted image 20240923144402.png]]

![[Pasted image 20240923144443.png]]
They accomplished 32-bit registers using two 16-bit registers. Maintained backwards compatibility

![[Pasted image 20240923144942.png]]
64-bit is just two 32-bits

## x86 Operand Types
<mark style="background: #ADCCFFA6;">Immediate</mark>
* Constant integer value
* Prefixed with $
* Examples: $8, $0x40, $-52

<mark style="background: #ADCCFFA6;">Register</mark>
* One of the 16 "general-purpose" registers
	* Some have particular users
* Very very very fast, can be read in a fraction of a clock cycle
* Examples: %rax, %rsi, %r13
* Evaluates to register's contents: Reg[%r13]

<mark style="background: #ADCCFFA6;">Memory</mark>
* 1, 2, 4, or 8 bytes of consecutive memory
* Address in a register; (parentheses) dereference address
* Various address modes; simplest example is (%rsi)
* Evaluates to memory location's contents: Mem[Reg[%rsi]]
* Very slow, avoid if possible by using registers

## x86 Assembly Code
`movq source, destination` copies data to the destination. Leaves original copy in place
	Example: `movq %rax, (%rbx)` which is equivalent to `*destination = z;` if z was %rax

<mark style="background: #ADCCFFA6;">b</mark> - operate on an 8-bit byte
<mark style="background: #ADCCFFA6;">w</mark> - operate on a 16-bit word
<mark style="background: #ADCCFFA6;">l</mark> - operate on a 32-bit long word
<mark style="background: #ADCCFFA6;">q</mark> - operate on a 64-bit quad word
![[Pasted image 20240923151216.png]]
Note: gcc will promote bytes & words to long words if destination is a register. Why? No idea

![[Pasted image 20240923151515.png]]

## x86 Addressing Modes
* Simple       (R$_b$)       Mem[Reg[Rb]]
	* Register R$_b$ specifies memory address
	* Corresponds to dereferencing a pointer in C
* Displacement    D$_R$      Mem[Reg[Rb] + D]
![[Pasted image 20240923152029.png]]
![[Pasted image 20240923152041.png]]
lol the class ended so i gave up