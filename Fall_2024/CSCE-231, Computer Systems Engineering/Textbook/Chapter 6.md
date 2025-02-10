## Procedural Programming
### The Program Stack
The <mark style="background: #ADCCFFA6;">program stack</mark> exhibits last-in first-out behavior. When we are taught about stack data structures, we are often given the analogy of a physical stack, which grows and shrinks from the top, as in a stack of plates. The program stack is generally at the high end of memory, <mark style="background: #BBFABBA6;">growing “downward” like a stalactite toward lower addresses: when we push something onto the stack, the address stored in the stack pointer becomes a lesser address; when we pop something off of the stack, the address stored in the stack pointer becomes a greater address</mark>.
![[Pasted image 20241023160612.png]]

Organized into <mark style="background: #ADCCFFA6;">stack frames</mark> (also known as activation frames). A stack frame is a both a working space in memory for a function and also a record of the state of the function when it calls another function. Contains:
* Arguments for the function
* If there were too many arguments for registers available
* The return address to the called function
* any registers the function needs to save between calls
* Any locally declared structures, arrays, or pointers

<mark style="background: #ADCCFFA6;">Stack pointer</mark> points at top of stack. Allocating/access space on the stack is just offsetting the stack pointer
![[Pasted image 20241023162016.png]]

### Calling a Function
The <mark style="background: #ADCCFFA6;">callee</mark> is the called function
The <mark style="background: #ADCCFFA6;">caller</mark> is the function who called the callee
After a callee is invoked, the results are available for the caller to use

![[Pasted image 20241023162302.png]]

Some registers are <mark style="background: #ADCCFFA6;">caller-saved registers</mark>, which means that if the calling function wants to use the contents of the registers after the function call, it must save them on the stack
Other registers are <mark style="background: #ADCCFFA6;">callee-saved registers</mark>, which means that the calling function is guaranteed that they will still hold their values after the function returns

![[Pasted image 20241023162420.png]]

### Returning From a Function
Use ret to return in x86





## Quiz
![[Pasted image 20241023170614.png]]
![[Pasted image 20241023170628.png]]
![[Pasted image 20241023170641.png]]
![[Pasted image 20241023170654.png]]
![[Pasted image 20241023170706.png]]
![[Pasted image 20241023170721.png]]
![[Pasted image 20241023170732.png]]
![[Pasted image 20241023170747.png]]
![[Pasted image 20241023170758.png]]
![[Pasted image 20241023170809.png]]
![[Pasted image 20241023170819.png]]
![[Pasted image 20241023170832.png]]
