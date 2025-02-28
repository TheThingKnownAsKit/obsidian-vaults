![[Pasted image 20240829135635.png]]

## Working With Bits in C
C supports changing bits using <mark style="background: #ADCCFFA6;">bitwise</mark> operations. These are Boolean operations that operate on <mark style="background: #ADCCFFA6;">bit vectors</mark>, also known as bit strings

A bit vector is a sequence of bits starting at 0 <mark style="background: #BBFABBA6;">AND READING RIGHT TO LEFT</mark>. For example, the bit vector A = [1, 1, 0, 0]. then bit a0 = 0, bit a1 = 0, bit a2 = 1, and bit a3 = 1

### Bitwise Operators
<mark style="background: #ADCCFFA6;">Bitwise complement</mark>, also known as bitwise NOT, takes a single argument. The operator in C is tilde: ~. It inverts the bit

<mark style="background: #ADCCFFA6;">Bitwise AND</mark> takes two arguments; the operator in C is a single ampersand: &. Each bit in the first operand is ANDed with the corresponding bit in the second operand. Example:
	If you have the operation C = D & E
	D = 0x3C and E = 0xA6 (in hex)
	D = 0011 1100
	E = 1010 0110 then if you do & for each bit you need both to be 1's or it's 0 so
	C = 0010 0100

<mark style="background: #ADCCFFA6;">Bitwise OR</mark> takes two arguments; the operator in C is a single vertical bar |. Same thing as AND but it OR's it

<mark style="background: #ADCCFFA6;">Bitwise exclusive OR</mark> or bitwise XOR takes two arguments; the operator in C is a carat ^. Same as AND and OR but it's XOR

<mark style="background: #ADCCFFA6;">Left shift</mark> takes two arguments, and the C operator is a double left angle bracket: <<. The first argument is the bit vector to be shifted, and the second argument is how far to shift the bits. It is "moving" all bits to the left by some number of shifts. The leftmost bits that shift out of the bit vector are discarded, and the 0s are shifted in to the right-hand side
![[Pasted image 20240829142849.png]]

<mark style="background: #ADCCFFA6;">Right shift</mark> also takes two arguments, and the C operator is a double right angle bracket: >>. It shifts the same as left but to the right
	In a <mark style="background: #ADCCFFA6;">logical right shift</mark>. the fill-bits are always 0s
	In an <mark style="background: #ADCCFFA6;">arithmetic right shift</mark>, the fill-bits duplicate the original leftmost bit
![[Pasted image 20240829143033.png]]
The reason there's two types of right shifts is that sometimes the leftmost bit is treated as a sign bit and can be quickly checked to see if its positive or negative

### Common Idioms
When examining bits, you usually only care about some of them and not all of them. A <mark style="background: #ADCCFFA6;">bitmask</mark> puts 1s in bit positions you are interested in examining and 0s everyplace else. You then apply the bitwise AND operation to the integer containing the bits with the bitmask. The result will have 0s in every bit position except the bits of interest, and the bits of interest will be persevered with their original 0/1 values

If you examine only one bit, you can treat it as true/false. If bit == 1, than do a thing

<mark style="background: #ADCCFFA6;">Constructing bit vectors</mark>
![[Pasted image 20240829143747.png]]

<mark style="background: #ADCCFFA6;">Assigning bits</mark>
![[Pasted image 20240829143802.png]]

## Logic Gates
For every operation in programs, bits must be manipulated in hardware. This is done with <mark style="background: #ADCCFFA6;">logic gates</mark>. They are showed with the inputs on the left and outputs on the right for simplicity 

The <mark style="background: #ADCCFFA6;">inverter</mark>, also known as a NOT gate. Figures are all shown here. The final three gates are the NAND gate (NOT AND), the NOR gate (NOT OR), and the XNOR gate (NOT XOR); which are logically equivalent to passing the output of an AND/OR/XOR gate through an inverter
![[Pasted image 20240829144002.png]]

These gates are shown operate on one pair of bits (or one bit in the case of the inverter). To perform bitwise operations on an n-bit bit vector (typically called a <mark style="background: #ADCCFFA6;">bus</mark> at the hardware level) would require n gates. Shorthand says we can show n bits at each input/output of the gate to imply applying the operation bitwise to busses
![[Pasted image 20240829144244.png]]

The <mark style="background: #ADCCFFA6;">multiplexor</mark> or mux is essentially a switch. The *select* bit(s) are used to determine which input bit is passed through to the output. If sel=0x0 then the output is the 0th input; if sel=0x1 then the output is the 1st input and so on. Generally, out = in$_{sel}$
	Kinda like an array of inputs and sel is which index to choose from
	A mux is a collection of logic gates essentially
![[Pasted image 20240829144449.png]]
There isn't one diagram for this but here's one
![[Pasted image 20240829144531.png]]