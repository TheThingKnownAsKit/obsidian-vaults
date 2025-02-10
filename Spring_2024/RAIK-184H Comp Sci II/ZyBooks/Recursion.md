# RECURSIVE DEFINITION
The **factorial** function $f(n)=n!$ for $n\ge 0$ can be defined as:
$f(0)=1$
$f(n)=n*f(n-1)$ for $n\ge 1$
This is a recursive definition. In a **recursive definition** of a function, the value of the function is defined in terms of the output value of the function on smaller input values

**Recursion** is the process of computing the value of a function using the result of the function on smaller input values

- A **basis** explicitly states that one or more specific elements are in the set.
- A **recursive rule** shows how to construct additional elements in the set from elements already known to be in the set. (There is often more than one recursive rule).
- An **exclusion statement** states that an element is in the set only if it is given in the basis or can be constructed by applying the recursive rules repeatedly to elements given in the basis.

For perfect binary trees:
A tree has **vertices** (denoted by a circle) and **edges** (denoted by line segments) which connect pairs of vertices. Not every collection of vertices and edges is a tree. A formal definition of trees along with their properties is given elsewhere in this material. Here we give a recursive definition for a particular class of trees called perfect binary trees. Each perfect binary tree has a designated vertex called the **root**
![[Pasted image 20240225154529.png]]

# RECURSIVE ALGORITHMS
A **recursive algorithm** is an algorithm that calls itself
	Calls to itself are **recursive calls**

![[Pasted image 20240225155855.png]]
![[Pasted image 20240225155909.png]]
![[Pasted image 20240225155940.png]]
![[Pasted image 20240225160057.png]]
