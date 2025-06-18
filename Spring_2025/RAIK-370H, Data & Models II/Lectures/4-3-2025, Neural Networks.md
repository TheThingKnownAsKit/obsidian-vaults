![[14 Neural Networks.pdf]]

## Multi-Layer Perceptron (MLP) Architecture
The MLP is constructed of layers of fully inter-connected perceptrons. Input data is fed into the input layer as an array of numbers. Output activation is read from the output layer, just as with a single perceptron. Between the input and output are neurons comprising the hidden layer(s)

### Outer Layer (Layer K)
Generally, the output layer is described at layer k and the layer directly before it is layer j
![[Pasted image 20250403131554.png]]

The output of node j is the input to node k if j is previous to k, The weight updates at layer k can then be expressed as:
$$\Delta w_{jk}-=\alpha*\delta_{k}*o_{j}$$
- Weight updates is learning rate * gradient = learning rate * error * input
- $\alpha$ is the learning rate
- $\delta_{k}$ is the error at node k
	- $$\delta_{k}=(o_{k}-y_{k})*\frac{\partial o_{k}}{\partial net_{k}}$$
	- Where the parenthesis part is error as from MSE with constants dropped, and the denominator is an extra term to account for activation derivative
- $o_{j}$ is the input (which comes from the derivative term)

<mark style="background: #BBFABBA6;">We need to express the jth node weights in terms of output error</mark>

Below is the equation to write the output activation ($o_{j}$) in terms of the input linear equation ($net_{j}$) in terms of the weights ($w_{ij}$)
$$\frac{\partial E}{\partial w_{ij}}=\frac{\partial E}{\partial o_{j}}\frac{\partial o_{j}}{\partial net_{j}}\frac{\partial net_{j}}{\partial w_{ij}}$$
Where:
- partial oj is the activation function derivative
- partial e over oj is:
	- $$\frac{\partial E}{\partial o_{j}}=\sum_{k\in K}\left(\frac{\partial E}{\partial o_{k}}\frac{\partial o_{k}}{\partial net_{k}}w_{jk}\right)$$
	- It is the sum of error across all output nodes based on the contribution to o_j to each node

## Backpropagation
Rather than solve for all that nonsense above on a generic hidden layer update, it is easier to carry this term back from the update we used on the output layer. <mark style="background: #ADCCFFA6;">Backpropagation</mark> is the learning method most commonly used for MLPs because it simplifies these calculations. For all early layers, it backpropagates the error computed at the output (easiest way to get error for inside layers)
Start with output layer, comparing directly to the error on the test set and go backwards

![[Pasted image 20250403132252.png]]

![[Pasted image 20250403132738.png]]
![[Pasted image 20250403133104.png]]
![[Pasted image 20250403133116.png]]

Gradient descent with learning rate by itself can fall into local minima. Use momentum to fix this
![[Pasted image 20250403133548.png]]

Sometimes over many layers, the weight update will disappear in the vanishing gradient problem. Use ReLU activation to solve this
![[Pasted image 20250403133712.png]]

![[Pasted image 20250403133800.png]]

I give up review later