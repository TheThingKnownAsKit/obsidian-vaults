- Linear Algebra Review
	- Matrix operations
		- Addition, subtraction
		- Dot product
		- Determinant and inverse (3 dimensions max)
- Principle Components Analysis
	- Motivation and curse of dimensionality
	- Eigenvalues and eigenvectors (2 dimensions max)
	- Conceptual application (i.e., PCA dimensional representation vs. original dimension)
- Linear Classifier
	- Fisher’s linear discriminate analysis (2 dimensions max)
- Optimization
	- Learning-based approach motivation (i.e., learning parameters without a closed form solution)
	- Gradient descent concept and application
		- Cost function
		- Derivative of a function to find gradient (exponents and chain rule)
		- Learning rate and momentum purposes
	- Sample gradient update (e.g., part of the update steps as in Quiz 7)
- Neural Networks
	- Perceptron model
		- Neuron basis
		- Weighted sum of input signal (linear equation)
		- Activation function concept and examples
	- Multilayer perceptron
		- Architecture (i.e., layers of interconnected perceptrons)
		- Backpropagation concept
			- Start at output where error is known, propagate back into earlier network layers
		- Vanishing gradient causes
	- Convolutional Neural Networks
		- Conceptual benefits of convolution vs. dense neurons for images
		- Convolution kernel operation (3 dimensions max)
			- E.g., Sum of cell-by-cell products
- Other Topics
	- Data bias
		- Potential causes and issues
		- Mitigating approaches
			- Undersampling, oversampling, etc.
	- SVMs
		- Conceptual approach
		- Kernel trick
	- Ensemble learning
		- Bootstrapping
		- Bagging (random forest), Boosting, and Stacking
		- Bias-variance tradeoff (i.e., underfit and overfit)

# Linear Algebra Review
- Addition, subtraction
Addition and subtraction is easy as hell you know how to do this just subtract/add them

---

- Dot product
Multiply each row and sum them into one value

---

- Determinant and inverse (3 dimensions max)

The <mark style="background: #ADCCFFA6;">determinant</mark> is the size of a matrix. Kind of like the area. 
For 2x2 matrices you find the matrix of minors
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

FOR FINDING THE INVERSE (using Polsley's method):
1. Find the determinant for each cell (don't multiply and sum them). It should still be a 2x2 or 3x3 matrix
2. Swap the signs in a checkered pattern to find the matrix of cofactors
Positive pattern
![[Pasted image 20250311135929.png]]
Negative pattern
![[Pasted image 20250311135939.png]]
3. Then you find the adjoint/adjugate matrix by flipping the cofactor matrix along the main diagonal
4. Divide the adjoint matrix by the determinant to find the inverse

# Principle Component Analysis
- Motivation and curse of dimensionality
The curse of dimensionality is when you have too many features and more data resides at the edges of high dimensional space so it is difficult to capture all the data in your training set

Feature selection is the process of deciding which features are the most important. Feature selection is important to reduce dimensionality which is important because if we have 1000000000 features we'll never be able to properly analyze the data, so reducing it to the most influential features improves accuracy

PCA is an algorithm that combines aspect of all features into fewer dimensions. Rather than doing it by hand, it does it for you. It is an unsupervised algorithm

NOTE: PCA does NOT remove any features, it transforms the data by encoding all the features into a "component" of the data. It creates a linear system as a matrix transformation from one dimensional space to another

---

- Eigenvalues and eigenvectors (2 dimensions max)
Eigenvectors are the vectors of a matrix that will not rotate when multiplied by that matrix. They can be scaled only by the eigenvalues. You need them for principle component analysis

$Av=\lambda v$ for eigenvectors v and eigenvalues $\lambda$
$A-\lambda I=0$ aka $A=\lambda I$ or if you prefer $Av=\lambda Iv$
$\det(A-\lambda I)=0$ to find the eigenvalues, solve for $\lambda$, to find eigenvectors solve for null space

1. Calculate the covariance matrix
2. Solve for the eigenvalues of the covariance matrix
3. Find the corresponding k eigenvectors for k top eigenvalues
	1. k being the number of dimensions you are reducing to (2 max in this test)
	2. The eigenvectors here are the direction of maximum spread aka the PRINCIPLE COMPONENT
4. Multiply the data by the set of eigenvectors to get the data in the new PCA dimension(s)

To normalize to a unit vector, divide by the magnitude, which is just the distance function

---

- Conceptual application (i.e., PCA dimensional representation vs. original dimension)
For example, take this data
![[Pasted image 20250427153505.png]]
Finding the eigenvector of the covariance matrix results in this principle component
![[Pasted image 20250427153702.png]]
When you multiply the data by this vector (doing the dot product), you project all the data onto this one line
![[Pasted image 20250427153738.png]]
So this becomes our single dimension principle component
![[Pasted image 20250427153815.png]]
You can cleanly separate this data right down the middle if you apply features (in this case we separate them into benign and malignant tumors)
![[Pasted image 20250427153847.png]]

# Linear Classifier
- Fisher’s linear discriminate analysis (2 dimensions max)

Fisher's Linear Discriminant works under the assumptions of normally distributed data with equal or common covariances
$$v_{c}=\omega _{c0}+\sum^F_{i=1}\omega_{ci}f_{i}$$
- f stands for feature (aka variable)
- $\omega$ stands for weight. The weight determines how important the features are for determining the value

It combines the intercept formula with the weight formula

Note: LDA does not actually solve for the decision boundary, it is finding the normal discriminant hyperplane onto which the data will be projected as a single dimension
- PCA projected onto the axis of max spread - unsupervised
- LDA gives us the axis of maximum class separation - supervised
So it finds the axis of class separation

STEPS:
1. Compute the covariance matrix by averaging the covariance matrices for each feature and use this as the common covariance
	1. Note that if there is more than one covariance matrix (which is common if you're using more than one feature), you just average the covariance matrices into one matrix
2. Find the covariance matrix inverse $\sum^{-1}$
	1. Go through the normal original -> minors -> cofactors -> adjoint -> inverse matrix process
3. Compute the feature weights using the formula $\omega _{ci}=\sum^F_{j=1}\left( \sum^{-1} \right)_{ij}\overline{f}_{cj}$
	- $\sum$ is the covariance matrix of all features f
	- $\sum^{-1}$ is the inverse matrix of the covariance matrix
	- $\overline{f}_{cj}$ (pronounced f-bar) is the average of features $f_{j}$ for class c
4. Compute the intercept formula $\omega _{c0}=-\frac{1}{2}\omega^f_{i=1}\omega _{ci}\overline{f}_{ci}$
5. Plug these numbers into the linear classifier formula to solve for the line $\omega _{c0}+\sum^F_{i=1}\omega_{ci}f_{i}$

<mark style="background: #BBFABBA6;">It looks like we're only going to have to do single feature weights on the test, so this can be simplified significantly</mark>
1. compute the covariance matrix by averaging the feature variance of the 2 features
2. Find the covariance matrix inverse $\sum^{-1}$, which for a covariance matrix of a single number is just the reciprocal
3. Compute the feature weights using the formula $\omega _{ci}=\sum^{-1}_{}*\overline{f}_{c}$
	1. $\sum^{-1}$ is the common covariance found in step 2
	2. $\overline{f}_{cj}$ is just the feature average you should already know from calculating the variance
	3. Note that c here refers to classifications (using Polsley's shape drawing example, it's either a square or circle) and i refers to the feature (we only have one here, curvature)
4. Compute the intercept formula $\omega _{c0}=-\frac{1}{2}\omega _{ci}\overline{f}_{ci}$
5.  Plug these numbers into the linear classifier formula to solve for the line $\omega _{c0}+\omega_{ci}f_{i}$
	1. It'll solve into something with a variable still in it as this is a line. Like $-1+1*curvature$

Note that the weights emphasize which features have the most impact
- The more positive the weight, the more positively correlated
- The more negative the weight, the more negatively correlated
- The closer to 0 the weight is, the less important the feature is
# Optimization
- Learning-based approach motivation (i.e., learning parameters without a closed form solution)
Calculating a model based on statistics and probability can sometimes be expensive and complicated (closed form equations that always yield the same model parameters)

Sometimes it's easier, more efficient, and simpler to just make a guess and learn. Learning-based approaches are open form solutions that make a guess, calculate the error of that guess, and take the derivative to adjust for the next guess. This can be remarkably effective at finding the center of a set of data

---

- Gradient descent concept and application
	- Cost function
	- Derivative of a function to find gradient (exponents and chain rule)
	- Learning rate and momentum purposes

The directional derivative used to adjust the next guess is called a gradient. The convex optimization algorithm to find the bottom part of the cost (mean squared error) of each guess (the least wrong guess) is called gradient descent

Algorithm steps:
1. Make a random guess
2. Calculate the gradient (directional derivative) of the cost function for the guessed value
	1. Usually for the cost function we use the mean squared error $$MSE=E(\mu)=\frac{1}{n}\sum^n_{i=1}(x_{i}-\mu)^2$$
3. Update the guess based on the gradient using the learning rate. Usually in the opposite direction
	1. After some chain rule fuckery the derivative equation ends up as this $$-\frac{2}{n}\sum^n_{i=1}(x_{i}-\mu)$$
	2. The learning rate is how much the guess can change at each iteration, typically a learning rate between 0.01 and 0.1 is recommended
	3. $$new\ guess=guess-(gradient*learning\ rate)$$
4. Repeat until optimization condition is met. Typically a set number of iterations





---

- Sample gradient update (e.g., part of the update steps as in Quiz 7)
I think learning rate and momentum

# Neural Networks
## Perceptron Model
- Neuron basis
Neurons are little electrical guys in your brain that take in input and decide to fire (yes) or not fire (no) more signals to other neurons. By passing input through all these neurons the brain makes calculations and decisions

Perceptron's imitate this in computers and code

---

- Weighted sum of input signal (linear equation)
$\text{Net input function}=\sum^n_{i=1}w_{i}*x_{i}+b$
So therefore, $\text{Output}=f(\sum^n_{i=1}w_{i}*x_{i}+b)$

Notice that perceptron is just a linear classifier. It uses weighted features to generate an output. The x here is the weight
$\text{Perceptron Output}=f(\sum^n_{i=1}w_{i}*x_{i}+b)$

---

- Activation function concept and examples
A certain level of stimulation is needed to reach a threshold before the perceptron has to fire. For a perceptron this is called the activation function

Step activation is the most basic one. Everyone is 0 up to a threshold, after which the signal is directly passed to output
![[Pasted image 20250401125844.png]]

Sigmoid activation is the most traditionally popular and more biologically accurate model. It allows for a small amount of signal to pass through even below the threshold, but moderates the signal based on a threshold
$$\sigma(t)=\frac{1}{1+e^{-t}}$$
![[Pasted image 20250401125859.png]]

ReLU is the most popular today (especially for deep learning). It is a simple model that is easy to calculate and avoids some issues with sigmoid
$$\sigma(t)=max(0,t)$$
  ![[Pasted image 20250401125935.png]]

ReLU vs Sigmoid
- Sigmoid moderates output growth so it does not grow as quickly as ReLU. This is useful BUT it is more computationally complex and gets expensive when you have thousands of perceptron's
- It is easier to take the derivative of ReLU which makes parameter updates easy at scale

You usually combine gradient descent with an activation function as an extra step for the perceptron learning algorithm

## Multilayer Perceptron (MLP) aka Neural Network
- Architecture (i.e., layers of interconnected perceptron's)
![[Pasted image 20250427164916.png]]

Input layer (generally layer l) -> as many hidden layers as you want -> output (generally layer k)

Individual perceptrons can only classify linearly (yes or no), multiple perceptrons can create non-linear decision boundaries

The output of node j is the input to node k if j is previous to k, The weight updates at layer k can then be expressed as:
$$\Delta w_{jk}-=\alpha*\delta_{k}*o_{j}$$
- Weight updates is learning rate * gradient = learning rate * error * input
- $\alpha$ is the learning rate
- $\delta_{k}$ is the error at node k
	- $$\delta_{k}=(o_{k}-y_{k})*\frac{\partial o_{k}}{\partial net_{k}}$$
	- Where the parenthesis part is error as from MSE with constants dropped, and the denominator is an extra term to account for activation derivative
- $o_{j}$ is the input (which comes from the derivative term)
Below is the equation to write the output activation ($o_{j}$) in terms of the input linear equation ($net_{j}$) in terms of the weights ($w_{ij}$)
$$\frac{\partial E}{\partial w_{ij}}=\frac{\partial E}{\partial o_{j}}\frac{\partial o_{j}}{\partial net_{j}}\frac{\partial net_{j}}{\partial w_{ij}}$$
Where:
- partial oj is the activation function derivative
- partial e over oj is:
	- $$\frac{\partial E}{\partial o_{j}}=\sum_{k\in K}\left(\frac{\partial E}{\partial o_{k}}\frac{\partial o_{k}}{\partial net_{k}}w_{jk}\right)$$
	- It is the sum of error across all output nodes based on the contribution to o_j to each node

However this is stupid and hard and time consuming which is why we do backpropagation instead

---

- Backpropagation concept

Basically since the output is known, instead of following calculations through to what we already know to update parameters based on error, start at output where error is known, propagate back into earlier network layers

![[Pasted image 20250403132252.png]]
![[Pasted image 20250403132738.png]]

---

- Vanishing gradient causes
Sometimes over many layers, the weight update will disappear. This is called the vanishing gradient problem. Using ReLU activation solves this problem

## Convolutional Neural Networks
- Conceptual benefits of convolution vs. dense neurons for images
Convolution is a form of digitally filtering one signal based on another. You can use it to model how a signal responds to certain conditions. You basically apply filters to the data to emphasize what you want to see and minimize noise

For image processing, it can sharpen, blur, edge detect, pattern detect, and more

Convolution neural networks utilize convolution operations to help capture important image information while reducing data complexity

---

- Convolution kernel operation (3 dimensions max)
	- E.g., Sum of cell-by-cell products

A kernel is basically a filter window. For example, you have a kernel that defines an eye and multiply it by the matrix values of an image of a face, and it will only multiply well with the parts of the matrix that look like an eye

You can combine backwards propagation with kernels by turning the kernels into model parameters
![[Pasted image 20250408131857.png]]
# Other Topics
## Data Bias
- Potential causes and issues
Garbage in, garbage out. You need good data to train a model. Includes the balance of labels and the quality of labels

---

- Mitigating approaches
	- Undersampling, oversampling, etc.

1. Be mindful of data provenance
	1. Where did it come from?
	2. How was it collected?
2. Clean your data
	1. Drop incomplete entries
	2. Search for patterns your model may exploit inaccurately (watermarks, consistent background noise)
3. Ensure high-quality, multi-annotator labelling
	1. If labeling data, work with multiple annotators and apply inter-rater agreement metrics
		1. For 2 annotators, use Cohen's Kappa
		2. For 3 or more, use Fleiss Kappa
4. Address class imbalance
	1. Undersampling removes samples belonging to the majority class
		1. May be done randomly. The point is to make sure the majority class is not overrepresented when training the model
		2. May also use techniques like clustering or tomek links to group into neighbors and remove consistently across neighborhoods (whatever that means)
		3. ![[Pasted image 20250427171413.png]]
	2. Oversampling generates new data for the minority class
		1. This can be done randomly by duplicating existing data points
		2. A better approach is to interpolate based on existing samples (common technique being SMOTE)
5. Evaluate and interpret the model
	1. Compute metrics for different test datasets and apply interpretation / auditing methods

## SVMs
- Conceptual approach
Support Vector Machines (SVMs) work by finding two support vectors with maximal margin between them. One creates a positive hyperplane and the other a negative hyperplane

SVM's are optimization-based. They model  data in higher dimensions but never actually apply transformations to them. This allows us to linearly separate data that we previously could not
![[Pasted image 20250427172525.png]]
This is not linearly separatable, but if you model it in 3d space, you can separate it linearly
![[Pasted image 20250427172556.png]]
The flat plane on the left is the linear separation

---

- Kernel trick
The dot product between two vectors can be used to give the relative directionality and magnitude that SVMs need. This is the kernel trick

A set of functions called the kernel functions compute the dot product of points in higher dimensional spaces.
NOTE: the kernel functions do not transform the space. The describe only a singular aspect of higher dimensional space without going there. Translates

The ability to compute the dot product in a high dimensional space without ever actually making the transformation is the kernel trick

Linear Kernel is $K(x,y)=x*y$
Polynomial Kernel is $K(x,y)=(x*y+c)^d$
Sigmoid Kernel is $K(x,y)=\tanh(ax*y+c)$
Gaussian Radial Basis Function (RBF) Kernel is $K(x,y)=e^{\left(\frac{||x-y||^2}{2\sigma^2}\right)}=e^{(-y||x-y||^2)}$

The linear kernel is just the dot product
The polynomial and sigmoid is used to model parabolic data or other certain kinds
The RBF kernel is very popular because it is useful for infinite dimensional space

## Ensemble Learning
Ensemble learning is just techniques to improve accuracy with your model

- Bootstrapping
Bootstrapping is related to cross validation, but instead of focusing on how good your model is at being generalized, it focuses on estimating statistical descriptors of your model
1. Create n subsamples of data WITH REPLACEMENT
2. Train n models
3. Build a probability distribution from the performance of each model
4. Define variance and confidence intervals of the model
![[Pasted image 20250422130916.png]]

---

- Bagging (random forest), Boosting, and Stacking
In bagging you sample smaller data subsets and in cross validation it's used to test generalizability of the model. It is useful for assisting bootstrapping as it helps estimate statistical parameters
1. Create the bootstrapped subsets
2. Train n models on those subsets and combine them

It combines multiple weak learners in parallel to make a stronger learner. Select them with majority vote (classifiers) or averaging (regression)

Random forests are one of the best traditional methods we have

Bagging is useful for weak learners operating in PARALLEL

Boosting is a sequential technique. The selection of the data is one of the steps of the process and it focuses on reducing bias to any one class or another by better coverage of all data
- Let's train the first model and see how it goes
- Then train another model on the data it got wrong
- Repeat

Stacking is a sequential ensemble method that uses another machine learning model at the end. Supports heterogeneous weak learners and can be arranged in multiple layers

---

- Bias-variance tradeoff (i.e., underfit and overfit)
![[Pasted image 20250422131805.png]]

![[Pasted image 20250422131950.png]]
