![[2.6-student.pdf]]

A <mark style="background: #ADCCFFA6;">critical point</mark> of a function is a point in the domain where its first-order partial derivatives equal 0 OR when the first-order partial derivatives fail to exist.
- You just find $f_{x}$ and $f_{y}$ and set them equal to 0 and solve for the variables.

![[Pasted image 20261008153433.png]]
You can calculate the determinant as the cross product of all the second order derivatives. So,
$$
D=\begin{bmatrix}
f_{xx} & f_{xy} \\
f_{yx} & f_{yy}
\end{bmatrix}=f_{xx}(x_{0},y_{0})f_{yy}(x_{0},y_{0})-f_{xy}(x_{0},y_{0})^2
$$

If you are optimizing on a restricted domain, find the critical points and then test the boundary points as well. So if you have a boundary of $0 \leq y\leq 1$, find the regular critical points and then also test y is 0 and 1.
![[Pasted image 20261008153748.png]]
