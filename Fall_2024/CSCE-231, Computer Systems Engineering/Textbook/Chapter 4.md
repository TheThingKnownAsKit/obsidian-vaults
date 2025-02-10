## ACTUALLY HELPFUL NOTES FROM HW AND LAB
### Binary Fixed-Point and Binary Scientific Notation
To convert from fixed-point form to decimal, calculate the binary value of above the ., that is the whole number. Then, calculate the binary value of below the . and divide it by $2^{NumOfBits}$
	Example: 110.111 in binary to decimal
	110 is 6 in binary
	111 is 7 in binary
	there are 3 spaces after the ., which is 2^3 which is 8, so 7/8 = 0.875
	Answer: 6 and 7/8ths or 6.875

The bias is $2^{w-1}-1$ where w is the number of bits in the exponent field (usually 7 bias)

When converting from a binary fixed-point value to floating point format, you just shift it until it's in the form 1.xxxxx with the 2 exponent being how many places the . had to move
		NOTE: FROM BFP TO SCIENTIFIC
	![[Pasted image 20240924114648 1.png]]
	positive means it moved to the left, negative means it moved to the right

---

GETTING VALUE FROM FLOATING POINT OR BINARY POINT FORM:
Usually has 1 bit for sign, 4 bits for exponent, and 3 bits for fraction with a bias of 7

From floating to binary:
1. Normalize if it isnt already (so it's in form 1.xxxxx)
2. The first bit will be the sign
3. Take the exponent of the 2 and ADD the bias to it to get the value
5. Calculate the fractional value to get its value using above methods
Note: If you are asked for any of these values in binary, just convert from decimal to binary. Usually if it wants the whole number as binary the first bit will be the sign value, the next 4 will be the exp value, and the last 3 will be the frac
	The frac is usually whatever it was in floating form
Example: Convert -1.011 x 2^2 to binary
1. first bit is 1 from the negative sign
2. 2 is the exponent, 2 + 7 = 9, 9 in binary is 1001
3. Last 3 bits are 011
4. Answer is 1100 1011

From floating to decimal:
1. Sign bit: Is it pos/neg?
2. Fraction bits: Sum everything to the right of the decimal point with decreasing negative exponents. Example: 2^-1 + 2^-2 + 2^-3
3. Exponent bits: Calculate the exponent value of 2^E
4. Multiply frac by exp and apply sign
Note: If in binary, convert it to floating just to make your life easier because remember the bias in exp
Example: What is the value of 1.101 x 2^4 in decimal?
1. Not negative
2. To get frac: 2^-1 + 2^-3 = 1.625
3. 2^4 is 16
4. 16 x 1.625 = 26 (not negative)

From binary point form to decimal:
1. The sign field is the leftmost bit (-/+)
2. The exp value is just the decimal value of the binary PLUS the bias
3. The fraction field is just that binary in decimal / 2^number of bits

From binary to floating:
1. First bit is sign
2. Next bits are the exponent. Convert to decimal and SUBTRACT the bias
3. The last bits are the fraction
Will follow the form: (sign)1.frac x 2^{exp}
	Example: 0100 0111 is 1.111 x 2^1 

### Arithmetic


## Fixed-Point Numbers
A <mark style="background: #ADCCFFA6;">fixed-point number</mark> is a number representation in which the binary point (decimal point) is always a certain number of positions from the lSB
	Always 3 places from LSB in an 8-bit number
	The binary point works just like regular binary calculations, the exponent is just negative past the point

## Rational Numbers
Representing values as rational numbers is when you store it as a numerator/denominator pair. This allows very large numbers (with small denominators) and very small numbers (with large denominators)

## Floating-Point Numbers
<mark style="background: #ADCCFFA6;">Floating-point numbers</mark> are very similar to scientific notation. It consists of a number, called the <mark style="background: #ADCCFFA6;">significand</mark>, that is multiplied by the <mark style="background: #ADCCFFA6;">radix</mark> raised to the power of some exponent

![[Pasted image 20240915151028.png]]
The numbers are the significand, the 2 is the radix

<mark style="background: #ADCCFFA6;">Normal form</mark> is an encoding of scientific notation that the vast majority of floating-point values are represented in
$\pm m*2^e=(-1)^S*1.T*2^e$
	Where m is the significand, b is the radix, and e is the exponent that specifies the numbers magnitude (distance and direction of floating point). T is the fractional portion of the significand
![[Pasted image 20240915151608.png]]

The <mark style="background: #ADCCFFA6;">IEEE 754</mark> standard places these values in a bit field with three subfields. the triple
![[Pasted image 20240915151703.png]]
![[Pasted image 20240915151731.png]]

![[Pasted image 20240915151744.png]]

## Rounding
IEEE 754 defines five rounding modes; the default for rounding ties between modes is to round to the nearest even value

## Subnormal Numbers
![[Pasted image 20240915153431.png]]

## Special Values
![[Pasted image 20240915153737.png]]

## Floating-Point Arithmetic
### Multiplication and Division
![[Pasted image 20240915154039.png]]

![[Pasted image 20240915154054.png]]

### Addition and Subtraction
![[Pasted image 20240915154121.png]]
## Type Casting
![[Pasted image 20240915154331.png]]