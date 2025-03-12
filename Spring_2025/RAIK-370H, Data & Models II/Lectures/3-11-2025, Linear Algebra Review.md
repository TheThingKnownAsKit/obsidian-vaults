![[08 Linear Algebra Overview.pdf]]

## 270 Review
Mean
$$\overline{x}=\frac{\sum^n_{i=1}x_{i}}{n}$$

Variance
$$var_{p}=\frac{\sum^n_{i=1}(x_{i}-\overline{x})^2}{n}$$
$$var_{s}=\frac{\sum^n_{i=1}(x_{i}-\overline{x})^2}{n-1}$$

Standard deviation
$$stdev_{p}=\sqrt{ var_{p} }=\sqrt{ \frac{\sum^n_{i=1}(x_{i}-\overline{x})^2}{n} }$$
$$stdev_{s}=\sqrt{ var_{s} }=\sqrt{ \frac{\sum^n_{i=1}(x_{i}-\overline{x})^2}{n-1} }$$

Covariance
$$covar_{p}(x,y)=\frac{\sum^n_{i=1}(x_{i}-\overline{x})*(y_{i}-\overline{y})}{n}$$
$$covar_{s}(x,y)=\frac{\sum^n_{i=1}(x_{i}-\overline{x})*(y_{i}-\overline{y})}{n-1}$$

Correlation
$$\rho_{A,B}=corrA,B=\frac{cov(A,B)}{\sigma_{A}\sigma_{B}}$$
Where $\sigma$ is the standard deviation

Linear Regression
![[Pasted image 20250311130223.png]]

## Linear Algebra Review
![[Pasted image 20250311130407.png]]

For matrix division just multiply by the inverse instead

We like matrices because they can use the GPU and it is much faster

The <mark style="background: #ADCCFFA6;">determinant</mark> is the size of a matrix. Kind of like the area. 
For 2x2 matrices
$$\det\left(\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}\right)=ab-dc$$
For larger matrices:
$$\det\left(\begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}\right)$$
![[Pasted image 20250311134422.png]]
![[Pasted image 20250311134437.png]]
![[Pasted image 20250311134449.png]]
You basically just multiply the top row by row item * 2x2 determinant of things not in its row or column and alternate + and -

The matrix of minors is finding the determinant of a > 2x2 matrix but you don't multiply by the current cell and you do it for every cell. Will output a matrix

The matrix of cofactors is just swapping signs in a checkered pattern. The positive pattern starts on the main diagonal, these ones keep their signs. The alternate checkered pattern swaps signs
Positive pattern
![[Pasted image 20250311135929.png]]
Negative pattern
![[Pasted image 20250311135939.png]]

The adjoint or adjugate matrix is just flipping the cofactor matrix along the main diagonal

The inverse is dividing the adjoint matrix by the determinant