## Interrupts and Exceptions
When an <mark style="background: #ADCCFFA6;">exception</mark> occurs, control is transferred from the user-level process to the OS kernel. The OS kernel handles the exception and then, depending on the exception, will do one of three things. It may return control to the user-level process at the instruction it was on when the exception occurred; it may return control to the process at the instruction immediately after the one it was on when the instruction occurred, or it may terminate the process
![[Pasted image 20241113161259.png]]

Some exceptions are <mark style="background: #ADCCFFA6;">asynchronous exceptions</mark>, or <mark style="background: #ADCCFFA6;">interrupts</mark>. An interrupt is caused by some event external to the processor and has no relevance to whichever instruction happens to be executing when it occurs

<mark style="background: #ADCCFFA6;">Synchronous exceptions</mark>, on the other hand, are caused by an instruction executed by the user-level process. If the exception is intentional, we call it a <mark style="background: #ADCCFFA6;">trap</mark>. One example of a trap is a system call, such as opening a file. If the exception is unintentional, then it is either an <mark style="background: #ADCCFFA6;">abort</mark> or a <mark style="background: #ADCCFFA6;">fault</mark>
	An abort is an unintentional and unrecoverable exception that must terminate the program, such as an illegal instruction.
	A fault, on the other hand is unintentional but may be recoverable. Despite the name, faults are not always bad things. For example, a _page fault_ (which we’ll discuss in Chapter 10) happens when the virtual memory system needs to retrieve a page of memory that the user-level process needs to access. A page fault would return to the process current instruction after the memory page is available
	Protection faults, such as a _segmentation fault_, tend to be unrecoverable
## Signals
Signals are OS constructs. As part of the kernel handling an exception, it may fire a signal; however, signals may come from other sources as well. Posix-compliant operating systems have a standard set of signals, with corresponding constants defined in <signal.h>. (You can see this list of signals by typing man signal at the command line.) For example, SIGVTALRM corresponds to number 26, as shown in the output of the code example at the start of this chapter; the signal fires after some amount of central processing unit (CPU) time has elapsed for the process. A related signal, SIGALRM, fires after some amount of wall-clock time has elapsed

```C
#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
 
void memory_access_handler( int signal ) ;
 
int main() {
    sigset(SIGSEGV, memory_access_handler);
    int *pointer;
    pointer = 0;
    printf("%d", *pointer);
    return 0;
}
 
void memory_access_handler( int signal ) {
    printf("You tried to access memory you shouldn't. Naughty, naughty!\n");
    exit(1);
}
```

## Context Switches
![[Pasted image 20241113174121.png]]

In many ways, a context switch looks like the OS handling an exception, except that at the end of the context switch, the OS returns control to a _different_ user-level process
![[Pasted image 20241113174204.png]]

## Quiz
![[Pasted image 20241113175624.png]]


![[Pasted image 20241113175635.png]]
![[Pasted image 20241113180804.png]]
Basically just calculate the value of each 32 bit and then convert it to hex
00 1001 110000 1100 11 101 11011
un  a2        f2        a1   f1  a0   f0

pad the 0's
00 1001 110000 1100 000011 0101 011011
2     4         6         4      6           4     6
0x270C0D5B

![[Pasted image 20241113175646.png]]
