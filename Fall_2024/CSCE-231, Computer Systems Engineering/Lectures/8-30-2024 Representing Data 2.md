## Binary Conversions
You can use repeated subtraction to convert from decimal to binary. This seems like a pain in the ass so I’m not going to explain it
![[IMG_0153.png]]
You need to know powers of two and no

You can do it with repeated division which is what we learned in Val’s class. Repeatedly divide by 2; going from right to left if it divides evenly by two than put a 0, otherwise put a 1. Keep the remainder of the division
![[IMG_0154.jpeg]]
210 to binary

## Bits to Bytes
A byte is 8 bits. In binary it’s 0b00000000 to 0b11111111. In hex it’s 0x0 to 0xFF. In integers as -128$_{10}$ to 127$_{10}$ or 0-255$_{10}$ if you ignore negatives

![[IMG_0155.jpeg]]

## Memory
![[IMG_0156.jpeg]]
![[IMG_0157.jpeg]]
Little Endian:
* Least significant byte has lowest address
* RISC-V is the cut off one

| Address | Big Endian | Little Endian |
| ------- | ---------- | ------------- |
| 0x1037  | 78         | 12            |
| 0x1036  | 56         | 34            |
| 0x1035  | 34         | 56            |
| 0x1034  | 12         | 78            |
Kind of backwards than what it sounds like. Least significant byte is the smallest one and the lowest address is actually the one with the highest number
	Actually kind of confused on what the least significant byte means?????

If you want to do a <mark style="background: #ADCCFFA6;">disassembly</mark> and reconstruct plain-text assembly code from binary object code, do:
	`objdump -d <filename>`
	-d for disassemble
![[IMG_0158.jpeg]]

