## Solutions
### Phase 1: String password
The password is "Premature optimization is the root of all evil."

### Phase 2: 6 digit password
Takes input
Pushes %rbx onto stack (rbx is a caller owner whatever that means)
	Always has -34 in if x/d
	If x/s, then ![[Pasted image 20241009132435.png]]

0x20 in hex is 32 in decimal

read_six_numbers is just making sure it's in format %d %d %d %d %d %d

1. Pushes argument onto stack and subtracts 0x20
2. Moves it into the 2nd argument position (rsi)
3. Checks to see if it's in form %d %d %d %d %d %d
4. Sets eax to 1, sets eax to 1 + entered
5. Checks to see if eax is equal 

Adding the index (starting at 1) to previous number value

1 2 4 7 11 16

### Phase 3: Switch statement
Switch statement with 2 numbers

First number (saved in rcx) depends on input of second number (saved in rdx)

eax depends on 1st input
rsp is 18 minus 2nd input 

trying to get eax and rsp to match

(independent of 2nd input)
1 -> eax is 738
2 -> eax is 330
3 -> eax is 465
4 -> eax is 147
5 -> eax is 310
6 -> eax is 748
7 -> eax is 328

being stupid literally just do any of those pairs, so 1 738

### Phase 4: Recursion
Takes in two numbers in %d %d format
First num has to be <= 14
No constraint on second

Essentially, you pass in two nums and the result of a recursive loop have to result in 35 (0x23)

Passes 2nd num, 0, and 14 into func4
Func4 calls trying 14:
1. 14, 0, 14

After processing, first num should also be 35

Honestly you could follow all the func4 instructions and find the right number but just trial and error 0-14 like a normal person

It's 8 35

### Phase 5: Lookup table
Has to be a string of length 6

For every character, it does a bitwise & with 0xf (this just indexes it per character in lookup table I think)
Uses this to look up a value in a predefined array at 0x402980
![[Pasted image 20241023210743.png]]
Result stored in local array

Compares the local array result with a string located at 0x402438 ("oilers")
Strings have to be equal

Apply lookup table above and & 0xf

"JDOEFG"
### Phase 6: Linked list
%d %d %d %d %d %d

Input a series of 6 numbers. They should be:
	Between 1 and 6
	Unique
	In descending order - NOTE

Sets each number equal to 7 - number

Puts into linked list
Checks to see if in descending order

5 = 363
4 = 305
1 = 230
2 = 174
3 = 127

Basically descending order from the VALUE AT THE NODE, not the node index

6 5 4 1 2 3

## Notes
layout asm to see assembly code
break explode_bomb

set step-mode
n for next, s for step (step steps INTO function, n goes to next line)

To access memory: x/d to see as digit or x/s for string (dereferences memory stuff)
P to see value of memory address
(Follow by $)

![[Pasted image 20241009124934.png]]

k to kill program

Once debugged a phase, do c to continue to next breakpoint (break every phase)

info breakpoint

r answers.txt

gdb bomb

4 is recursive function