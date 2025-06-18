![[7-Determinants-COMPLETE.pdf]]

## The Determinant
For every square n x n matrix A we want to assign a scalar, called the <mark style="background: #ADCCFFA6;">determinant</mark> of A, denoted by $\det(A)$ that satisfies
$$\det(A)=0\Leftrightarrow \text{A is not invertible (singular)}$$
$$\det(A)\ne0\Leftrightarrow \text{A is invertible (non-singular)}$$
Basically the determinant is the measure of if a matrix is invertible or not. <mark style="background: #BBFABBA6;">It is a bit of an arbitrary number that is only important because you can infer a lot of things from it</mark>
1. If it is not 0, the matrix is invertible
2. It can kinda sorta represent the area/volume a matrix takes up (depending on circumstances)
3. It represents a value you can multiply the inverse of a matrix of to get the original matrix
4. If a matrix is invertible (the determinant != 0), then it's columns are independent (only for square matrices)
5. $\det A^T=\det(A)$
6. The determinant of an identity matrix is 1
7. A matrix is <mark style="background: #ADCCFFA6;">block traingular</mark> if one of the quadrants of a 4 x 4 matrix is 0, eg $\begin{bmatrix}A & C \\ 0 & B\end{bmatrix}$ where A, C, and B are matrices and 0 is the zero matrix. The determinant of this is $\det A*\det B$

![[Pasted image 20250415205721.png]]
![[Pasted image 20250415205731.png]]
![[Pasted image 20250415205740.png]]
![[Pasted image 20250415205751.png]]
![[Pasted image 20250416125227.png]]

Again, really illustrating that the determinant doesn't really mean anything in a way that is useful for non-math majors. It is just a useful number that represents a lot of information

## Finding the Determinant
<mark style="background: #BBFABBA6;">FOR A 1 x 1 MATRIX</mark>
For a 1 x 1 matrix (a scalar), $A=[a]$, the determinant is just a, so $\det(A)=a$. Very simple. Notice that as long as a != 0, $a^{-1}=\frac{1}{a}$

<mark style="background: #BBFABBA6;">FOR A 2 x 2 MATRIX</mark>
If $A=\begin{bmatrix}a & b \\ c & d\end{bmatrix}$ is a 2 x 2 matrix, we define $\det(A)=ad-bc$
Recall and notice that if the matrix is invertible, then $A^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d & -b \\ -c & a\end{bmatrix}$
So, $\frac{1}{\det(A)}$ is the scalar you multiply a 2 x 2 matrix by to help invert it (you also need to move the matrix values around)

<mark style="background: #BBFABBA6;">FOR A 3 x 3 MATRIX</mark>
If $A=\begin{bmatrix}a & b & c \\ d & e & f \\ g & h & i\end{bmatrix}$ is a 3 x 3 matrix, we define
$$\det(A)=a*\det\begin{bmatrix}
e&f \\ h&i
\end{bmatrix}-b*\det \begin{bmatrix}
d & f \\
g & i
\end{bmatrix}+c*\det \begin{bmatrix}
d & e \\
g & h
\end{bmatrix}$$
$$=a(ei-hf)-b(di-gf)+c(dh-ge)$$
ALGORITHM:
1. Consider your current entry in the first row (the first entry in the first row if you're just starting)
2. Draw lines horizontally and vertically (this entry moves like a rook in chess)
3. The 4 elements that are NOT intersecting with the horizontal and vertical lines are the ones you will consider. calculate as if it was the determinant of a 2 x 2 matrix
4. multiply your current entry's value by this sub-sub-determinant
5. Go to the next entry in the first row and repeat
6. Once all the entries in the first row have been calculates, I thiiiiiiiiiiiink it just alternates + and - for summing all the sub-determinants (+, -, +)

![[Pasted image 20250415203510.png]]
![[Pasted image 20250415203522.png]]

<mark style="background: #BBFABBA6;">FOR A n x n MATRIX FOR N >= 3</mark>
If $A=\begin{bmatrix}a_{ij}\end{bmatrix}$ is a n x n matrix, we define
$$
\det(A)=a_{11}*\det(A_{11})-a_{12}*\det(A_{12})+\dots+(-1)^{n+1}a_{1n}\det(A_{1n})$$
$A_{ij}=\text{matrix from detleting the ith row and the jth column of A}$

This is called <mark style="background: #ADCCFFA6;">cofactor expansion</mark> **along the first row** of A. you just find a ton of sub-determinants
![[Pasted image 20250415205139.png]]

You can also do cofactor expansion along the first column
![[Pasted image 20250415205219.png]]
![[Pasted image 20250415205227.png]]

You can also do it along any row or column (but why)
![[Pasted image 20250415205250.png]]
![[Pasted image 20250415205302.png]]

<mark style="background: #BBFABBA6;">It is easiest to find the determinant using the row or column with the most zero's</mark>

