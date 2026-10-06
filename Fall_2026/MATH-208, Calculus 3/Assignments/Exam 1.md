
## Section 1.1: Functions of many variables
Topics and important equations we covered:
- graphs of functions of two variables
	- A function f of two independent variables is a rule that assigns to each pair (x, y) in some domain D exactly one real number f(x, y)
- traces
	- Traces is when you have a function with two or more variables and you fix all but one and let the other vary. So you can have a y-trace, x-trace, z-trace.
- contour maps
	- A level curve (or contour) of a function $f=f(x,y)$ of two variables is a curve of the form $f(x,y)=k$ where k is a constant
	- ![[Pasted image 20261001100826.png]]

Motivating Questions:
- What is a function of several variables? What do we mean by the domain of a function of several variables?
	- It is a way to map two or more inputs to one output. Usually models a relationship of some kind. The domain of a function is the range of possible values you could give as input and still be defined.
- How do we find the distance between two points in ℝ?
	- $\sqrt{ (x_{2}-x_{1})^2 }$
- What is the equation of a sphere in ℝ?
	- $(x-x_{0})^2=R^2$ where R is radius
- What is a trace of a function of two variables? What does a trace tell us about a function?
	- A trace is when you hold one of the two variables constant and allow the other to vary
	- This shows you a sort of preview of the trend of one of the variables. You can see how it behaves without having to worry about the other one, which would make the data much more complicated to analyze.
- What is a level curve/contour of a function of two variables? What does a level curve/contour tell us about a function?
	- A level curve (or contour) of a function $f=f(x,y)$ of two variables is a curve of the form $f(x,y)=k$ where k is a constant
	- It can help construct the graph of a function of two variables. It is sort of like projecting (not in the mathematical sense) a 3D graph onto a flat surface, like elevation maps. It gives us key information and a vague idea of its 3D shape.
	- It also tells us the concavity of a graph. If the contour lines are getting closer together, it is concave up, and if they are getting further apart, they are concave down. Getting closer/further apart as the function INCREASES.
	- ![[Pasted image 20261001110640.png]]
## 1.2: Vectors
Topics and important equations we covered:
- basic algebra of vectors
	- If you add/subtract them just add/subtract their terms
	- If you multiply/divide them just multiply/divide their terms
	- If you scale them just multiply all terms by the scalar
- magnitude
	- Magnitude is the length, found using the Distance Formula. Remember vectors have already done $x-x_{0}$ just by putting themselves into vector form.
	- $|v|=\sqrt{ x^2+y^2+z^2 }$
- direction
	- Direction is it's direction :)
	- To find the vector in the direction of v, it's $\frac{v}{|v|}$
- translation-invariance
	- Doesn't care where it is
- geometric interpretation of vector operations
	- ![[Pasted image 20261001102320.png]]

Motivating Questions:
- What is a vector?
	- A vector is a line with direction and magnitude that is position independent. It is made up of components (individual points/coordinates)
- What does it mean for two vectors to be equal?
	- They have the same direction and magnitude. Position is irrelevant
- How do we add two vectors together and multiply a vector by a scalar?
	- Add corresponding terms
	- Multiply all terms by the scalar
- How do we determine the magnitude of a vector? What is a unit vector, and how do we find a unit vector in the direction of a given vector?
	- The magnitude is the distance formula
	- The unit vector is the vector with magnitude 1 (any direction)
	- The unit vector in the direction of vector v is $\frac{v}{|v|}$ so just the vector divided by its magnitude which makes a lot of sense if you think about it
## 1.3: Dot product
Topics and important equations we covered:
- computing the dot product, basic dot product algebra
	- It is just the rows multiplied together and summed if you put it in matrix form (put it in matrix form). Results in a scalar
	- It follows the same basic properties as regular multiplication
- dot product & orthogonality
	- If the dot product of two vectors is 0 they are orthogonal
- uv = |u||v| cos(𝜃)
	- If u and v are two vectors and theta is the angle between them, then $u\cdot v=|u||v|\cos \theta$. That's DOT PRODUCT not multiplication
	- If their dot product is < 0, theta is obtuse. If it = 0, it is 90 degrees (or pi). If it is > 0 it is acute
- work, force, and displacement
	- ![[Pasted image 20261001124439.png]]
	- Work: $W=F\cdot AB=|F||AB|\cos \theta$
	- AKA, the work is determined only by the magnitude of the force applied parallel to the displacement
- projections: geometric & algebraic
- ![[Pasted image 20261001123750.png]]
- To find the projection of u onto v, we need a component parallel to v and one perpendicular to v.
	- TLDR: We need a vector that points in the same direction as v but has a length of $|u|\cos \theta$
- Two equations, both equivalent: $proj_{v}u=|u|\cos \theta \frac{v}{|v|}=\left( \frac{u\cdot v}{v\cdot v} \right)v$
- This is u onto v. The subsymbol goes first because it's prettier. Remember the one BELOW the one we want to project to goes as the smaller symbol. Projecting ONTO something BELOW us
- The component of u along v is just them separated, so $comp_{v}u=\frac{u\cdot v}{|v|}$ which is a scalar

Motivating Questions:
- How is the dot product of two vectors defined and what geometric information does it tell us?
- How can we tell if two vectors in ℝ𝑛 are perpendicular?
	- Dot product is 0
- How do we find the projection of one vector onto another?
	- Above
## 1.4: Cross product
Topics and important equations we covered:
- computing the cross product
	- ![[Pasted image 20261001124814.png]]
	- The outside pattern is - then + then - then + on and on
- geometric interpretation of the cross product
	- $u\times v$ is orthogonal to BOTH u and v, direction determined by the right hand rule. (i.e. $i\times j=k$)
	- The magnitude of the cross product can be made greater by lengthening either u or v
	- It is greatest when the angle between u and v is 90 degrees
	- IMPORTANT: $|u\times v|=|u||v|\sin \theta$ so kind of similar to the same rule for dot product just with sign.
	- Properties:
		- $u\times v=-(v\times u)$
		- $(u+v)\times w=(u\times w)+(v\times w)$
		- Constants are constants
		- $u\times v=0$ IF u and v are parallel
		- it is NOT associative!!!!
- length of u times v
- parallelograms and parallelepipeds
	- The area of a parallelogram is the same thing as the magnitude of v cross u aka the vectors spanning it.
	   ![[Pasted image 20261001125449.png]]
	   - Parallelepipeds are just 3d parallelograms. Its volume is base times height, and you can find the area of the base as above. The height  is a tad more complicated, at $height=|w||\cos \alpha|$
	   - $Volume=|u\times v||w||\cos \alpha|=|(u\times v)\cdot w|$
	     ![[Pasted image 20261001125824.png]]

Motivating Questions:
- How and when is the cross product of two vectors defined?
	- Calculate as seen above
- What geometric information does the cross product provide?
	- The area spanned by two vectors.
## 1.5: Lines & planes in space
Parameterization is just using t has a variable in x(t) equations and such. You HAVE To do it for 3D lines.

Topics and important equations we covered:
- parameterized lines
	- A line in 3 space has to be parametrized because we can't represent it in simple point slope format line a 2d line. It needs a DIRECTION VECTOR and a STARTING POINT. You take this and you put all three variables into terms of t. Putting things into terms of t is basically what parametrizing is.
	- The parametric equation for a line through the point $P=(x_{0},y_{0},z_{0})$ in the direction of the vector $v= <a,b,c>$ are $\matrix{x(t)=x_{0}+at \\ y(t)=y_{0}+bt \\ z(t)=z_{0}+ct}= <x_{0},y_{0},z_{0}>+t<a,b,c>$
	- Typically in the form $r(t)=something$
- equation for plane
	- $a(x-x_{0})+b(y-y_{0})+c(z-z_{0})=0$ OR
	- $<a,b,c>\cdot<x-x_{0},y-y_{0},z-z_{0}>=0$
		- $n=<a,b,c>$ and IS ORTHOGONAL TO THE PLANE (remember you can find orthogonal things by taking the cross product)
		- So to find the equation of a plane, vectorized, you need an orthogonal vector and a point on the plane
- parametrizing the intersection of two planes
	- If you have two planes v and u, set their equations equal to each other and solve as a system of linear equations using substitution and elimination. Solve for x, y, and z. This is all your naught variables, so $x_{0},y_{0},z_{0}$.
	- Find the vector normal to these two planes, so the cross product of the vectors. This is your $<a,b,c>$ vector.
	- Take the naught values and the normal vector and plug it into $\matrix{x(t)=x_{0}+at \\ y(t)=y_{0}+bt \\ z(t)=z_{0}+ct}$ 
- equation for a plane spanned by three points
	- Write out a vague diagram that's probably inaccurate just to help keep track of info. Label your points as a, b, and c
	- Find two vectors, both originating from the same point. So $v=AB$ and $u=AC$, for example
	- Remember, for a plane, you need a point on the plane and a vector normal to the plane. You already have a point on the plane, you just need the normal vector. Take the cross product of v and u to find the normal plane
	- Put it into $<a,b,c>\cdot<x-x_{0},y-y_{0},z-z_{0}>=0$ format. Simplify if you want

Motivating Questions:
- How are lines in ℝ3 similar to and different from lines in ℝ2?
	- It is still a line. A path connecting two points. It is NOT represented in point slope format. The problem is we essentially have 4 dimensions, 3 from xyz, and then 4 as the result of those inputs. We can't represent that normally since we are not 4D, so we use time as the 4th dimension (or whatever else you want really but time is the most applicable). Because you can't visually represent 4 dimensions the same way as 3 dimensions, you have to represent a line as parametrized functions of all three variables instead of something as easy as point sloep form.
- What is the role that vectors play in representing equations of lines, particularly in ℝ3?
	- It gives you the slope basically? That's not exactly right but you need a vector in the direction of where you want to go to parametrize the equation and the value of that vector is what you multiply t by.
- How can we think of a plane as a set of points determined by a point and a vector?
	- A plane is just a specific x slope and y slope + any constant offsets. It is linear. Also, if we multiply by something orthogonal to the plane, I think it just of smushes any possible output to be on that plane since orthogonal = 0??? not sure
- How do we find the equation of a plane through three given non-collinear points?
	- Described above
## 1.6: Vector-valued functions
Topics and important equations we covered:
- determine paramterizations of circles and other curves in ℝ2 and ℝ3
	- In r2: $<a,b>+R<\cos t,\sin t>=<a+R\cos t,b+R\sin t>$
	- In r3 you HAVE to use parametrized vector-value function because of reasons stated on the parametrizing section. So, it would become $r(t)= <x(t),y(t),z(t)>$

Motivating Questions:
- What is a vector-valued function? What do we mean by the graph of a vector-valued function?
	- A vector-valued function is a function whose input is a real parameter t and whose output is a vector. t is a time variable. So, r(t) is the position of something at time t. Burn this into your head, a vector-valued function is a function of the position of something at time t.
		- $r(t)= <x(t),y(t),z(t)>$
	- The graph of a vector-valued function is always a curve. It is a collection of terminal points of vectors emanating from the origin. So if you had a vector who's endpoint was on the curve and origin was the origin.
- What is a parameterization of a curve in ℝ2? In ℝ3? What can the parameterization of a curve tell us?
	- The parameterization of a curve in R2 is just $<a,b>+R<\cos t,\sin t>$
	- The parameterization of a curve in R3 will be three t equations for x,y,z because of the same reasons you have to parameterize 3D lines
## 1.7: Motion and velocity vectors
Topics and important equations we covered:
- compute velocity and acceleration vectors given position vector
	- The velocity is the derivative of the vector-valued function
		- Magnitude is the speed (scalar)
		- Direction is the direction of motion
	- Acceleration is the second derivative of the vector-valued function
	- The velocity should be computed component-wise, so the velocity of the whole of r(t) is the partial derivative of all its terms in one vector
		- $v(t)=r'(t)= <x'(t),y'(t),z'(t)>$
- v(𝑡) = r′(𝑡)
	- Velocity
- a(𝑡) = v′(𝑡) = r″(𝑡)
	- Acceleration
- compute speed as a function of time given the position vector
	- Speed is $|v(t)|=|r'(t)|$ so magnitude of velocity
- tangent lines of parameterized curves
	- $L(t)=r(a)+tr'(a)$ is tangent to the curve, where a is the input value we are trying to find the tangent line to at, and r'(a) is the whole vector-valued function

Cute and important and cool thing to remember: the product rule also applies to dot products

Motivating Questions:
- What do we mean by the derivative of a vector-valued function and how do we calculate it?
	- The derivative of a vector-valued function is the array of all its partial derivatives. You calculate the partial derivatives and put them in an array.
- What does the derivative of a vector-valued function measure?
	- Velocity
- What do we mean by the integral of a vector-valued function and how do we compute it?
	- The integral of a vector-valued function is how much distance it traveled after t time. Compute it by computing the integral of all the components and putting them in an array.
- How do we describe the motion of a projectile if the only force acting on the object is acceleration due to gravity?
	- $r(t)=\langle v_{0}\cos(\theta)t+x_{0},-\frac{g}{2}t^2+v_{0}\sin(\theta)t+y_{0} \rangle$

## 1.8: Arc length
Topics and important equations we covered:
- set up definite integral for arc length
	- Arc length is the distance traveled on a curve, which is the integral of the speed of a function, and the speed is the magnitude of velocity
		- speed = magnitude of velocity = $|r'(t)|=|v(t)|$
		- So distance is $\int^b_{t=a}|v(t)|dt$
	- Arc length is only this if v(t) is never the zero vector so the particle never stops or changes direction
	- The circumference of a circle is just the arc length of literally the whole thing
- $L=\int^b_{a}|r'(t)|dt=\int^b_{a}|v(t)|dt$
	- Remember they mean magnitude with the single bars not abs val
	- This is the arc length

Motivating Questions:
- How can a definite integral be used to measure the length of a curve in 2-or 3-space?
	- $L=\int^b_{a}|r'(t)|dt=\int^b_{a}|v(t)|dt$
## 2.1: First-order partial derivatives
Topics and important equations we covered:
- partial derivatives as derivatives of traces
- estimating partial derivatives with difference quotient
	- The difference quotient is $\frac{f(a+h)-f(a)}{h}$ at a point a where a single variable (i.e. x = a) which is the average rate of change of f over the interval [a, a+h]
	- Use this if you have a table and nothing else
	- You can also use this with contour maps to estimate the slope at that point. It's just change in z/change in y or x. 
- inferring signs of partial derivatives from contour maps
	- TODO
- computing partial derivatives

Motivating Questions:
- How are the first-order partial derivatives of a function 𝑓 (𝑥, 𝑦) of the independent variables 𝑥 and 𝑦 defined?
- Given a function 𝑓 of the independent variables 𝑥 and 𝑦, what do the first-order partial derivatives 𝑓𝑥 and 𝑓𝑦 tell us about 𝑓 ?
## 2.2: Second-order partial derivatives
Topics and important equations we covered:
- the second-order homogeneous partial derivatives as concavity of traces
	- $f_{xx}$ measures the concavity of the x-trace. It is concave DOWN if < 0 and UP if > 0
	- $f_{yy}$ measures the concavity of the y-trace. It is concave DOWN if < 0 and UP if > 0
- Clairaut’s Theorem
	- Mixed partials measure "twisty-ness". Let f be a function of several variables for which the partial derivatives are continuous near the point (a, b). Then, $f_{xy}(a,b)=f_{yx}(a,b)$. They are interchangeable
	- Pick the easier one to calculate

Motivating Questions:
- Given a function 𝑓 of two independent variables 𝑥 and 𝑦, how are the second-order partial derivatives of 𝑓 defined?
- What do the second-order partial derivatives 𝑓𝑥𝑥, 𝑓𝑦𝑦, 𝑓𝑥𝑦, and 𝑓𝑦𝑥 of a function 𝑓 tell us about the function’s behavior?
	- ![[Pasted image 20261001110632.png]]
## 2.3: Linearization and tangent planes
Topics and important equations we covered:
- computing the tangent plane from the partial derivatives
	- To find a tangent plane, you need the slope in the x direction, the slope in the y direction, and a point on the plane.
	- $z=f_{x}(x_{0},y_{0})(x-x_{0})+f_{y}(x_{0},y_{0})(y-y_{0})+f(x_{0},y_{0})$
	- this is LINEARIZATION
- using tangent plane (= linearization) to estimate nearby values of the function
	- Finding the tangent plane to something to estimate nearby values. Turn a non-linear function into a linear function at a point to estimate it over short distances
- computing differentials
	- The differential is just $f_{x}(x_{0},y_{0})\Delta x+f_{y}(x_{0},y_{0})\Delta y$. So like basically just the slope times the change in the variables

Motivating Questions:
- What does it mean for a function of two variables to be locally linear at a point?
	- At a specific point, you can represent it as a linear function
- How do we find the equation of the plane tangent to a locally linear function at a point?
	- Above
- What is the differential of a multivariable function of two variables and what are its uses?
## 2.4: Chain rule
Topics and important equations we covered:
- compute a derivative of composite functions
	- $\frac{dz}{dt}=\frac{\partial z}{\partial x}\frac{dx}{dt}+\frac{\partial z}{\partial y}\frac{dy}{dt}$
	- It's always partial of variable in the z equation to partial of the variable in the parametric equation all added together for all variables
- tree diagrams
	- ![[Pasted image 20261001143153.png]]

Motivating Questions:
- What is the Chain Rule and how do we use it to find a derivative?
	- For when you have an outer function and an inner function, both with a derivation term
- How can we use a tree diagram to guide us in applying the Chain Rule?
	- Keeps track of the bullshit. Helps apply the chain rule for parametrized equations. Shows that you need to multiply the partials with respect to z by the derivatives with respect to t and add them all together (add each branch)
## 2.5: Directional derivatives and the gradient
Topics and important equations we covered:
- compute directional derivative
	- Directional derivative in the direction of vector u is $D_{u}f(x,y)= <f_{x}(x,y),f_{y}(x,y)\cdot u>=\nabla f(x,y)\cdot u$
		- 1. Find the gradient (which is just a vector of the partial derivatives)
		- 2. Verify if u is a unit vector or not
		- 3. If it is not a unit vector, turn it into one by $\frac{u}{|u|}$ so find the magnitude and divide by it
		- 4. Compute the dot product of the unit vector u and the gradient
	- So tldr the directional derivative in the direction of vector u is equivalent to the dot product of the gradient
	- It represents the rate of change per unit change in (x, y)
		- REMEMBER THAT U HAS TO BE A UNIT VECTOR. We want to get the rate of change per UNIT, so we need it to be the unit vector
- estimating directional derivatives
	- You can estimate "change in (x,y)" by $\Delta_{(x,y)}=|\Delta_{(x-y)}u|$
- the direction of the gradient
	- The direction of the gradient is the direction of steepest ascent. Aka it is perpendicular to the dot/line. Orthogonal to the level curve
- the magnitude of the gradient
	- The magnitude of the gradient is the rate of change in the direction of the gradient AKA it is the rate of greatest increase

Motivating Questions:
- The partial derivatives of a function 𝑓 (𝑥, 𝑦) tell us the rate of change of 𝑓 (𝑥, 𝑦) in the direction of the coordinate axes. How can we measure the rate of change of 𝑓 (𝑥, 𝑦) in other directions?
	- Use a different function ?????
- What is the gradient of a function and what does it tell us?
	- The gradient is the function that points in the direction of maximum change. It is a 2D vector that points in the direct of steepest ACCENT. $\nabla f(x,y)= <f_{x}(x,y),f_{y}(x,y)>$
	- It is tangent to the contour line at a point.
	- The magnitude of the gradient is a directional derivative in the direction of the gradient.
