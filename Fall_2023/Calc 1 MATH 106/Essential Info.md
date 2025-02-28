## Basic Essential
*Exponents*
$\frac{1}{x} = x^{-1}$
$\sqrt{x}=x^{\frac{1}{2}}$

*Fraction Operations*
To subtract/add fractions, give them a common denominator. (IMPORTANT WHEN DEALING WITH EXPONENT STUFF)
To multiply fractions, multiply the numerators by each other and the denominators by each other
To divide, flip the second fraction and then multiply.

*Quadratic Formula*
$x=\frac{-b\pm \sqrt{b^2-4(ac)}}{2a}$
For $ax^2+bx+x=0$

###### Long Division
![[Pasted image 20230917145048.png]]
![[Pasted image 20230917145109.png]]
![[Pasted image 20230917145219.png]]
![[Pasted image 20230917145234.png]]

## General Graphing
*Slope*
Slope formula: $\frac{y_2-y_1}{x_2-x_1}$
Point slope form: $y-y_1=m(x-x_1)$
Slope intercept form: $y=mx+b$

*Graph Transformations*
Vertical Stretch/shrink: $y= kf(x)$
Horizontal stretch/shrink: $y=f(kx)$
Reflect across x-axis: $y=-f(x)$
Vertical shift(+ is up): $y=f(x) \pm k$
Horizontal shift(+ is left): $y=f(x\pm k)$

*Finding Perpendicular/Parallel*
To find a perpendicular equation, put in y = mx + b format, take the opposite reciprocal of m, use the point given to find b, put back into y = mx + b format using b and the new m.
	NOTE: If the product of their slopes is -1, they are perpendicular
To find parallel, put in y = mx + b format, take m and plug in the given point to find b, put into y = mx + b using the new b and m.

*Function Forms*
Linear: y = mx + b where m is the slope and b is the y-intercept.
Exponential: $P=P_0a^t$, where $P_0$ is the initial quantity, a is the growth/decay factor, and t is time.
Natural Base Exponential: $P(t) = P_0*e^{kt}$, where k is the continuous rate of growth/decay (for growth, k > 0).
Periodic: $f(t)=A\sin(Bt)+k$ (or cos) where:
															|A| is the vertical stretch/shrink and the AMPLITUDE.
															|B| is the horizontal stretch/shrink and is related to the PERIOD of the function, P, by the formula: $P=\frac{2\pi}{|B|}$
																Note: If it's something like (t/b), just do 1/b
															K is the vertical shift and determines the MIDLINE.

*Inverse/Invertible*
A function is invertible if for every y it has exactly one x. (vertical AND horizontal line test)
Switch every x for y and solve for y. 

*Continuity and Differentiability*
A function is discontinuous if:
There is a jump/hole/removable/asymptote
These will restrict the interval of continuity
	Dividing by zero
	Taking the square root of a negative number
	Take the log (in any base) of zero or of a negative number
A function is undifferentiable if:
There is a discontinuity/cusp/corner/vertical tangent line
Watch out for piece-wise functions and abs value.
	NOTE: Being continuous does not mean it is differentiable, but if it is not continuous then it is NEVER differentiable.
*Intermediate Value Theorem*
If a function is continuous over [a, b] then there exists a value c so that f(c) = k.

*Secant and Tangent Lines*
Secant lines are the average slope from one point to another. Just a linear line connecting the two.
	Find the average slope and use a point in y = mx + b to find the line equation.
A tangent line is a linear line that only touches the graph in one spot, which is the instantaneous slope at that point.
	Find the instantaneous slope and use it's point in y = mx + b to find the equation.
	$y=f'(x_0)(x-x_0)+y_0$

*Least/Greatest Values of f(x) and f'(x)*
![[Pasted image 20230917125644.png]]
The smallest and largest values of f(x) are those locations where the vertical coordinate on the graph is the smallest and largest.
The smallest and largest values of the derivative f'(x) are where the slope of the function is smallest and largest.
![[Pasted image 20230917130336.png]]
(A,B) Note that f' is positive everywhere, meaning f is always increasing. Hence the greatest value is just the rightmost value, and the least is the leftmost.
(C,D) Directly from the graph.
(E,F) Since f'' gives the slope of the graph of f', f'' is greatest where f' is rising most rapidly, and least where it is falling most rapidly.

*Decreasing/Increasing and Concave Up/Down*
![[Pasted image 20230917111842.png]]
The function is increasing when, moving along the curve from left to right, the y-values are increasing.
The function is concave up when the slope of the function is increasing as we move along the curve from left to right.

The sign of f' gives the increasing vs. decreasing nature of the function. (is it below or above the x axis?)
The sign of f'' gives the concavity/convexity
	If f'' > 0 then the slope of f' is increasing; hence the shape is concave up/convex (it holds water)
	If f'' < 0 then the slope of f' is decreasing; hence the shape is concave down (the graph does not hold water)
NOTE: If there is an x in the second derivative the concavity will have a condition. Like it's concave when x > 0 and < 5 or something.

Making a table can be helpful.
For $f(x)=x^3+2x$
$f'(x)=3x^2+2$
$f''(x)=6x$
| Graph  | Pos/Neg                   | Pos/Neg | Signif Point | Pos/Neg                 | Pos/Neg |
| ------ | ------------------------- | ------- | ------------ | ----------------------- | ------- |
| x      |                           |         | 0            |                         |         |
| f'     | +                         | +       |              | +                       | +       |
| f''    | -                         | -       |              | +                       | +       |
| f info | Increasing & Concave Down |         |              | Increasing & Concave Up |         | 

HELPFUL:
If the slope of f(x) is negative, the graph of f'(x) wil be below the x-axis, positive then above.
All relative extrema of f(x) will become x-intercepts of f'(x)
All points of inflection of f(x) will become relative extreme of f'(x)
The derivative usually has one less turn than the original.

## Limits
*Limits*
$\lim_{h\to0} \left(\frac{f(x+h)-(f(x))}{h}\right)$
	NOTE: IT IS VERY HELPFUL TO REMEMBER THE MINUS GOES ON THE ENTIRE F(X) FUNCTION, FLIPPING ALL THE SIGNS.
Gives the instantaneous velocity at x. 
Properties of Limits:
* If b is a constant, then $\lim_{x\to c}(bf(x))=b\left(\lim_{x\to c}f(x)\right)$
* $\lim_{x\to c}(f(x) + g(x)) = \lim_{x\to c}f(x) + \lim_{x\to c}g(x)$
* $\lim_{x\to c}(f(x) * g(x)) = \lim_{x\to c}f(x) * \lim_{x\to c}g(x)$
* $\lim_{x\to c}\left(\frac{f(x)}{g(x)}\right) = \frac{\lim_{x\to c}f(x)}{\lim_{x\to c}g(x)}$, provided $\lim_{x\to c}g(x)$ != 0
* For any constant k, $\lim_{x\to c}k=k$
* $\lim_{x\to c}x=c$

The limit of f(x) only exists if the two side limits are equal. (looking at you piece-wise functions)
Even if there's a removable or not piece-wise discontinuity then the limit is where the discontinuity happens, not the actual result of f(x).
## Derivatives
[Derivative Rules]
*Derivative constant rule:* For any real number c, if f(x) = c then f'(x) = 0. The derivative of a constant is 0.
*Constant multiple rule:* For any real number k, if kf(x) then kf'(x)
*The sum rule:* f(x) + g(x) = f'(x) + g'(x)
*THE POWER RULE:* For any nonzero number n, if $f(x)=x^n$, then $f'(x)=nx^{n-1}$
*The derivative of exponential (natural base):* $e^x$ is just $e^x$
*The derivative of exponential (any base):* $a^x$ is $\ln(a)a^x$
*The product rule:* For $P(x)=f(x)*g(x)$ is $P'(x)=f'(x)g(x)+f(x)g'(x)$
*The quotient rule:* For $Q(x)=\frac{f(x)}{g(x)}$ and g(x) != 0 then $Q'(x)=\frac{f'(x)g(x)-f(x)g'(x)}{(g(x))^2}$
	NOTE: In the product rule, the order does not matter as long as it is consistent. It DOES MATTER in quotient.
*The chain rule:* For $C(x)=f(g(x))$ is $C'(x)=f'(g(x))*g'(x)$
	Very helpful to write out what f(x), f'(x), g(x), and g'(x) is before trying to solve.
	Can have to do the chain rule multiple times for one equation :)

[Derivatives of Trig Functions]
$\frac{d}{dx}\sin(x)=\cos(x)$
$\frac{d}{dx}\cos(x)=-\sin(x)$
$\frac{d}{dx}\tan(x)=\sec^2(x)$
$\frac{d}{dx}\cot(x)=-\csc^2(x)$
$\frac{d}{dx}\csc(x)=-\csc(x)\cot(x)$
$\frac{d}{dx}\sec(x)=\tan(x)\sec(x)$

[Derivatives of Inverse Functions]
Remember for all of these that it's chain rule. Multiply by derivative of inside function.
*The derivative of ln:* $\frac{d}{dx}\ln(x)=\frac{1}{x}$ for all positive real numbers
	Ln is an inverse function so that's why it's here i dont know my brain hurts im crying.
*Derivative of inverse sine:* $\frac{d}{dx}[\arcsin(x)]=\frac{1}{\sqrt{1-x^2}}*g'(x)$
*Derivative of inverse tangent:* $\frac{d}{dx}[\arctan(x)]=\frac{1}{1+x^2}*g'(x)$
*Derivative of inverse cosine:* $\frac{d}{dx}[arccos(x)]=-\frac{1}{\sqrt{1-x^2}}*g'(x)$
*Derivative of an inverse function:* $\frac{d}{dx}[f^{-1}(x)]=\frac{1}{f'(f^{-1}(x))}*g'(x)$

[Application of Derivatives]
*Velocity, Acceleration and Rate of Change*
Derivatives give instantaneous velocity and/or rate of change.
The average velocity of the object on the interval from t = a to t = b is denoted $AV_{[a,b]}$ and is given by the formula:
	$AV_{[a,b]} = \frac{s(b)-s(a)}{b-a}$

For word problems and finding what the derivative is measuring, it is helpful to just divide y/x.
Like if C(r) is the total cost of paying off a loan at an annual interest rate of r percent, then C'(r) is dollars per percent or dollars/percent.
	C(r) gives dollars and the x is percent.

Acceleration is the second derivative.
## Trigonometry
*Trig Functions*
SOH CAH TOA
S:$\frac OH$ C:$\frac AH$ T:$\frac OA$

Sine: $\sin(x)$
Cosine: $\cos(x)$
Tangent: $\frac{\sin(x)}{\cos(x)}$
Cotangent: $\cos(x)\sin(x)$ OR $\frac{1}{\sin(x)}$   Reciprocal of tan
Secant: $\frac{1}{\cos(x)}$                                    Reciprocal of cos
Cosecant: $\frac{1}{\sin(x)}$                                 Reciprocal of sin

![[Pasted image 20230917135826.png]]
![[Pasted image 20230917140601.png]]

*Unit Circle*
![[Pasted image 20230917121409.png]]
1 degree = $\frac{\pi*radians}{180}$
1 radian = $\frac{\pi}{180}$
To convert between the two, multiply the number of radians/degrees by the appropriate equation to find its value in the other measurement.
## Logarithms
![[Pasted image 20230917145743.png]]

*Properties of Logarithms*
$\log(xy)=\log(x)+\log(y)$     Same for ln
$\log\left(\frac xy \right)=\log(x)-\log(y)$    Same for ln
$\log(x^k)=k*\log(x)$              Same for ln
$\log(10^x)=x$                         $\ln(e^x)=x$
$10^{\log(x)}=x$                           $e^{ln(x)}=x$

*e and ln*
ln is the opposite of $e^x$. 
![[Pasted image 20230917114258.png]]
e^(the whole thing youre applying it to including ln) is the opposite of ln. Simplifies to the expression without e or ln.

