5.1-5.3, 6.1-6.2, 7.1-7.2, 8.1, and 9.1-9.2
# Definitions
## closed under addition
A set V is said to be <mark style="background: #ADCCFFA6;">closed under addition</mark> if for all elements $u,v\epsilon V$ (vectors u and v in V), then
$$\overrightarrow{u}+\overrightarrow{v}\epsilon V$$

## closed under scalar multiplication
A set V is said to be <mark style="background: #ADCCFFA6;">closed under scalar multiplication</mark> if for each $v\epsilon V$ and scalar $k\epsilon\mathbb{R}$, then:
$$k\overrightarrow{v}\epsilon V$$

## subspace of $\mathbb{R}^n$
Let V be a nonempty subset of $\mathbb{R}^n$ that is closed under both vector addition and scalar multiplication. Then V is a <mark style="background: #ADCCFFA6;">subspace</mark> of $\mathbb{R}^n$.

## coordinates of a vector
Recall i and j as the standard unit vectors of [1, 0] and [0, 1]
We can describe other vectors as linear combinations of these vectors.
$$\overrightarrow{v}=\begin{bmatrix}
a \\
b
\end{bmatrix}=a\begin{bmatrix}
1 \\
0
\end{bmatrix}+b\begin{bmatrix}
0 \\
1
\end{bmatrix}$$

When doing this, we say a and b are <mark style="background: #ADCCFFA6;">coordinates</mark> of v with respect to {i, j} and $\begin{bmatrix}a \\ b\end{bmatrix}$ is the <mark style="background: #ADCCFFA6;">coordinate vector</mark> of v with respect to {i, j}

## coordinate vector with respect to a basis?
Solved the same as the other one

## basis
A set R of vectors is called a <mark style="background: #ADCCFFA6;">basis</mark> of $\mathbb{R}^n$ if:
1. $Span(R)=\mathbb{R}^n$ <-- existence question
2. R is linearly independent <-- uniqueness

Similarly, a basis of a subspace V of $\mathbb{R}^n$ is a set of vectors S that
1. $Span(S)=V$
2. S is linearly independent

## dimension
The <mark style="background: #ADCCFFA6;">dimension</mark> of $\mathbb{R}^n$ (or subspace V) is the number of vectors in a basis for $\mathbb{R}^n$ (or V). Denoted by $dim(\mathbb{R}^n)$ or $dim(v)$


## row, column, and null space of a matrix
The <mark style="background: #ADCCFFA6;">row space</mark> of A, denoted by row(A) is the subspace of $\mathbb{R}^n$ spanned by the rows of A. Basically just the RREF rows that have a pivot put into the format
The <mark style="background: #ADCCFFA6;">column space</mark> of A, denoted by col(A), is the subspace of $\mathbb{R}^m$ spanned by the columns of A
The <mark style="background: #ADCCFFA6;">null space</mark> of A, denoted by null(A), is the set in $\mathbb{R}^n$ of all vectors $\overrightarrow{x}$ that satisfy $A\overrightarrow{x}=\overrightarrow{0}$

## rank and nullity of a matrix
The <mark style="background: #ADCCFFA6;">nullity</mark> of a matrix A is nullity(A)=dim(null(A)). Suppose A is an m x n matrix. Then rank(A)+nullity(A)=n

Basically all the pivot columns + all the free variable columns = total columns
(Rank is equivalent to pivot columns and nullity is equivalent to free var columns)

Rank is the number of pivot columns

## linear transformation
A transformation $T:\mathbb{R}^{n}\to\mathbb{R}^m$ is called a <mark style="background: #ADCCFFA6;">linear transformation</mark> if
1. $T(\overrightarrow{u}+\overrightarrow{v})=T(\overrightarrow{u})+T(\overrightarrow{v})$
2. $T(k\overrightarrow{u})=kT(\overrightarrow{u})$
for all vectors u and v in $\mathbb{R}^n$ and scalars k

## domain, codomain, image/range, and kernel
A <mark style="background: #ADCCFFA6;">function</mark> or transformation T from $\mathbb{R}^n$ to $\mathbb{R}^m$, denoted $T:\mathbb{R}^{n}\to \mathbb{R}^m$, is a mapping of vectors in $\mathbb{R}^n$ to vectors in $\mathbb{R}^m$.
- $\mathbb{R}^n$ is the domain
- $\mathbb{R}^m$ is the codomain
- For $x\epsilon \mathbb{R}^m$, the image of $\overrightarrow{x}$ is $T(\overrightarrow{x})$
- The set of all images of T is called the range (or images because mathematicians hate us)
![[Pasted image 20250417184840.png]]

Let $T:\mathbb{R}^n\to \mathbb{R}^m$ be a linear transformation with standard matrix A. Then the <mark style="background: #ADCCFFA6;">kernal</mark> of T, denoted $ker(T)$, is the set of all vectors $\overrightarrow{x}\in \mathbb{R}^n$ such that
$$T(\overrightarrow{x})=\overrightarrow{0}$$

Note that $ker(T)=null(A)$

## the determinant of a square matrix
For every square n x n matrix A we want to assign a scalar, called the <mark style="background: #ADCCFFA6;">determinant</mark> of A, denoted by $\det(A)$ that satisfies
$$\det(A)=0\Leftrightarrow \text{A is not invertible (singular)}$$
$$\det(A)\ne0\Leftrightarrow \text{A is invertible (non-singular)}$$
Basically the determinant is the measure of if a matrix is invertible or not. <mark style="background: #BBFABBA6;">It is a bit of an arbitrary number that is only important because you can infer a lot of things from it</mark>

## characteristic polynomial of a square matrix
$\det(A-\lambda I)$ the <mark style="background: #ADCCFFA6;">characteristic polynomial</mark> of A
The roots of the characteristic equation are the eigenvalues of A

## eigenvalues, eigenvectors, and eigenspaces of square matrices
Let A be a square n x n matrix. We say a nonzero vector x is an <mark style="background: #ADCCFFA6;">eigenvector</mark>
 of A if $A\overrightarrow{x}=\lambda\overrightarrow{x}$ for some scalar $\lambda$
 We call $\lambda$ the <mark style="background: #ADCCFFA6;">eigenvalue</mark> associated to the eigenvector x
 The set of all eigenvectors associated with a given eigenvalue of a matrix is known as the <mark style="background: #ADCCFFA6;">eigenspace</mark> associated with that eigenvalue
 
# Topics to Review

## Determine whether or not a set is closed under addition and/or scalar multiplication.
A set is closed under addition if there is no vector you can add to v to push it out of it's span. For all elements $u,v\epsilon V$ (vectors u and v in V), then $\overrightarrow{u}+\overrightarrow{v}\in V$ it is closed

A set is closed under multiplication if there is no scalar value you can multiply it by to pus hit out of it's span. If for each $v\in V$ and scalar $k \in \mathbb{R}$, then $kv\in V$ it is closed

For example, if V only spans positive quadrants, is there any vector you can add to it to make it negative? Usually, you only need to consider 0, 1, and -1 when doing scalar multiplication and vector addition. Calculate it out if needed but it's usually conceptual enough

REMEMBER THAT U HAS TO BE IN V, YOU CAN'T JUST ADD WHATEVER TO IT. k can be whatever though

## Prove that a subset of $\mathbb{R}^n$ is or is not a subspace.
To be a subspace, it has to be closed under addition and scalar multiplication

NOTE: The span of a vector is a subspace and subspaces must contain the zero vector and inverse sets

A vector space has to follow the 10 vector space axioms in addition to closure and containing the 0 vector, while a subspace only has to have closure and the 0 vector and is usually a subspace of a vector space

## Determine whether a set of vectors is a basis of a subspace.
A set R of vectors is called a basis of $\mathbb{R}^n$ if:
1. $Span(R)=\mathbb{R}^n$ <-- existence question
2. R is linearly independent <-- uniqueness
Similarly, a basis of a subspace V of $\mathbb{R}^n$ is a set of vectors S that
3. $Span(S)=V$
4. S is linearly independent

IMPORTANT NOTES:
Remember that it's span is how many leading entries it has
Remember to show linear independence we need a leading entry in every column
This means to show that it is a basis of $\mathbb{R}^n$ you need to have a leading entry in every COLUMN and ROW of REF

Basis is always in the form $basis=\left\{\begin{bmatrix}1 \\ 1\end{bmatrix},\begin{bmatrix}1 \\ 1\end{bmatrix}\right\}$ or $basis=\left\{\begin{bmatrix}1 & 1\end{bmatrix},\begin{bmatrix}1 & 1\end{bmatrix}\right\}$

Basically to see if a vector is a basis just solve for REF and see if it has leading entries everywhere

## Write the coordinates of a vector with respect to a given basis.
You will be given something like: Find the coordinates of the vector $\overrightarrow{v}=\begin{bmatrix}2 \\ 6\end{bmatrix}$ with respect to $\left\{\begin{bmatrix}1 \\ 0\end{bmatrix},\begin{bmatrix}1 \\ 2\end{bmatrix}\right\}$.
It's very simple, you just multiply the columns of the basis by the rows of v, so in this case its
$2\begin{bmatrix}1 \\ 0\end{bmatrix}+6\begin{bmatrix}1 \\ 2\end{bmatrix}=\begin{bmatrix}2 \\ 0\end{bmatrix}+\begin{bmatrix}6 \\ 12\end{bmatrix}=\begin{bmatrix}8 \\ 12\end{bmatrix}$

## Identify the dimension of a subspace.
For a domain: $\mathbb{R}^n$, the dimension is n
For a vector, put it into REF and the number of vectors in its span is its dimension. For example, if a vector's span is $\left(\begin{bmatrix}1 \\ 2 \\ 0\end{bmatrix},\begin{bmatrix}0 \\ 1 \\ 1\end{bmatrix}\right)$, then the dimension is 2

NOTE: a subspace MUST contain the 0 vector as well as be closed under addition and multiplication

## Find a basis for the row, column, and null spaces of a matrix.
You basically just find the row, column, or null space and put it in a special format and that's the basis

ROW SPACE:
Find the RREF of the matrix. The row space is every row that has a pivot
For example, 
$A=\begin{bmatrix}1 & 3 & 2 \\ 0 & 2 & 0 \\ -1 & -1 & -3\end{bmatrix}\to RREF(A)=\begin{bmatrix}1 & 0 & 3 \\ 0 & 1 & 0 \\ 0 & 0 & 0\end{bmatrix}$
$basis=\{\begin{bmatrix}1&0&3\end{bmatrix},\begin{bmatrix}0 & 1 & 0\end{bmatrix}\}$
You just put the rows in a comma separated list

COLUMN SPACE:
Find the RREF of the matrix. Note which columns have a pivot in them. Unlike row space, these pivot columns ARE NOT directly the column space since columns are not preserved in row operations. Instead, the ORIGINAL VERSION of the pivot columns form the column space for the basis
For example, $A=\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}\overrightarrow{RREF}\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$
It has a pivot column in col 1, so $col(B)=\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}$
The basis of the column space is just the columns in comma separated form, so $basis=\left\{\begin{bmatrix}1 \\ 2 \\ 3\end{bmatrix}\right\}$

NULL SPACE:
The null space is any value that would cause the matrix to 0 out. You put a matrix in RREF form and solve it for = 0. Put it in vector form and that's the answer
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

## Understand the Rank-Nullity Theorem.
The nullity of a matrix A is $nullity(A)=dim(null(A))$
Suppose A is an m x n matrix. Then $rank(A)+nullity(A)=n$

Basically says that all pivot columns + all free columns = total columns
(Rank is equivalent to pivot columns and nullity is equivalent to free var columns)

## Interpret a matrix as a linear transformation (how do functions work?)
A function or transformation T from $\mathbb{R}^n$ to $\mathbb{R}^m$, denoted $T:\mathbb{R}^{n}\to \mathbb{R}^m$, is a mapping of vectors in $\mathbb{R}^n$ to vectors in $\mathbb{R}^m$.
- $\mathbb{R}^n$ is the domain
- $\mathbb{R}^m$ is the codomain
- For $x\epsilon \mathbb{R}^m$, the image of $\overrightarrow{x}$ is $T(\overrightarrow{x})$
- The set of all images of T is called the range (or images because mathematicians hate us)
![[Pasted image 20250417184840.png]]

A matrix transformation is a transformation $T:\mathbb{R}^n\to \mathbb{R}^m$ defined by $T(\overrightarrow{x})=A\overrightarrow{x}$ where A is an m x n matrix

## Find the standard matrix of a linear transformation
If we have a linear transformation $T:\mathbb{R}^2\to \mathbb{R}^m$ and $T(\overrightarrow{x})=A\overrightarrow{x}$, then
$A=\begin{bmatrix}1 & 1 & 1 \\ T(\overrightarrow{e_{1}}) & T(\overrightarrow{e_{2}}) & T(\overrightarrow{e_{3}}) \\ 1 & 1 & 1\end{bmatrix}$ for example. Basically you just summarize what a transformation will do in matrix form

For example, $T:\mathbb{R}^3\to \mathbb{R}^2$ defined by $T\left(\begin{bmatrix}x \\ y \\ z\end{bmatrix}\right)=\begin{bmatrix}5x+y \\ 7z\end{bmatrix}$
Another example is $h:\mathbb{R}\to \mathbb{R}^2$ defined by $h(x)=\begin{bmatrix}0 \\ x\end{bmatrix}$

To get the standard matrix of a transformation, you have to go a step further and just drop the variables and put it into matrix form, for example
$\begin{bmatrix}5x+y \\ 7z\end{bmatrix}\to \begin{bmatrix}5 & 1 & 0 \\ 0 & 0 & 7\end{bmatrix}$ where the columns represent variables. Another example would be $f(x)=\begin{bmatrix}0 \\ x\end{bmatrix}\to \begin{bmatrix}0 \\ 1\end{bmatrix}$

## Determine if a transformation is linear.
A transformation $T:\mathbb{R}^{n}\to\mathbb{R}^m$ is called a linear transformation if
1. $T(\overrightarrow{u}+\overrightarrow{v})=T(\overrightarrow{u})+T(\overrightarrow{v})$
2. $T(k\overrightarrow{u})=kT(\overrightarrow{u})$
for all vectors u and v in $\mathbb{R}^n$ and scalars k

KEY NOTES: Addition tends to break if there's any constants and multiplication tends to break if there's any exponents. Otherwise, it is usually linear

Basically just calculate the four scenarios and if all of them hold it is linear
1. It is the difference between doing $\begin{bmatrix}0 \\ x_{1}+x_{2}\end{bmatrix}$ and $\begin{bmatrix}0 \\ x_{1}\end{bmatrix}+\begin{bmatrix}0 \\ x_{2}\end{bmatrix}$. This is why constants tend to break it since you're adding the constants twice, so it wouldn't be equal. Note the given example is linear
2. Similarly, for multiplication it is the difference between doing $k\begin{bmatrix}0 \\ x_{1}\end{bmatrix}$ and $\begin{bmatrix}0 \\ kx_{1}\end{bmatrix}$, which is why exponents tend to break it since if one of your terms is $x^2$, then it'd be $(kx)^2$ which is different than $k(x^2)$

Theorem 6.2.11: Let A be an m x n matrix. Define $T:\mathbb{R}^n\to \mathbb{R}^m$ by $T(v)=Av$. Then T is a linear transformation
The identity and zero transformations are linear

## Find the basis for the image and kernel of a linear transformation. (Remember, if $T(x)=Ax$ for some matrix A, then $im(T)=col(A)$ and $ker(T)=null(A)$.

FOR IMAGES:
An image of a function is just the output if given a certain input. For example, if you have $f(x)=\begin{bmatrix}x \\ x^2\end{bmatrix}$, the image of -2 is $f(-2)=\begin{bmatrix}-2 \\ 4\end{bmatrix}$
For $\mathbb{R}^n$, the standard basic vectors are $e_{1}=\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$ $e_{2}=\begin{bmatrix}0 \\ 1 \\ 0\end{bmatrix}$, $e_{3}=\begin{bmatrix}0 \\ 0 \\ 1\end{bmatrix}$
The image of the basis vectors is the result of multiplying these vectors by the original one, example below
$S(x)=\begin{bmatrix}0 & -1 & 7 \\ 2 & 4 & 3\end{bmatrix}x$
$S(\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix})=\begin{bmatrix}0 & -1 & 7 \\ 2 & 4 & 3\end{bmatrix}\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$ <-- 1st column of the matrix
$S(\begin{bmatrix}0 \\ 1 \\ 0\end{bmatrix})=\begin{bmatrix}0 & -1 & 7 \\ 2 & 4 & 3\end{bmatrix}\begin{bmatrix}0 \\ 1 \\ 0\end{bmatrix}$ <-- 2nd column
$S(\begin{bmatrix}0 \\ 0 \\ 1\end{bmatrix})=\begin{bmatrix}0 & -1 & 7 \\ 2 & 4 & 3\end{bmatrix}\begin{bmatrix}0 \\ 0 \\ 1\end{bmatrix}$ <-- 3rd column

FOR KERNELS:
Let $T:\mathbb{R}^n\to \mathbb{R}^m$ be a linear transformation with standard matrix A. Then the kernel of T, denoted $ker(T)$, is the set of all vectors $\overrightarrow{x}\in \mathbb{R}^n$ such that
$$T(\overrightarrow{x})=\overrightarrow{0}$$
Note that $ker(T)=null(A)$
Literally all a kernel is is the nullspace of a matrix. You find the basis for a kernel the same way you find a basis for the nullspace, by just putting it in basis format

## Find coordinate vectors with respect to a given basis. 
Recall i and j as the standard unit vectors of $[1, 0]$ and $[0, 1]$
We can describe other vectors as linear combinations of these vectors.
$$\overrightarrow{v}=\begin{bmatrix}
a \\
b
\end{bmatrix}=a\begin{bmatrix}
1 \\
0
\end{bmatrix}+b\begin{bmatrix}
0 \\
1
\end{bmatrix}$$
When doing this, we say a and b are <mark style="background: #ADCCFFA6;">coordinates</mark> of v with respect to {i, j} and $\begin{bmatrix}a \\ b\end{bmatrix}$ is the <mark style="background: #ADCCFFA6;">coordinate vector</mark> of v with respect to {i, j}

Doing this with a basis, you just replace the standard unit vectors with the basis vectors
1. Set up the basis vectors in an augmented matrix with v as the solution, so if we have $v=\begin{bmatrix}2 \\ 6\end{bmatrix}$ with respect to $\left\{\begin{bmatrix}1 \\ 0\end{bmatrix},\begin{bmatrix}1 \\ 2\end{bmatrix}\right\}$ then the augmented matrix is $\begin{bmatrix}1 & 1 & | & 2 \\ 0 & 2 & | & 6\end{bmatrix}$
2. Solve the augmented matrix into REF, so $\begin{bmatrix}1 & 1 & | & 2 \\ 0 & 1 & | & 3\end{bmatrix}$
3. Solve the system of linear equations for the variables, which is $c_{2}=3$ and $c_{1}+c_{2}=2\to c_{1}=-1$
Therefore, the coordinate vector of v with respect to the basis is $\begin{bmatrix}-1 \\ 3\end{bmatrix}$

## Find the matrix representation of a linear transformation between abstract vector spaces.
shoot me

## Determine if a linear transformation is one-to-one, onto, or an isomorphism.
Let $T:V\to W$ be a transformation of vector spaces
1. If each vector $w\in W$ is the image of AT LEAST ONE vector $v\in V$, then T is onto
	1. Every element of W has at least one thing in V that maps to it. Many v's can point to a w as long as every w has a link
	2. If the rank < number of rows
2. If each vector $w\in W$ is the image of AT MOST ONE vector $v\in V$, then T is one-to-one
	1. Every element of V maps to one element in W. There are no free variables
3. We call T an isomorphism if it is BOTH onto and one-to-one
	1. There are 4 variables in v and w and each variable in v maps to one in w for example

Theorem: Let $T:V\to W$ be a transformation of vector spaces with matrix representation A with respect to some bases for V and W
1. T maps V onto W if and only if RREF(A) has a pivot in every row
2. T is one-to-one if and only if RREF(A) has a pivot in every column

## Find determinants using cofactor expansion along a row or column.
FOR A 1 x 1 MATRIX:
For a 1 x 1 matrix (a scalar), $A=[a]$, the determinant is just a, so $\det(A)=a$. Very simple. Notice that as long as a != 0, $a^{-1}=\frac{1}{a}$

FOR A 2 x 2 MATRIX:
If $A=\begin{bmatrix}a & b \\ c & d\end{bmatrix}$ is a 2 x 2 matrix, we define $\det(A)=ad-bc$
Recall and notice that if the matrix is invertible, then $A^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d & -b \\ -c & a\end{bmatrix}$
So, $\frac{1}{\det(A)}$ is the scalar you multiply a 2 x 2 matrix by to help invert it (you also need to move the matrix values around)

FOR A 3 x 3 MATRIX:
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

FOR A n x n MATRIX FOR N >= 3:
If $A=\begin{bmatrix}a_{ij}\end{bmatrix}$ is a n x n matrix, we define
$$
\det(A)=a_{11}*\det(A_{11})-a_{12}*\det(A_{12})+\dots+(-1)^{n+1}a_{1n}\det(A_{1n})$$
$A_{ij}=\text{matrix from detleting the ith row and the jth column of A}$
This is cofactor expansion. You just find a ton of sub-determinants. Along the column works the same way. It is easiest to find the determinant using the row or column with the most 0's

## Describe how row operations affect the determinant.
It basically just wants us to list a ton of properties, so I will

Let $A=[a_{ij}]$ be an n x m matrix
1. If B is obtained from A by interchanging two different rows or columns, then $\det B=-\det A$
2. If B is obtained from A by multiplying one of the rows or columns of A by a non-zero constant k. Then $\det B=k\det A$
3. If B is obtained from A by adding a multiple of one row or column of A to another row, then $\det B=\det A$

Extra:
1. $\det AB=\det A\det B$
2. $\det A^{-1}=\frac{1}{\det A}$
3. $\det kA=k^n\det A$
4. $\det(A+B)\neq \det(A)+\det(B)$

## Describe the significance of when the determinant is zero.
If the determinant is 0, it is not invertible (singular). Otherwise, it is invertible (non-singular)

Properties relating to it being 0:
1. If A has a row of zeroes, then $\det A=0$
2. If two rows of A are the same, then $\det A=0$
3. If one row of A is a scalar multiple of another row, then $\det A=0$

## Use characteristic polynomials to compute eigenvalues and eigenvectors.
The characteristic polynomial is $\det(A-\lambda I)$ and it's basically all you need
<mark style="background: #BBFABBA6;">Keep track of the operations you do when solving RREF, it will affect the determinant</mark>

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

## Finding the basis of the eigenspace
Given a lambda, do $A-\lambda I$ and solve into RREF. Find the nullspace, this is the eigenspace

# Test Observations
## Examples of ....
A 2-dimensional subspace of $\mathbb{P}^3$ is ... $a+bx$

Two different bases for $\mathbb{P}^2$ is ... $\{1,x,x^2\}$ and $\{2,x,x^2\}$

A linearly independent set with more than one vector in $\mathbb{M}_{2\times2}$ that does not span $\mathbb{M}_{2\times2}$ is ... $\left\{\begin{bmatrix}1 & 0 \\ 0 & 0\end{bmatrix},\begin{bmatrix}0 & 1 \\ 0 & 0\end{bmatrix}\right\}$

A linear transformation $T:\mathbb{R}^3\to\mathbb{P}^2$ that is an isomorphism is ... $T\left(\begin{bmatrix}a \\ b \\ c\end{bmatrix}\right)=a+bx+cx^2$