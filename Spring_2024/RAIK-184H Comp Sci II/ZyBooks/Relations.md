# INTRODUCTION TO BINARY RELATIONS
Mathematically, a **binary relation** between two sets A and B is a subset R of A x B. The term binary refers to the fact that the relation is a subset of the Cartesian product of two sets
	Conditional sets basically. aRx if x is an integer multiple of a, true for 2R2, not NOTE true for 4R8

**Arrow diagram**
![[Pasted image 20240331195834.png]]

**Matrix representation**
![[Pasted image 20240331195921.png]]

![[Pasted image 20240331200115.png]]

# PROPERTIES OF BINARY RELATIONS
## Reflexive and Anti-Reflexive
A relation is **reflexive** if and only if for every $x\epsilon A$, then $xRx$, Every element in the set must be related to itself. Every point is a self loop

A relation is **anti-reflexive** if and only if for every x in the domain of R, it is not true that xRx. Every element in the set must not be related to itself. Every point is not a self loop
![[Pasted image 20240331200815.png]]
Can be neither reflexive nor anti reflexive by having some but not all self loops
![[Pasted image 20240331200957.png]]

## Symmetric and Anti-Symmetric
A relation is **symmetric** if and only if for every pair, x and y, $y\epsilon A$, $xRy$ if and only if yRx. A relation is symmetric if for every pair of elements x and y in the domain, one of the following situations holds:
* xRy and yRx are both true
* Neither xRy nor yRx is true
Basically you could switch the x and y and it'd solve the same
![[Pasted image 20240331201348.png]]
![[Pasted image 20240331201416.png]]

A relation is **anti-symmetric** if and only if for every pair, x and y$\epsilon$A, if x$\ne$y then it can not be the case that xRy and yRx are both true. It holds if:
- xRy, but it is not true that yRx
- yRx, but it is not true that xRy
- Neither xRy nor yRx is true
![[Pasted image 20240331201621.png]]![[Pasted image 20240331201649.png]]
NOTE: When talking about symmetry, self-reference/loops is always ignored. X should never be itself

## Transitive
A relation is **transitive** if and only if for every three elements, x, y, z $\epsilon$ A, if xRy and yRz, then it must also be the case that xRz
![[Pasted image 20240331201853.png]]

MORE TRIANGLES WHY ALWAYS TRIANGLES
Pythagorean Theorem of discrete math
# DIRECTED GRAPHS, PATHS, AND CYCLES
![[Pasted image 20240331202517.png]]

![[Pasted image 20240331202602.png]]

![[Pasted image 20240331202700.png]]

# COMPOSITION OF RELATIONS
![[Pasted image 20240331202956.png]]
![[Pasted image 20240331202902.png]]
