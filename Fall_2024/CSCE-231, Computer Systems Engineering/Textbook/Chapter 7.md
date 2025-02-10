## Why/What Concurrency
When there are multiple computations at the same time, we say that the computations are <mark style="background: #ADCCFFA6;">concurrent</mark>. Generally speaking, there are three reasons that programmers use concurrency
1. To use <mark style="background: #ADCCFFA6;">parallel programming</mark> to make a program run faster by dividing up the work to multiple threads
2. Responsiveness as in reducing the amount of time that some computation has to wait for resources to be available
3. The problem/function being solved has inherent concurrency built into it

## Parallel Programming
Inherently sequential programs cannot have concurrency no matter how much you cry
<mark style="background: #ADCCFFA6;">Embarrassingly parallel</mark> is when, given enough processors, we could perform every computation at the same time as every other computation

Shared memory nonsense doesn't seem important I already took the test

## Interleaving
<mark style="background: #ADCCFFA6;">Interleaving</mark> is the process of lining up two concurrent processes and writing out all the possible ways it can be executed. Things in the same column can happen in any order but you cannot skip columns before all of them have been executed
	A <mark style="background: #ADCCFFA6;">valid interleaving</mark> is an interleaving that preserves the correct ordering from each flow of control
	An <mark style="background: #ADCCFFA6;">invalid interleaving</mark> is one that does not preserve the correct ordering from each flow of control
	![[Pasted image 20241108160536.png]]

When the correctness of a concurrent algorithm relies on some valid interleaving's not happening, this is called a <mark style="background: #ADCCFFA6;">race condition</mark> because there is a race for certain events to occur before some other event occurs

## Process-Based Concurrency
To create a new process, we use the <mark style="background: #ADCCFFA6;">fork()</mark> function, which requires that we include the unistd.h header. The fork() function will create an almost-identical copy of the process that had called the fork() function
	The <mark style="background: #ADCCFFA6;">parent</mark> process (which called the command) retains its full context and its full memory space
	The <mark style="background: #ADCCFFA6;">child</mark> process gets a full copy of its parent’s context and a full copy of its parent’s memory space
	The parent retains its original process ID, and the child gets a new process ID.The _only_ difference between the parent and the child is the value returned by fork()

## Thread-Based Concurrency
A <mark style="background: #ADCCFFA6;">thread</mark> is sometimes called a _lightweight process_. Unlike a heavyweight process, a thread is not a true process: if you run top or ps, you won’t see individual threads listed; instead, you’ll only see the process that contains the thread. <mark style="background: #BBFABBA6;">Instead, a thread is a separate control flow within a process</mark>
- Occupies the same memory, it just creates a new context to run in
![[Pasted image 20241108161132.png]]

Use <mark style="background: #ADCCFFA6;">pthread()</mark>

## Preventing Races
The pthreads library has a built-in _mutual exclusion_ mechanism, commonly called a <mark style="background: #ADCCFFA6;">mutex</mark>. A mutex is a shared variable that a thread can hold mutually-exclusive of other threads; that is, only one thread can access the mutex at any given time
	Locks and unlocks code / variables so concurrency doesn't operate out of order

If things are locked in a way that no thread is able to progress, this is a <mark style="background: #ADCCFFA6;">livelock</mark>
During <mark style="background: #ADCCFFA6;">starvation</mark>, a thread is never able to attain enough resources to progress