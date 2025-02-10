[[x86-64-cheat-sheet.pdf|x86 Cheat Sheet]]

![[Pasted image 20241002123903.png]]

For move instructions telling you to use indexed addressing mode, that just means your mov instruction's source spot will look like `offset(base, index, scale)`, where:
	Offset is if you need an offset (usually can omit)
	Base is where the list starts
	Index is where the index is stored
	Scale is the size of each element in bits (1, 2, 4, 8)
Example: `movzbl	(%rcx, %rdx, 4), %ecx`

Displacement addressing mode usually just means you do `displacement(source)`