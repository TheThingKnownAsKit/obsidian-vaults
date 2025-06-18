![[10 Principal Components Analysis.pdf]]

## Principal Components Analysis
Instead of only picking a few features, combine aspects of all our features into fewer dimensions

<mark style="background: #ADCCFFA6;">Principal Components Analysis (PCA)</mark> is transforming all data from a higher dimension to a lower one. Encodes all features into a new "component" of the data
- No labels, unsupervised
- Creates a linear system as a matrix which transforms data from one dimensional space to another

Take this graph
![[Pasted image 20250313125114.png]]![[Pasted image 20250313125131.png]]

PCA will use the direction of maximum covariance. This is the principal component
- Project onto the principal component line with the goal to maintain as much spread and separability in the original data as possible
- Uses eigenvectors
![[Pasted image 20250313125248.png]]

## Eigenvectors
The vectors of a matrix that will not rotate when multiplied by that matrix are its <mark style="background: #ADCCFFA6;">eigenvectors</mark>. They can be scaled only, and the factor of their scaling is defined by <mark style="background: #ADCCFFA6;">eigenvalues</mark>

The process of computing eigenvectors and eigenvalues as part of the principle components analysis

$Av=\lambda v$ for eigenvectors v and eigenvalues $\lambda$
- For eigenvectors v, matrix A multiplied with v is no different than a scalar value $\lambda$ times v
$Av=\lambda Iv$ for identity matrix I
- This is the same as multiplying by 1 and should not change any results
$(A-\lambda I)v=0$
- Moving to one side of the equation and simplifying
If v is non-zero, then $|A-\lambda I|=0$. (determinant of $A-\lambda I$ is 0)
- The null space of a matrix is the set of all vectors that, when multiplied by the matrix, give the 0 vector
- If a non-zero vector is in the null space, the matrix is singular
- If a matrix is singular, it's determinant is 0

https://docs.google.com/spreadsheets/d/18PeeQJcI5dSRgYTbd2rByChapDAKWNWvqJXAD0q8dvY/edit?gid=0#gid=0

The point is kind of that instead of having to do feature engineering yourself it is an algorithm that does it for you
