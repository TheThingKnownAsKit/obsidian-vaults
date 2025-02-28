A <mark style="background: #ADCCFFA6;">binary coded decimal</mark> is literally just a decimal number in binary????? Why is he rambling????
It uses four bits per decimal value to make it easier to read. Complicated math nonsense

Base 16 [0 1 2 3 4 5 6 7 8 9 A B C D E F]
Slightly more human readable, mostly used to make binary more readable so no one actually cares about it as a base
Each hex digit is four bits and you need two hex digits to represent a byte

In C hex’s always begin with 0x

Hex to binary:
1. Replace hex-digit with corresponding four bits (so helpful)
Binary to hex:
1. Separate bits into quartets 
2. Replace each quartet with corresponding hex-digit
Or just make the table. Write out decimal and hex, then just remember to carry the 1 over after adding 1 to the four binary digits

Remember decimal is just 1 or 0 * 2^place in descending order