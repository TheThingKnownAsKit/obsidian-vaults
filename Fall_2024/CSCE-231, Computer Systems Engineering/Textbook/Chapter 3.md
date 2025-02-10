## ACTUALLY HELPFUL OVERFLOW INFO
<mark style="background: #BBFABBA6;">For unsigned integers: </mark>
If and only if the carry-out from adding the most significant bit is 1, overflow occurred
![[Pasted image 20240903173906.png]]

<mark style="background: #BBFABBA6;">WITH SIGNED:</mark>
1. If you add two positive numbers together and the result is negative, it overflowed. Vice versa with positive
2. Procedurally, you can compare the MSB carry-in and carry-out value.
	1. If one of these bits is 1 and the other is 0, overflow occurred
	2. If they're both 1 or both 0 then overflow did not occur
![[Pasted image 20240914143913.png]]


OKAY BASICALLY
The <mark style="background: #ADCCFFA6;">Most significant bit (MSB)</mark> is just the leftmost one, and the <mark style="background: #ADCCFFA6;">least significant bit (LSB)</mark> is the rightmost

## Integers
### Unsigned
<mark style="background: #ADCCFFA6;">Unsigned integers</mark> are exactly what it sounds like. Can only be 0 or positive
![[Pasted image 20240903171858.png]]

NOTE: If you want to use an unsigned integer, you have to explicitly tell the compiler to do so using the keyword unsigned
![[Pasted image 20240903172113.png]]

### Signed
You can represent a signed integer using <mark style="background: #ADCCFFA6;">two's complement</mark> to 1. determine pos/neg quickly 2. addition works as expected and 3. the same hardware works for signed and unsigned

Essentially, the MSB carries a pos/neg weight. Learned this in Val's class. If the MSB is 1 than it's negative, otherwise positive

![[Pasted image 20240914143443.png]]
![[Pasted image 20240914143502.png]]

## Binary Arithmetic
For each bit-position, add the bits from the two operands along with anything carried from the previous bit-position. Keep the LSB and carry the most significant bit (if there is one) to the next bit-position
![[Pasted image 20240903172537.png]]

![[Pasted image 20240903172609.png]]

It works the same in hex except you're usually carrying over more than just 1. If you add 0xD + 0xA your answer should be 0x17

### Hardware Implementation
Addition in the hardware can be done with the 1-bit full adder
![[Pasted image 20240903172920.png]]

![[Pasted image 20240903172942.png]]
This is a <mark style="background: #ADCCFFA6;">ripple-carry adder</mark>. It's simple and easy to implement and mimics the addition technique of carrying over. It is slow though

The <mark style="background: #ADCCFFA6;">carry-lookahead adder</mark> is able to compute all of the sum bits and all of the carry bits in parallel with each other, making it much much faster. The speed of computation is independent from the size of the integers. It is more complex and won't be discussed in detail

Most engineers create a <mark style="background: #ADCCFFA6;">hybrid adder</mark>. For example, they'd create a 4 or 8 bit carry-lookahead adder, and than chain those together in ripple-carry fashion

### Integer Overflow
When you add two integers n-bit integers together, the result may require n + 1 bits to store. Integers have fixed storage, so the excess high-significance bit will be truncated, and the computer will report a different value than you expected. This is <mark style="background: #ADCCFFA6;">overflow</mark>
![[Pasted image 20240915133231.png]]

It's less of a number line and more of a number circle. Remember if you hit the integer limit than it'll wrap back around to -2 billion or whatever it is

Two ways to detect this with unsigned:
1. If the sum is less than either of the operands, it overflowed
2. If the COMPUTER needs to detect overflow, than use: if and only if the carry-out from adding the most significant bit is 1, overflow occurred
![[Pasted image 20240903173906.png]]

WITH SIGNED:
1. If you add two positive numbers together and the result is negative, it overflowed. Vice versa with positive
2. Procedurally, you can compare the MSB carry-in ad carry-out value.
	1. If one of these bits is 1 and the other is 0, overflow occurred
	2. If they're both 1 or both 0 then overflow did not occur
![[Pasted image 20240914143913.png]]

## Subtraction
A - B = A + (-B) is the same as A + ~B. You basically just complement the second number. add 1, and add them because fuck subtraction

Overflow happens if the MSB carry out value is 0 (flipped from 1 for actual adding)

## Multiplication
```
result = 0;
for (i = 0; i < multiplier; i++)
	result += multiplicand;
```
Simple implementation but also sucks because it's slow

Instead be cool and smart and use compiler tricks to do it faster

First, remember that you can multiply by 2 simply by placing a 0 to the right of the LSB (left shift)
$x * 2^{m}= x << m$
Next remember that multiplication is distributive (you can break up numbers into multiples of common denominators)
Lastly remember that every number in binary is a power of two, so you can just break numbers into left shifts like a big brain

The load effective address instruction can take a value in a register, multiply it by 1, 2, 4, or 8, and then add that to another value in another register:
```C
leaq (Rb, Ri, S), Rd
```
Where it computes Rb + S * Ri and stores it in Rd

Full multiplication:
![[Pasted image 20240915133512.png]]
## Division
![[Pasted image 20240915133816.png]]

## Type Casting
Small to big type is relatively seamless, big to small usually misrepresents the data and stuff because bits get cut off