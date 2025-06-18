![[13 Perceptron.pdf]]

## Perceptron
The <mark style="background: #ADCCFFA6;">Perceptron</mark> is a simplified model of a neuron using a linear classifier model. It is a set of input signals to a node which can fire an output. Inputs -> outputs

Input features are weighted by synapses and the accumulation of those signals is fed into a function that models the activation or firing
$$\text{net input function}=\sum w_{i}*x_{i}$$
$$\text{output}=f\left( \sum w_{i}*x_{i}+b \right)$$
Mimic the behavior of a stronger/weaker connection using weights

Different types of activation:
- Step activation: everything is 0 up to the activation threshold, after which the signal directly passes to output
  ![[Pasted image 20250401125844.png]]

  - This is sigmoid activation. Most popular traditionally and a better biological model. It allows for a small amount of the signal to propagate even below the threshold
  $$\sigma (t)=\frac{1}{1+e^{-\beta t}}$$
  ![[Pasted image 20250401125859.png]]

- ReLu (rectified linear unit) activation is the most popular today with large language models
  $$\sigma(t)=max(0,t)$$
  ![[Pasted image 20250401125935.png]]

ReLU vs Sigmoid
- Sigmoid has some benefits during training in that the activation outputs do not grow as quickly, however it is more computationally complex
- Thinking about gradient descent, the derivation of ReLU is much cleaner, 1 for any positive value of t, which can make parameter updates easy at scale

If these are all linear classifiers, why are we using gradient descent to train the? The presence of the activation function is an extra step. Even apart from the activation function, gradient descent methods will scale better to more dimensions

## Gradient Descend for ReLU Perceptron
$$MSE=J(\theta)=\frac{1}{n}\sum^n_{i=1}(h_{\theta}(x_{i})-y_{i})^2$$
- $h_{\theta}$ is the output of our model, which is the activation on the bias added to the linear equation of weighted features

We will need partial derivatives for the change in each model parameter. Because this is a linear equation, every partial derivation will have the following form:
$$\frac{\partial J(\theta)}{\partial\theta}=\frac{\theta}{\partial\theta_{k}}\left( \frac{1}{n}\sum^n_{i=1}\left( f\left( \sum^n_{m=0}\theta_{i,m}*x_{i,m} \right)-y_{i} \right)^2 \right)$$
Which simplifies to:
$$\frac{1}{n}\sum^n_{i=1}2\left( f\left( \sum^n_{m=0}\theta_{i,m}*x_{i,m} \right)-y_{i} \right)*\frac{\partial}{\partial\theta_{k}}\left( f\left( \sum^n_{m=0}\theta_{i,m}*x_{i,m} \right)-y_{i} \right)$$

![[Pasted image 20250401132715.png]]

```Python
class Perceptron:
	def __init__(self):
		self.weights = None
		self.bias = 0
	
	def initialize(self, n_features):
	"""set initial w and b as zeros"""
		self.weights = np.zeros(n_features)
		self.bias = 0
		return
	
	def predict(self, inputs):
	""" feed forward using activation function """
		activation = np.dot(inputs, self.weights) + self.bias
		return 1 if activation > 0 else 0
	
	def train(self, X, y, epochs=100, learning_rate=0.1):
	"""Train the perceptron using the input data and target labels."""
		self.initialize(X.shape[1])# initialize the w and b
		for epoch in range(epochs):
			for inputs, label in zip(X, y):
			y_pred = self.predict(inputs) # get prediction
			error = label - y_pred # calculate delta error
			# update w and b
			self.weights += learning_rate * error * inputs # learning rate * gradient
			self.bias += learning_rate * error
		return
```

![[Pasted image 20250401132730.png]]

## The Brain
<mark style="background: #ADCCFFA6;">Neural Networks</mark> are constructed of multiple perceptions. The traditional formulation is a <mark style="background: #ADCCFFA6;">multi-layered perceptron (MLP)</mark> and consists of an input and output layer of perceptron, along with a hidden layer

![[Pasted image 20250401134033.png]]
Individual perceptrons can only classify linearly (yes or no), multiple perceptrons can create non-linear decision boundaries
![[Pasted image 20250401134125.png]]

