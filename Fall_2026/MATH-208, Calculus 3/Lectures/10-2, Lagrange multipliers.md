![[2.7-student.pdf]]

You can find the min/max of a function and its critical points by using Lagrange multipliers

Solve the below system of equations:
$$
\begin{matrix}
\nabla f=\lambda\nabla g \\
g(x,y)=c
\end{matrix}
$$
Lambda and c are just scalars. g has to become parallel to f via lambda.

1. Calculate $\nabla f$ and $\nabla g$
2. Set up your system of linear equations in
$$\begin{matrix}
\lambda g_{x}=f_x \\
\lambda g_{y}=f_y \\
\lambda g_{z}=f_z \\
g(x,y,z)=c
\end{matrix}$$
3. Solve the system for the critical points. You can do this by either substitution (solve xyz in terms of $\lambda$) or by eliminating $\lambda$
	1. SUBSTITUTION:
		1. Solve the first three equations for xyz in terms of $\lambda$. We will call these $x_{\lambda},y_{\lambda},z_{\lambda}$
		2. Substitute these into the constraint equation so $g(x_{\lambda},y_{\lambda},z_{\lambda})=c$. Solve for $\lambda$
		3. Plug the $\lambda$ value you just got back into $x_{\lambda},y_{\lambda},z_{\lambda}$ to get the actual $(x,y,z)$ coordinates
	2. ELIMINATION (usually worse):
		1. Solve the first three equations for $\lambda$, so $\lambda=\frac{f_{x}}{g_{x}}$
		2. Set these equations equal to each other, so $\frac{f_{x}}{g_{x}}=\frac{f_{y}}{g_{y}}$ to find the direct algebraic relationship between xyz
		3. Substitute that relationship into the constraint equation $g(x,y,z)=c$ to solve for the coordinates
	3. Evaluate f at every critical point. So, take the xyz from either substitution or elimination and plug it into $f(x,y,z)$. The largest number from this is the max and the smallest is the min