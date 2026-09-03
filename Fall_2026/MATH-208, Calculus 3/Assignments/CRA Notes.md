# Geometry Review
## Equation for a line passing through a point and perpendicular to a line

1. Find the slope of the perpendicular line. Remember that slope-intercept form $y=mx+b$ has m as the slope and b as the y intercept
2. Lines perpendicular to each other have negative reciprocal's of each other's scope, so you can find the slope of the line by doing $-\frac{1}{m}$
3. Put the values in point-slope form, $y-y_{1}=m(x-x_{1})$, substituting in the values from point p
4. Solve

## Extracting standard form values from the polynomial form of an ellipse
You have to complete the square basically. You'll get an equation in the form of $x^2+y^2=1$ or something and have to find the values from the standard form of an ellipse, which is:
$$
\frac{(x-h)^2}{a^2}+\frac{(y-k)^2}{b^2}=1
$$
1. **Group the variables and isolate the constant** if it hasn't been done already. You should have something like (all the x terms) + (all the y terms) = the constant. Most likely you will have an x and x^2 term, if you don't, put a 0 substitute in
2. **Factor out the leading coefficients** of the x and y groups
3. **Complete the square** for both x and y. Typically, you take the coefficient of the linear term (x or y without the square), divide it by 2, and square the result. Add this number inside the parentheses to both groups. THIS INCLUDES balancing the right side of the equation. Add the factored out coefficient to the number you just added inside the parenthesis to the right hand side of the equation to balance out the new things added
4. **Rewrite as a perfect square binomial** so just condense the expressions into squared binomials
5. **Set the equation to 1** by dividing the entire thing by what the constant has simplified to on the right hand side. It should now be in the standard form for an ellipse

Example: $4x^2+9y^2-16x+18y-11=0$
1. $(4x^2-16x)+(9y^2+18y)=11$
2. $4(x^2-4x)+9(y^2+2y)=11$
3. $4(x^2-4x+4)+9(y^2+2y+1)=36$
	1. For the x add value, $\left( -\frac{4}{2} \right)^2=4$
	2. For the y add value, $\left( \frac{2}{2} \right)^2=1$
	3. For the right hand side, $11+4(4)+9(1)=36$
4. $4(x-2)^2+9(y+1)^2=36$
5. $\frac{(x-2)^2}{9}+\frac{(y+1)^2}{4}=1$
6. So in this case, $h=2,k=-1,a=3,b=2$

## Finding a point on a plane that is equidistant from two given points
If a point lies on a specific axis, it's value in the other axis will be 0. For example, if you're trying to find a point on the x-axis plane, it would follow the format (x, 0), and if you wanted one on the y-axis plane, it would be (0, y). That is half the point done

After that,
1. Find the distance between the two points from each other. If you've got points $A(x_{1,y_{1}})$ and $B(x_{2},y_{2})$, then it'll be $(x-x_{1})^2+(y-y_{1})^2=(x-x_{2})^2+(y-y_{2})^2$
2. Plug in known zeroes, so either all y's or all x's
3. Expand and solve, the resulting x or y value is the second point besides 0

## Defining a region bounded by circular arcs and straight lines in polar coordinates
![[Pasted image 20260901143053.png]]
This is what I mean by that.

If you want to know the radial boundaries (aka the region bounded between two concentric circular arcs), you've got to find the maximum radius and minimum radius of the region
TODO: JUST ASK MORE ABOUT POLAR COORDINATES IN GENERAL BECAUSE ???


# Derivative Review
![[Pasted image 20260901143417.png]]

| Function      | Derivation                  |
| ------------- | --------------------------- |
| $\sin(x)$     | $\cos(x)$                   |
| $\cos(x)$     | $-\sin(x)$                  |
| $\tan(x)$     | $\sec^2(x)$                 |
| $\sec(x)$     | $\sec(x)\tan(x)$            |
| $\csc(x)$     | $-\csc(x)\cot(x)$           |
| $\cot(x)$     | $-\csc^2(x)$                |
| $\arcsin(x)$  | $\frac{1}{\sqrt{ 1-x^2 }}$  |
| $\arccos(x)$  | $-\frac{1}{\sqrt{ 1-x^2 }}$ |
| $\arctan(x)$  | $\frac{1}{1+x^2}$           |
| $e^x$         | $e^x$                       |
| $a^x$         | $a^x\ln(a)$                 |
| $\ln(x)$      | $\frac{1}{x}$               |
| $\log_{a}(x)$ | $\frac{1}{x\ln(a)}$         |

# Integral Review
