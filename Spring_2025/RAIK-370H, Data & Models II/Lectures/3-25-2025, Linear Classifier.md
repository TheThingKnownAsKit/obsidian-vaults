![[11 Linear Classifier.pdf]]

PCA does not work in singular matrices because they are not invertible

![[Pasted image 20250327120711.png]]
This red line is linear classification. How do we separate the data?

Review: Important Matrix Operations
<mark style="background: #ADCCFFA6;">Determinant</mark> - A value which can be computed from a matrix which encodes certain properties of the matrix.
	From a simple perspective, it’s something like the area or “amount” of a matrix which may be used in other linear transformations.
<mark style="background: #ADCCFFA6;">Inverse Matrix</mark> - The inverse of a square matrix A, denoted by A-1, is the matrix such that the product of A and A-1 is the Identity matrix.
	From a simple perspective, it is the matrix equivalent of a reciprocal.

Remember the variance equation
$$var=\frac{\sum^n_{i=1}(x_{i}-\overline{x})^2}{n-1}$$

## Fisher's Linear Discriminant Equation
<mark style="background: #ADCCFFA6;">Fisher's Linear Discriminant</mark> works under the assumptions of normally distributed data with equal or common covariances
$$v_{c}=\omega _{c0}+\sum^F_{i=1}\omega_{ci}f_{i}$$
- f stands for feature (aka variables)
- $\omega$ stands for weight. The weight determines how important the features are for determining the value
Combines the intercept formula with the weight formula
STEPS FOR THE EQUATION
1. Compute the covariance matrix ($\sum$)
	1. You average the covariance matrices for each feature and use this common covariance
	2. Used for feature weights
2. Find the covariance matrix inverse $\sum^{-1}$
3. Compute feature weights
4. Compute the intercept formula
5. Plug the numbers into the linear classifier formula to solve for the line

Note: <mark style="background: #BBFABBA6;">When using the covariance matrix, you average the covariance matrices for each feature</mark> (pool and divide by n)

INTERCEPT FORMULA:
$$\omega _{c0}=-\frac{1}{2}\omega^F_{i=1}\omega _{ci}\overline{f}_{ci}$$
- $\omega_{ci}$ is the intercept for the class c. It is the sum of the weighted average features
- Note that the 1/2 is just given. Not sure how/if we solve for it
This intercept represents what our model decides without any information from the features.

THE WEIGHT FORMULA:
$$\omega _{ci}=\sum^F_{j=1}\left( \sum^{-1} \right)_{ij}\overline{f}_{cj}$$
- $\sum$ is the covariance matrix of all features f
- $\sum^{-1}$ is the inverse matrix of the covariance matrix
- $\overline{f}_{cj}$ (pronounced f-bar) is the average of features $f_{j}$ for class c
Multiply by the inverse matrix is like dividing by the covariances. The ith weight comes from all of the features' means divided by how they covary with the ith feature