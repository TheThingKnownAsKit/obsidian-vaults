A <mark style="background: #ADCCFFA6;">constant time operation</mark> is an operation that, for a given processor, always operates in the same amount of time, regardless of input values
	A group of constant operations can be considered one big constant operation
	Not affected by hardware performance differences
![[Pasted image 20240827140940.png]]

An algorithm with runtime complexity T(N) has a lower bound and an upper bound.
	The <mark style="background: #ADCCFFA6;">lower bound</mark>: A function f(N) that is $\le$ the best case T(N), for all values of N $\ge$ 1.
	The <mark style="background: #ADCCFFA6;">upper bound</mark>: A function f(N) that is $\ge$ the worst case T(N). for all values of N $\ge$ 1.
For example, if an algorithm's best case runtime is T(N) = 5N + 4, then subtracting any nonnegative integer yields a lower bound. Therefore, <mark style="background: #BBFABBA6;">two additional criteria are commonly used to choose a preferred upper or lower bound.</mark>
	The <mark style="background: #ADCCFFA6;">preferred bound</mark>: 1. is a single-term polynomial and 2. bounds T(N) as tightly as possible
![[Pasted image 20240827141541.png]]
<mark style="background: #BBFABBA6;">It kinda looks like for the lower bound you just take the best case and remove everything but the first term. For the lower bound, you find out what the worst case runtime equation is when N = 1</mark> ($3(1)^2+10(1)+17=30$), so the upper bound is $30N^2$ instead. Remember to check the greater than/less than test to make sure it satisfies it 

<mark style="background: #ADCCFFA6;">Asymptotic notation</mark> is the classification of runtime complexity that uses functions that indicate only the growth rate of a bounding function. Basically it just gets rid of the constant in front of the N term, so instead of it being $30N^2$ it'll just be $N^2$
	<mark style="background: #ADCCFFA6;">O notation</mark> provides a growth rate for an algorithm's upper bound
	$\Omega$ <mark style="background: #ADCCFFA6;">notation</mark> provides a growth rate for an algorithm's lower bound
	$\Theta$ <mark style="background: #ADCCFFA6;">notation</mark> provides a growth rate for an algorithm's upper and lower bound
![[Pasted image 20240827142953.png]]

<mark style="background: #ADCCFFA6;">Big O notation</mark> is a mathematical way of describing how a function's runtime generally behaves in relation to the input size. All functions have the same growth rate (determined by highest order term of the function) are characterized using the same Big O notation
	Rule 1: If f(N) is a sum of several terms, the highest order term is kept and others are discarded
	Rule 2: If f(N) has a term that is a product of several factors, all constants are omitted
<mark style="background: #BBFABBA6;">Basically take the algorithm steps, apply the two rules which just means simplify, boom you're done</mark>. It's like taking the limit, only the biggest term matters and all constants are omitted
![[Pasted image 20240827143530.png]]
Bases of logs are omitted since they are just constant multiples of each other. $5\log_{10}N$ simplifies to $\log N$

![[Pasted image 20240827143801.png]]
![[Pasted image 20240827143835.png]]
