![[12 Gradient Descent.pdf]]

The premise of this is that instead of calculating the center of the data (the mean), we just make a guess, calculate the error, and make a better guess based on that

We are doing an <mark style="background: #ADCCFFA6;">optimization</mark> problem to select the best value of a function based on some criteria. More specifically this is an example of <mark style="background: #ADCCFFA6;">convex optimization</mark> where it creates a convex curve and the minimum point is optimal

We call the error function a <mark style="background: #ADCCFFA6;">cost</mark> function. It is the cost associated with a given value

1. Make a guess
2. Calculate the error from the guess to every point
	1. Use mean square error, $$MSE=E(\mu)=\frac{1}{n}\sum^n_{i=1}(x_{i}-\mu)^2$$
3. Take the derivative of the error function to give us the <mark style="background: #ADCCFFA6;">gradient</mark>, which is a directional derivative. This gives us the instantaneous slope (rate of change) at the select point. <mark style="background: #BBFABBA6;">This will give us the direction to move for our next guess</mark>
	1. After some chain rule fuckery, it ends up as this $$-\frac{2}{n}\sum^n_{i=1}(x_{i}-\mu)$$
4. Update your guess based on the gradient. Move in the OPPOSITE direction of the gradient. For instance, if the slope is -8, go positive
5. Repeat until optimization condition is met. Typically for a set number of iterations

The more guesses you make, the more the mean squared error plot will look like a parabola
![[Pasted image 20250327132931.png]]
The point of minimum error (therefore the best fit) is the bottom of the parabola. We want to find this parabola line without blindly guessing

Instead of bouncing back and forth between the two arms of the parabola, we can use a <mark style="background: #ADCCFFA6;">learning rate</mark> to control the rate of learning. It is how much the guess can change at each iteration
$$guess=guess-(gradient*learning\ rate)$$
The learning rate is called a <mark style="background: #ADCCFFA6;">hyperparameter</mark>, which you set before building the model. It is a parameter that will impact your final model, although the value itself is not ultimately a part of the final model
NOTES:
- A high learning rate (such as 1.05) can move the guess out of the convex region
	- ![[Pasted image 20250327142815.png]]
- A learning rate <1 can converge, but a higher value like 0.95 takes many steps
	- ![[Pasted image 20250327142841.png]]
- <mark style="background: #BBFABBA6;">Therefore, the typical learning rate is recommended to be between 0.01 to 0.1</mark>
	- ![[Pasted image 20250327142924.png]]

