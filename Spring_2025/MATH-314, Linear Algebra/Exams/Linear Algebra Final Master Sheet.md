Midterm 1 (1.1-1.3, 2.1-2.4, 3.1-3.2, 4.1-4.4),
Midterm 2 (5.1-5.3, 6.1-6.2, 7.1-7.2, 8.1, 9.1-9.2),
Sections 8.2, 10.1-10.3, and 10.5*
* For section 10.5, ONLY Least Squares Approximations will be on the exam. QR Factorization will not be on the exam.

Misc. definitions that are easy to confuse:
- Consistent - system has one or infinite solutions
- Inconsistent - system has no solution
- Linearly independent - systems only solution is the trivial solution (there are no free variables)
	- There should be a leading entry in every column
- Linearly dependent - there is a free variable
- Symmetric - a matrices' transpose is equal to the matrix aka $A^T=A$
- Non-singular - a square matrix's RREF solves to the identity matrix
- Singular - a square matrix's RREF does NOT solve to the identity matrix
- Homogenous - if a system of linear equations has all constant terms of 0. Basically they take the form $Ax=0$
	- All homogenous systems are consistent
- Invertible - satisfies $AB=BA=I_{n}$
	- Every invertible matrix is non-singular
- Non-invertible - does not satisfy $AB=BA=I_{n}$
- Onto - If each vector $w\in W$ is the image of AT LEAST ONE vector $v\in V$, then T is onto
	- Every element of W has at least one thing in V that it maps to
	- If the rank < number of rows
- One-to-one - If each vector $w\in W$ is the image of AT MOST ONE vector $v\in V$, then T is one-to-one
	- every element of V maps to one element in W
	- There are no free variables
- Isomorphism - if it is both onto and one-to-one
	- There are n variables in V and W and each variable in V maps to one in W

The different forms solutions can take that I get confused what they want
![[Pasted image 20250510150654.png]]
An augmented matrix is just a matrix with the | bar things

# FINAL: Section 10.1 - 10.3 & 10.5 Orthogonality
Let $\{v_{1},v_{2},\dots,v_{k}\}$ be a set of nonzero vectors in $\mathbb{R}^n$. This set is called <mark style="background: #ADCCFFA6;">orthogonal</mark> if $\overrightarrow{v}_{i}*\overrightarrow{v}_{j}=0$ for all $i\neq j$

Moreover, if $||\overrightarrow{v}_{i}||=1$ for $i=1,\dots,k$, then we say the set is <mark style="background: #ADCCFFA6;">orthonormal</mark>. Basically if it's magnitude is 1 it's orthonormal

<mark style="background: #ADCCFFA6;">Normalizing</mark> an orthogonal set is the process of turning an orthogonal set into an orthonormal set
If $\{v_{1},v_{2},\dots,v_{k}\}$ is orthogonal then the set $\left\{\frac{1}{||\overrightarrow{v}_{1}||}\overrightarrow{v_{1}},\frac{1}{||\overrightarrow{v}_{2}||}\overrightarrow{v_{2}},\dots,\frac{1}{||\overrightarrow{v}_{n}||}\overrightarrow{v_{n}}\right\}$ is orthonormal

An orthogonal (or orthonormal) is a basis that is also an orthogonal (or orthonormal) set
Recall that the projection of a vector x to a nonzero vector d is given by $proj_{d}x=\frac{x*d}{||d||^2}d=\frac{x*d}{d*d}d$
Let W be a subspace of $\mathbb{R}^n$ and suppose that $f_{m}$ is an orthogonal basis of W. Then for every x in W,
$$x=\sum^n_{m=1}\frac{x*f_{m}}{||f_{m}||^2}$$
The corollary to that is suppose q is an ORTHONORMAL basis of W. Then for any x in W,
$$x=\sum^n_{m=1}(x*q_{m})q_{m}$$

An <mark style="background: #ADCCFFA6;">orthogonal projection</mark> is when you project a vector x onto a subspace W that has an orthogonal basis of $f_{m}$. Basically 
![[Pasted image 20250511121844.png]]

We can <mark style="background: #ADCCFFA6;">decompose</mark> a vector x into the sum of its projection $W=proj_{W}x$ and the vector orthogonal to w, which we call $w^\bot$ (w-perp)
Theorem: $w^\bot$ is orthogonal to every
1. $f_{i}$ and
2. every vector in W
Note that the distance from P (head of vector x) to W is the magnitude of $w^\bot$
![[Pasted image 20250511122150.png]]

The <mark style="background: #ADCCFFA6;">Gram-Schmidt Process</mark> is an algorithm for taking a basis, applying the process to it, and then getting an orthogonal basis
Let $\{v_{1},v_{2},\dots,v_{k}\}$ be a basis for a subspace W in $\mathbb{R}^n$. Then the orthogonal basis $\{f_{1},f_{2},\dots,f_{k}\}$ for W can be found using the below formulas:
$\begin{matrix}f_{1}=v_{1} \\ f_{2}=v_{2}-\frac{f_{1}*v_{2}}{f_{1}*f_{1}}f_{1} \\ f_{3}=v_{3}-\frac{f_{2}*v_{3}}{f_{2}*f_{2}}f_{2}-\frac{f_{1}*v_{3}}{f_{1}*f_{1}}f_{1} \\ f_{n}=v_{n}-\frac{f_{n-1}*v_{n}}{f_{n-1}*f_{n-1}}f_{n-1}-\dots-\frac{f_{1}v_{n}}{f_{1}*f_{1}}f_{1}\end{matrix}$

If W is a subspace of $\mathbb{R}^n$, define the <mark style="background: #ADCCFFA6;">orthogonal complement</mark> $W^\bot$ of W by $W^\bot=\{w^\bot\in \mathbb{R}^n:w^\bot*w=0\text{ for all }w\in W\}$
1. Find the span of W
2. Multiply unknown vector x by each column in the span
3. Set up the system of linear equations that sets the above in part 2 to 0 and puts it into a new matrix
4. Solve the system for RREF
5. Put it into null space form (columns defined by the fee variables)
6. This is the basis for $W^\bot$

Theorem: Let W be a subspace of $\mathbb{R}^n$
1. $W^\bot$ is a subspace of $\mathbb{R}^n$
2. $\{0\}^\bot=\mathbb{R}^n$ and $(\mathbb{R}^n)^\bot=\{0\}$
3. If $W=span(x_{1},x_{2},\dots,x_{k})$ then $W^\bot=\{x\in \mathbb{R}^n|x*x_{i}=0\text{ for }i=1,2,\dots,k\}$
Theorem: Let A be an m x n matrix. Then we have:
4. $(row(A))^\bot=null(A)$
5. $(col(A))^\bot=null(A^T)$

TODO LATER: ORTHOGONAL DECOMPOSITION

<mark style="background: #ADCCFFA6;">Least-Squares Approximation</mark> is what you do when $Ax=b$ has no solution for x. You find the vector z so that Az is as close as possible to b
$$||b-Az||\leq||b-Ax||$$
![[Pasted image 20250511124057.png]]

Notice that $b-Az$ is orthogonal to col(A), so $b-Az\in(col(A))^\bot$. Also recall that $(col(A))^\bot=null(A^T)\Rightarrow b-Az\in null(A^T)$
Therefore, $A^TAz=A^Tb$ <mark style="background: #BBFABBA6;">is a best approximation to a solution</mark>
1. Show that the system $Ax=b$ is inconsistent (if needed)
2. Find the transpose of A
3. Multiply the transpose of A by A
4. Multiply the transpose of A by b
5. Set the matrix from part 3 into an augmented matrix with part 4 as the = side and solve to RREF
6. the RREF solution is z

# FINAL: Section 8.2 Similar and Diagonalizable Matrices
We say two n x n matrices A and B are <mark style="background: #ADCCFFA6;">similar</mark>, denoted $A\sim B$, if $A=PBP^{-1}$ where P is some invertible matrix

Theorem: If $A\sim B$ are n x n matrices, then
- $\det(A)=\det(B)$
- $rank(A)=rank(B)$
- A and B have the same characteristic polynomial and eigenvalues
- $A^{-1}\sim B^{-1}$ (if A is invertible)
- $A^T\sim B^T$
- $A^k\sim B^k$ for all integers $k\geq1$

Let A be an n x n matrix. A is a <mark style="background: #ADCCFFA6;">diagonalizable</mark> if it is similar to a diagonal matrix. That is, $A=PDP^{-1}$ where P is some invertible matrix and D is a diagonal matrix
A <mark style="background: #ADCCFFA6;">diagonal</mark> matrix is one with only values other than 0 on the main diagonal

NOTE:
An n x n matrix A is diagonalizable <mark style="background: #BBFABBA6;">if and only if</mark> there is an invertible matrix P given by $P=\begin{bmatrix}| & | &  & | \\ x_{1} & x_{2} & \dots & x_{n} \\ | & | &  & |\end{bmatrix}$, where the columns $x_{i}$ are eigenvectors of A
Moreover, if A is diagonalizable, the corresponding eigenvalues of A are the diagonal entries of the diagonal matrix D

Observe: A diagonalizable $\Leftrightarrow$ eigenvectors of A form a basis for $\mathbb{R}^n$

TO FIND IF A MATRIX IS DIAGONALIZABLE:
1. Find the eigenvalues of a matrix using $\det(A-\lambda I)$
2. Second, solve $A-\lambda I$ for each eigenvalue, put it into RREF, and write it as a basis
	1. Note that if there are repeat eigenvalues, only do it once for the repeat value
	2. Note that if while doing this step it results in a matrix that is not a valid basis for $\mathbb{R}^n$ then it is not diagonalizable
3. The combined vectors of the basis's for every eigenvalue form the matrix P and the eigenvalues from step 1 form D
4. If needed, solve $P=I_{n}$ in an augmented matrix to find $P^{-1}$

For example, $A=\begin{bmatrix}2 & 0 & 0 \\ 1 & 4 & -1 \\ -2 & -4 & 4\end{bmatrix}$ has eigenvalues $\lambda=2,2,6$
2. Find eigenspace basis's
$A-2I=\begin{bmatrix}0 & 0 & 0 \\ 1 & 2 & -1 \\ -2 & -4 & 2\end{bmatrix}\overrightarrow{RREF}\begin{bmatrix}1 & 2 & -1 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix}\to \begin{matrix}x_{1}=-2s+t \\ x_{2}=s \\ x_{3}=t\end{matrix}$
$\text{Basis for }S_{\lambda=2}=\left\{\begin{bmatrix}-2 \\ 1 \\ 0\end{bmatrix},\begin{bmatrix}1 \\ 0 \\ 1\end{bmatrix}\right\}$

$A-6I=\begin{bmatrix}-4 & 0 & 0 \\ 1 & -2 & -1 \\ -2 & -4 & -2\end{bmatrix}\overrightarrow{RREF}\begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & \frac{1}{2} \\ 0 & 0 & 0\end{bmatrix}\to \begin{matrix}x_{1}=0 \\ x_{2}=-\frac{1}{2}s \\ x_{3}=s\end{matrix}$
$\text{Basis for }S_{\lambda=6}=\left\{\begin{bmatrix}0 \\ -1 \\ 2\end{bmatrix}\right\}$
3. Putting it all together
$D=\begin{bmatrix}2 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 6\end{bmatrix}$
$P=\begin{bmatrix}-2 & 1 & 0 \\ 1 & 0 & -1 \\ 0 & 1 & 2\end{bmatrix}$
$P^{-1}=\begin{bmatrix}-\frac{1}{4} & \frac{1}{2} & \frac{1}{4} \\ \frac{1}{2} & 1 & \frac{1}{2} \\ \frac{1}{4} & \frac{1}{2} & -\frac{1}{4}\end{bmatrix}$

The <mark style="background: #ADCCFFA6;">algebraic multiplicity</mark> of an eigenvalue $\lambda$ is the number of times it appears as a root in the characteristic polynomial
	From the example above the geometric multiplicity of 2 is 2
The <mark style="background: #ADCCFFA6;">geometric multiplicity</mark> of an eigenvalues $\lambda$ is $dim(S_{\lambda})$

Let A be an n x n matrix A. <mark style="background: #BBFABBA6;">Then A is diagonalizable if and only if</mark> for each eigenvalue $\lambda$ of A, the algebraic multiplicity of $\lambda$ is equal to the geometric multiplicity of $\lambda$
Note that from the above theorem we can also conclude that any matrix that has n distinct eigenvalues is diagonalizable

You can take the power of a diagonalizable matrix by $A^n=PD^nP^{-1}$

# MIDTERM 2: Section 8.1 Eigenvalues and vectors
Let A be a square n x n matrix. We say a nonzero vector x is an <mark style="background: #ADCCFFA6;">eigenvector</mark>
 of A if $A\overrightarrow{x}=\lambda\overrightarrow{x}$ for some scalar $\lambda$
 
The characteristic polynomial is $\det(A-\lambda I)$ and it's basically all you need
Algorithm for solving for eigenvectors using given eigenvalues:
1. Calculate $A-\lambda I$
	1. Note: If you were not given eigenvalues, solve for eigenvalues using the characteristic polynomial first. Should be the roots of $\det(A-\lambda I)$
2. Solve $A-\lambda I$ into RREF
3. The solution for the variables is each row value of the eigenvector for this specific eigenvalue
4. Repeat per eigenvalue
	1. Note if it's a 2x2 matrix don't even bother just solve it like a two-variable equation

If you want to solve for an eigenvalue given a matrix and an eigenvector, use the definition of the two instead of the characteristic polynomial
$$A\overrightarrow{x}=\lambda\overrightarrow{x}$$
1. Multiply the matrix by the eigenvector
2. Set this equal to $\lambda\overrightarrow{x}$ 
3. Solve algebraically 

To determine if a given vector is an eigenvector for a matrix, multiply the two vectors together (usually Av and yes the order matters) and the result should be a scalar multiple of the eigenvector

If you have an eigenvalue of 0 and need to find it's associated eigenvector, go through the regular process of finding an eigenvector except only reduce to REF instead of RREF. These values will solve to the solution

<mark style="background: #BBFABBA6;">To find the basis of the eigenspace</mark>, Given a lambda, do $A-\lambda I$ and solve into RREF. Find the nullspace, this is the eigenspace

# MIDTERM 2: Section 9.1 - 9.2 Vector Spaces
It's just doing everything we already know how to do but with variables instead of numbers

Know that $\mathbb{P}^n$ is just a polynomial in n dimensions, so $\mathbb{P}^3$ is just 1, x, x^2, x^3. A basis is just that with {}

$\mathbb{M}_{n\ x\ m}$ just means Matrix with n rows and m columns 

# MIDTERM 2: Section 7.1 - 7.2 Determinants
For every square n x n matrix A we want to assign a scalar, called the <mark style="background: #ADCCFFA6;">determinant</mark> of A, denoted by $\det(A)$ that satisfies
$$\det(A)=0\Leftrightarrow \text{A is not invertible (singular)}$$
$$\det(A)\ne0\Leftrightarrow \text{A is invertible (non-singular)}$$
Basically the determinant is the measure of if a matrix is invertible or not. <mark style="background: #BBFABBA6;">It is a bit of an arbitrary number that is only important because you can infer a lot of things from it</mark>
- If A has a row of zeroes, the determinant is 0
- If two rows of A are the same, then the determinant is 0
- If one row of A is a scalar multiple of another row, then the determinant is 0

Theorem: Let $A=[a_{ij}]$ be an n x n matrix
1. If B is obtained from A by interchanging two different rows, then
$$\det B=-\det A$$
2. If B is obtained from A by multiplying one of the rows of A by a non-zero constant k, then
$$\det B=k\det A$$
3. If B is obtained from A by adding a multiple of one row of A to another row, then
$$\det B=\det A$$
4. If A and B are square matrices, then
$$\det AB=\det A\det B$$
$$\det A^{-1}=\frac{1}{\det A}$$
$$\det kA=k^n\det A$$
$$\det(A+B)\neq \det(A)+\det(B)$$

FINDING THE DETERMINANT:
<mark style="background: #BBFABBA6;">FOR A 1 x 1 MATRIX:</mark>
For a 1 x 1 matrix (a scalar), $A=[a]$, the determinant is just a, so $\det(A)=a$. Very simple. Notice that as long as a != 0, $a^{-1}=\frac{1}{a}$

<mark style="background: #BBFABBA6;">FOR A 2 x 2 MATRIX:</mark>
If $A=\begin{bmatrix}a & b \\ c & d\end{bmatrix}$ is a 2 x 2 matrix, we define $\det(A)=ad-bc$
Recall and notice that if the matrix is invertible, then $A^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d & -b \\ -c & a\end{bmatrix}$
So, $\frac{1}{\det(A)}$ is the scalar you multiply a 2 x 2 matrix by to help invert it (you also need to move the matrix values around)

<mark style="background: #BBFABBA6;">FOR A 3 x 3 MATRIX:</mark>
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

<mark style="background: #BBFABBA6;">FOR A n x n MATRIX FOR N >= 3:</mark>
If $A=\begin{bmatrix}a_{ij}\end{bmatrix}$ is a n x n matrix, we define
$$
\det(A)=a_{11}*\det(A_{11})-a_{12}*\det(A_{12})+\dots+(-1)^{n+1}a_{1n}\det(A_{1n})$$
$A_{ij}=\text{matrix from detleting the ith row and the jth column of A}$
This is cofactor expansion. You just find a ton of sub-determinants. Along the column works the same way. It is easiest to find the determinant using the row or column with the most 0's

# MIDTERM 2: Section 6.1 - 6.2 Linear Transformations
A <mark style="background: #ADCCFFA6;">function</mark> or transformation T from $\mathbb{R}^n$ to $\mathbb{R}^m$, denoted $T:\mathbb{R}^{n}\to \mathbb{R}^m$, is a mapping of vectors in $\mathbb{R}^n$ to vectors in $\mathbb{R}^m$.
- $\mathbb{R}^n$ is the domain
	- Otherwise known as the number of columns of the standard matrix of transformation
- $\mathbb{R}^m$ is the codomain
	- Otherwise known as the number of rows of the standard matrix of transformation
- For $x\epsilon \mathbb{R}^m$, the image of $\overrightarrow{x}$ is $T(\overrightarrow{x})$
- The set of all images of T is called the range (or images because mathematicians hate us)

Note that the image of a vector is literally just the output it gives if you do f(x), it's very easy

A <mark style="background: #ADCCFFA6;">matrix transformation</mark> is a transformation $T:\mathbb{R}^{n}\to \mathbb{R}^m$ defined by $T(\overrightarrow{x})=A\overrightarrow{x}$ where A is an m x n matrix

For example, $T:\mathbb{R}^3\to \mathbb{R}^2$ defined by $T\left(\begin{bmatrix}x \\ y \\ z\end{bmatrix}\right)=\begin{bmatrix}5x+y \\ 7z\end{bmatrix}$
To get the standard matrix of a transformation, you have to go a step further and just drop the variables and put it into matrix form, for example
$\begin{bmatrix}5x+y \\ 7z\end{bmatrix}\to \begin{bmatrix}5 & 1 & 0 \\ 0 & 0 & 7\end{bmatrix}$ where the columns represent variables

A transformation $T:\mathbb{R}^{n}\to\mathbb{R}^m$ is called a <mark style="background: #ADCCFFA6;">linear transformation</mark> if
1. $T(\overrightarrow{u}+\overrightarrow{v})=T(\overrightarrow{u})+T(\overrightarrow{v})$
2. $T(k\overrightarrow{u})=kT(\overrightarrow{u})$
for all vectors u and v in $\mathbb{R}^n$ and scalars k
KEY NOTES: Addition tends to break if there's any constants and multiplication tends to break if there's any exponents. Otherwise, it is usually linear

Basically just calculate the four scenarios and if all of them hold it is linear
1. It is the difference between doing $\begin{bmatrix}0 \\ x_{1}+x_{2}\end{bmatrix}$ and $\begin{bmatrix}0 \\ x_{1}\end{bmatrix}+\begin{bmatrix}0 \\ x_{2}\end{bmatrix}$. This is why constants tend to break it since you're adding the constants twice, so it wouldn't be equal. Note the given example is linear
2. Similarly, for multiplication it is the difference between doing $k\begin{bmatrix}0 \\ x_{1}\end{bmatrix}$ and $\begin{bmatrix}0 \\ kx_{1}\end{bmatrix}$, which is why exponents tend to break it since if one of your terms is $x^2$, then it'd be $(kx)^2$ which is different than $k(x^2)$

Theorem 6.2.11: Let A be an m x n matrix. Define $T:\mathbb{R}^n\to \mathbb{R}^m$ by $T(v)=Av$. Then T is a linear transformation
The identity and zero transformations are linear

Theorem: Let $T:V\to W$ be a transformation of vector spaces with matrix representation A with respect to some bases for V and W
1. T maps V onto W if and only if RREF(A) has a pivot in every row
2. T is one-to-one if and only if RREF(A) has a pivot in every column

Let $T:\mathbb{R}^n\to \mathbb{R}^m$ be a linear transformation with standard matrix A. Then the <mark style="background: #ADCCFFA6;">kernal</mark> of T, denoted $ker(T)$, is the set of all vectors $\overrightarrow{x}\in \mathbb{R}^n$ such that
$$T(\overrightarrow{x})=\overrightarrow{0}$$

Note that $ker(T)=null(A)$

# MIDTERM 2: Section 5.1 - 5.3 Subspaces of $\mathbb{R}^n$
A set V is said to be <mark style="background: #ADCCFFA6;">closed under addition</mark> if for all elements $u,v\epsilon V$ (vectors u and v in V), then the below. Basically a set is closed under addition if there is no vector you can add to v to push it out of it's span. REMEMBER THAT U HAS TO BE IN V YOU CAN'T JUST ADD WHATEVER TO IT
$$\overrightarrow{u}+\overrightarrow{v}\epsilon V$$
A set V is said to be <mark style="background: #ADCCFFA6;">closed under scalar multiplication</mark> if for each $v\epsilon V$ and scalar $k\epsilon\mathbb{R}$, then the below. Basically a set is closed under multiplication if there is no scalar value you can multiply it by to pus hit out of it's span. k can be whatever value
$$k\overrightarrow{v}\epsilon V$$
Let V be a nonempty subset of $\mathbb{R}^n$ that is closed under both vector addition and scalar multiplication. Then V is a <mark style="background: #ADCCFFA6;">subspace</mark> of $\mathbb{R}^n$
- NOTE THAT A VECTOR HAS TO CONTAIN THE 0 VECTOR TO BE A SUBSPACE OF $\mathbb{R}^n$
- It also has to contain the inverse vector as well ($V^{-1}$)
- The span of any set of vectors is a subspace of $\mathbb{R}^n$

Tip: When determining closure you usually just have to look at the edge cases, like adding 1 or 0 to it and pos/neg values

A <mark style="background: #ADCCFFA6;">vector space</mark> is a subspace that follows a few more constraints. The extra 8 properties + closure with vector addition and scalar multiplication mean that it is a vector space
![[Pasted image 20250510154700.png]]

A <mark style="background: #ADCCFFA6;">coordinate vector</mark> is just $\begin{bmatrix}a \\ b\end{bmatrix}$ that you can multiply by standard unit vectors to describe their coordinates, so $v=\begin{bmatrix}a \\ b\end{bmatrix}=a\begin{bmatrix}1 \\ 0\end{bmatrix}+b\begin{bmatrix}0 \\ 1\end{bmatrix}=ai+bj$, so $\begin{bmatrix}a \\ b\end{bmatrix}$ is the coordinate vector WITH RESPECT TO {i, j}
To find the coordinate vector of a vector with respect to a set of vectors, you just combine them and put the set into an augmented matrix with v as the solution
So the coordinates for vector $\begin{bmatrix}2 \\ 6\end{bmatrix}$ with respect to $\left\{\begin{bmatrix}1 \\ 0\end{bmatrix},\begin{bmatrix}1 \\ 2\end{bmatrix}\right\}$ is $\begin{bmatrix}1 & 1 & | & 2 \\ 0 & 2 & | & 6\end{bmatrix}$ and you just solve to REF which is $\begin{bmatrix}1 & 1 & | & 2 \\ 0 & 1 & | & 3\end{bmatrix}$, which means $a=-1$ and $b=3$. These are the coordinates, the coordinate vector is $\begin{bmatrix}-1 \\ 3\end{bmatrix}$

A set R of vectors is called a <mark style="background: #ADCCFFA6;">basis</mark> of $\mathbb{R}^n$ if:
1. $Span(R)=\mathbb{R}^n$ <-- existence question
2. R is linearly independent <-- uniqueness
to show that it is a basis of $\mathbb{R}^n$ you need to have a leading entry in every COLUMN and ROW of REF
Basis is always in the form $basis=\left\{\begin{bmatrix}1 \\ 1\end{bmatrix},\begin{bmatrix}1 \\ 1\end{bmatrix}\right\}$ or $basis=\left\{\begin{bmatrix}1 & 1\end{bmatrix},\begin{bmatrix}1 & 1\end{bmatrix}\right\}$
Basically to see <mark style="background: #BBFABBA6;">if a vector is a basis just solve for REF and see if it has leading entries everywhere</mark>
NOTE: If V is a subspace, then any linearly independent subset of V can be extended to be a basis for V

The <mark style="background: #ADCCFFA6;">dimension</mark> of $\mathbb{R}^n$ and subspaces is the number of vectors in a basis. Denoted by $dim(\mathbb{R}^n)$ or $dim(v)$. Basically how many leading entries does the REF of the matrix have

The <mark style="background: #ADCCFFA6;">row space</mark> of a matrix A is the subspace of $\mathbb{R}^n$ spanned by the rows of A
Find the RREF of the matrix. The row space is every row that has a pivot
For example, 
$A=\begin{bmatrix}1 & 3 & 2 \\ 0 & 2 & 0 \\ -1 & -1 & -3\end{bmatrix}\to RREF(A)=\begin{bmatrix}1 & 0 & 3 \\ 0 & 1 & 0 \\ 0 & 0 & 0\end{bmatrix}$
$basis=\{\begin{bmatrix}1&0&3\end{bmatrix},\begin{bmatrix}0 & 1 & 0\end{bmatrix}\}$
You just put the rows in a comma separated list

The <mark style="background: #ADCCFFA6;">column space</mark> of A, denoted by col(A), is the subspace of $\mathbb{R}^m$ spanned by the columns of A
Find the RREF of the matrix. Note which columns have a pivot in them. Unlike row space, these pivot columns ARE NOT directly the column space since columns are not preserved in row operations. Instead, the ORIGINAL VERSION of the pivot columns form the column space for the basis
For example, $A=\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}\overrightarrow{RREF}\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$
It has a pivot column in col 1, so $col(B)=\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}$
The basis of the column space is just the columns in comma separated form, so $basis=\left\{\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}\right\}$

The <mark style="background: #ADCCFFA6;">null space</mark> of A is the set in $\mathbb{R}^n$ of all vectors x that satisfy $Ax=0$
The null space is any vector that would cause the matrix to 0 out. You put a matrix in RREF form and solve it for = 0. Put it in vector form and that's the answer
Example, $A=\begin{bmatrix}2 & 2 \\ -3 & -3\end{bmatrix}\overrightarrow{RREF}\begin{bmatrix}1 & 1 \\ 0 & 0\end{bmatrix}$
We have free variables here (as is common and necessary in null spaces), so $\begin{matrix}x=-t \\ y=t\end{matrix}$
In vector form, this is $\overrightarrow{x}=\begin{bmatrix}-1 \\ 1\end{bmatrix}t$, which in basis format is $basis=\left\{\begin{bmatrix}-1 \\ 1\end{bmatrix}\right\}$
<mark style="background: #BBFABBA6;">Note: if there are no free variables the null space is the zero vector since the only solution to Ax = 0 is the trivial solution of 0</mark>

Procedure because it's kinda funky:
1. row reduced to RREF
	1. $rref(M)=\begin{bmatrix}1 & 0 & 2 & 0 & 3 & 1 \\ 0 & 1 & -1 & 0 & 1 & -2 \\ 0 & 0 & 0 & 1 & -2 & 1 \\ 0 & 0 & 0 & 0 & 0 & 0\end{bmatrix}$
2. identify variables
	1. $\begin{matrix}x_{1}=2a+3b+c \\ x_{2}=-a+b-2c \\ a \\ x_{4}=-2b+c \\ b \\ c\end{matrix}$
3. set up a vector solution in terms of the free variables
	1. $a\begin{bmatrix}2 \\ -1 \\ 1 \\ 0 \\ 0 \\ 0\end{bmatrix}+b\begin{bmatrix}-3 \\ -1 \\ 0 \\ 2 \\ 1 \\ 0\end{bmatrix}+c\begin{bmatrix}-1 \\ 2 \\ 0 \\ -1 \\ 0 \\ 1\end{bmatrix}$
4. these vectors are the basis of the nullspace
	1. $basis(null(M))=\left\{\begin{bmatrix}2 \\ -1 \\ 1 \\ 0 \\ 0 \\ 0\end{bmatrix},\begin{bmatrix}-3 \\ -1 \\ 0 \\ 2 \\ 1 \\ 0\end{bmatrix},\begin{bmatrix}-1 \\ 2 \\ 0 \\ -1 \\ 0 \\ 1\end{bmatrix}\right\}$

The <mark style="background: #ADCCFFA6;">rank-nullity theorem</mark> says the nullity of a matrix A is $nullity(A)=dim(null(A))$
Suppose A is an m x n matrix. Then $rank(A)+nullity(A)=n$
<mark style="background: #BBFABBA6;">Basically says that all pivot columns + all free columns = total columns</mark>
(Rank is equivalent to pivot columns and nullity is equivalent to free var columns)

# MIDTERM 1: Section 4.1 - 4.4 Matrices
A matrix is just an augmented matrix without the | column in it

The <mark style="background: #ADCCFFA6;">dimension</mark> of a matrix is m x n where m is the rows and n is the cols

Matrix addition and scalar multiplication: literally just add every corresponding cell together or multiply all entries by a scalar

Matrix multiplication is a little more complicated. You can only multiply matrices A: m x n and B: n x p if matrix A has the same number of columns as B has rows. The n here needs to match. The new dimensions are then m x p
Dot product matrix A's rows by matrix B's columns and have that as the new value. Note that multiplication is not distributive, which means AB is not equal to BA
$$\overrightarrow{\begin{bmatrix}
1 & 3 & -2 & 1 \\
-2 & 1 & 0 & 4
\end{bmatrix}}

\downarrow{\begin{bmatrix}
4 \\
-2 \\
1 \\
1
\end{bmatrix}}$$
This is a 2x4 * 4x1 matrix, so it transforms into a 2x1 matrix

The <mark style="background: #ADCCFFA6;">transpose</mark> of an m x n matrix A is the n x m matrix $A^T=([a_{ij}])^T=[a_{ji}]$. Basically you just swap every entry's row and column. Flip it across the diagonal basically. It will change the dimensions of the matrix, so a 3x2 matrix would become a 2x3 matrix. Easier to do mathematically than visually, so entry $a_{1,2}\to a_{2,1}$ for row, col

A matrix is <mark style="background: #ADCCFFA6;">diagonal</mark> if every entry outside of the main diagonal is zero

A <mark style="background: #ADCCFFA6;">matrix equation</mark> is an equation of the for $Ax=b$ for some m x n matrix A, n x 1 vector x, and m x1 vector b

If a matrix is nonsingular, it has the following properties:
1. $Ax=b$ has a unique solution for any b in $\mathbb{R}^n$
2. $Ax=0$ has only the trivial solution $x=0$ because the columns are linearly independent

IF a system is <mark style="background: #ADCCFFA6;">homogenous</mark> it is not possible for it to be inconsistent because the trivial solution will always be a solution. In general, solution sets of homogenous systems are equal to span

<mark style="background: #ADCCFFA6;">Inverse matrices</mark> are b if $AB=BA=I_{n}$. Inverse matrices are unique. If no such B exists then it is not invertible. Basically what matrix can you multiply your matrix by for it to equal the identity matrix.
Note: You can use the inverse matrix of A to solve $Ax=b$, it'll just be $x=A^{-1}b$
1. To determine if a matrix is invertible with a given B, you basically just prove 1. that $AB=I_{n}$ and 2. that $BA=I_{n}$ so it's kind of tedious. You just multiply them
2. To find a B if not given one: solve $A=I_{n}$ into RREF using an augmented matrix. If the resulting left hand side matrix is not in identity matrix form, it is not invertible. The right hand side is now B aka $A^{-1}$ 
3. If it's a 2x2 matrix it's much easier; if you have a 2x2 matrix $A=\begin{bmatrix}a & b \\ c & d\end{bmatrix}$, then the inverse of A is just $A^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d & -b \\ -c & a\end{bmatrix}$ if A is invertible. If A is NOT invertible, you can tell because $ad-bc=0$ in not invertible matrices

# MIDTERM 1: Section 3.1 - 3.2 Big Ideas about Vectors
Literally just says you can express vectors as $\begin{bmatrix}1 \\ 1 \\ 1\end{bmatrix}+\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}$ instead of in one matrix. It's called a <mark style="background: #ADCCFFA6;">linear combination</mark>

The <mark style="background: #ADCCFFA6;">span</mark> of a set of all possible linear combinations for a space or given vector group. Basically, if you take a group of vectors and put them into one matrix (or if you start with a matrix to begin with), and solve it for REF, <mark style="background: #BBFABBA6;">its span is how many leading entries it has</mark>

A <mark style="background: #ADCCFFA6;">redundant</mark> vector is a vector you can remove without changing the span of the set. That is, if you solved the matrix for REF it would NOT have a leading entry

A set of vectors is <mark style="background: #ADCCFFA6;">linearly independent</mark> if the only solution to the linear combination equation is the trivial solution (everything = 0). Otherwise, they are linearly dependent

# MIDTERM 1: Section 2.1 - 2.4 Systems of Linear Equations
SLE will stand for system of linear equations because I got tired of typing it

<mark style="background: #ADCCFFA6;">Elementary Row Operations</mark> are operations you can perform on a linear system without changing the solution
1. Switching the order of equations (rows) i and j
$$R_{i}\leftrightarrow R_{j}$$
2. Multiplying both sides of equation (row) i by the same non-zero constant, k, and replacing equation i with the result
$$kR_{i}\to R_{i}$$
3. Adding k times equation (row) i to equation (row) j, and replacing equation j with the result:
$$R_{j}+kR_{i}\to R_{j}$$

Writing all of the coefficients in an array with a | equaling replacing the equals sign is called an <mark style="background: #ADCCFFA6;">augmented matrix</mark>
$\begin{bmatrix}x &  &  & | & a \\  & y &  & | & b \\  &  & z & | & c\end{bmatrix}$

<mark style="background: #ADCCFFA6;">REF</mark> is when
1. All entries below leading entry are 0
2. Each leading entry is in a column to the right of the leading entries in the rows above it
3. All rows of zeroes, if there are any, are located below nonzero rows
<mark style="background: #ADCCFFA6;">RREF</mark> is when
4. it is in REF
5. Each leading entry is 1
6. All entries below AND above leading entries are 0

Variables that do not have a leading entry in their column are <mark style="background: #ADCCFFA6;">free variables</mark>. Free variables get assigned as parameter's and you can put the solution in terms of them

The process of row reducing a matrix to REF is called <mark style="background: #ADCCFFA6;">Gaussian elimination</mark>
Row reducing a matrix to RREF is called <mark style="background: #ADCCFFA6;">Gauss-Jordan elimination</mark>
They're basically just algorithms to reduce a matrix. Shouldn't need them at this point

<mark style="background: #ADCCFFA6;">Rank</mark> of a matrix, rank(A), is the number of nonzero rows in an REF of A. It has the following properties (where r is rank)
1. The set of solutions involves exactly n - r parameters, corresponding to n - r free variables
2. If r < n, the system has infinitely many solutions
3. If r = n, the system has a unique solution

# MIDTERM 1: Section 1.1 - 1.3 Preliminaries
The <mark style="background: #ADCCFFA6;">length/size/magnitude</mark> of a vector is the distance between it's head and tail. Just use distance formula

If two vectors dot product is 0 they are orthogonal; they cancel each other out

A <mark style="background: #ADCCFFA6;">direction vector</mark> of a line L is any vector that lies on the line. So it's just like a vector overlaid onto a regular line it's not that deep

The <mark style="background: #ADCCFFA6;">projection</mark> of a vector v onto a nonzero vector d is given by
$$proj_{d}v=\frac{v*d}{d*d}d$$
This is just like shadows. Projecting something onto s<mark style="background: #ADCCFFA6;"></mark>omething else. Projecting v onto d also gives the projection of v onto a line L with direction d
![[Pasted image 20250510131700.png]]

A <mark style="background: #ADCCFFA6;">parametric equation</mark> is just like $\begin{matrix}x=2t-1 \\ y=-3t+6\end{matrix}$ so just basically a matrix in variable form

A nonzero vector n is called <mark style="background: #ADCCFFA6;">normal</mark> to a plane if it is orthogonal to every vector in the plane

The <mark style="background: #ADCCFFA6;">standard form</mark> of a plane equation is $ax+by+cz=d$

The difference between a line, plane, and hyperplane depends on the $\mathbb{R}$ you're working with. Basically how it works is for n > 3, anything with dimensions of n-3 is a line, n-2 is a plane, and n-1 is a hyperplane
![[Pasted image 20250510133130.png]]