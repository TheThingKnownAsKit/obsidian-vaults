![[2.3-student.pdf]]

---

![[2.4-student.pdf]]

So if you have $\frac{df}{dt}=f_{x}\frac{dx}{dt}+f_{y}\frac{dy}{dt}$, basically what you do is find the partial derivatives of the main function $T(x,y)$ or $z$ or $f$ or something for both x and y, and then also find the derivative of $x(t)$ and $y(t)$. Multiply the partial derivatives by their respective $x(t)$ or $y(t)$, add them together, and that's what f is.

Example
$$
\displaylines{x(t)=\cos(t)\\y(t)=\sin(t)\\T(x,y)=100-\frac{1}{2}x^2-3y^2}
$$
We need $T_{x}$, $T_{y}$, $\frac{dx}{dt}$, and $\frac{dy}{dt}$
$$
\displaylines{
\frac{dx}{dt}=-\sin(t)
\\ \frac{\\dy}{dt}=\cos(t)
\\ T_{x}=-x
\\ T_{y}=-6y
}
$$
Plug that into the formula and get: $\frac{df}{dt}=-x\cos(t)-6y\sin(t)$
**After you plug it into the formula, remember to substitute the x's and y's away.** We want to express this in terms of t, so substitute their original $x(t)$ and $y(t)$

So, the final result is $\frac{df}{dt}=-(\cos(t))\cos(t)-6(\sin(t))\sin(t)$


For chain rule with multiple variables problems, like
$$
\frac{\partial w}{\partial s}=\frac{\partial w}{\partial x}\frac{\partial x}{\partial s}+\frac{\partial w}{\partial y}\frac{\partial y}{\partial s}
$$
![[Pasted image 20260924165001.png]]
The nominator is what equation you should be looking at and the denominator is the active variable. Just map it out and solve it should be alright. Remember that the second partial denominator on the right hand side of the equation