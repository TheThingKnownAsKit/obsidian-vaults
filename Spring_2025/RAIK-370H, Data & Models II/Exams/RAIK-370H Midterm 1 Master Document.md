- Decision Trees
	- ID3 algorithm
		- Entropy
		- Information Gain
	- Application of Decision Tree ID3 algorithm (pros/cons)

## Naive Bayes
- <mark style="background: #ADCCFFA6;">Assumptions of Naive Bayes</mark>
That every feature is INDEPENDENT of each other

This is done because otherwise the feature combination calculations would become immense for even a few features

---

- <mark style="background: #ADCCFFA6;">Formula for Naive Bayes Output (i.e., Given a feature vector X, how to calculate P(y|X) for all classes of y)</mark>

If X is a feature vector (just a list of features) and y is the class we're inspecting:
$$P(y|X)=argmax_{y}\left( P(y)\prod^n_{i=1}P(X_{i}|y) \right)$$
	Note: The $\prod$ is the product operator. It is basically the same thing as $\sum$ except instead of adding every calculations, you multiply them

In words, it is the probability of the class * the cumulative products of every feature given the class

<mark style="background: #BBFABBA6;">The point is you do the above calculation for each class and then the solution is the class with the higher likelihood.</mark> We're trying to identify what class something will be by what features it has

For example, if we have feature vector [A, B] and class vector [c1, c2] and with the data given below. We want to know what class the feature values A = 1 and B = 0 is most likely to belong to. Calculations would be:

| A   | B   | Class |
| --- | --- | ----- |
| 0   | 1   | c1    |
| 0   | 0   | c2    |
| 1   | 1   | c1    |
| 0   | 1   | c1    |
| 1   | 0   | c1    |
| 0   | 0   | c2    |
| 1   | 1   | c1    |
| 0   | 0   | c2    |
| 1   | 0   | c1    |
| 1   | 0   | c2    |

Start with c1:
$$P(c_{1}\vert A=1,B=0)=P(c_{1})\prod^n_{i=1}P(X_{i}|y)$$
$$P(c_{1}|A=1,B=0)=P(c_{1})*P(A=1|c_{1})*P(B=0|c_{1})$$
In this scenario, A should be true when we calculate fractions and B should be false

Count the occurrences and put in fractional form (remember independent probabilities are just occurrences/total samples)
- c1 occurs 6 times, so 6/10
- When A = 1, 4 times is it also c1, so 4/6
- When B = 0, only 2 times is it also c1, so 2/6
Put these values into the equation
$$P(c_{1}|A=1,B=0)=\frac{6}{10}*\frac{4}{6}*\frac{2}{6}=\frac{4}{30}$$

Repeat the steps above but for c2 this time, you get
$$P(c_{2}|A=1,B=0)=\frac{4}{10}*\frac{1}{4}*\frac{4}{4}=\frac{1}{10}$$

$argmax\left( \frac{4}{30},\frac{1}{10} \right)=\frac{4}{30}$ so we will select c1 in this case as the most likely feature

---

- <mark style="background: #ADCCFFA6;">Laplace Smoothing</mark>
If there is a 0 in the problem it can cause errors or off math because we are working with samples, not whole sets. If we record no occurrences for something, the probability is 0, when in reality it's probably just very rare

Laplace smoothing fixes this by adding a very small value, $\alpha$, to each probability to make sure nothing is 0

$$P(X_{i}|y)=\frac{\text{occurrences of feature in class}+\alpha}{\text{all feature occurences in class}+\alpha*(\text{size of dataset})}$$

Note: all feature occurrences in class mean occurrences of every feature type in this class

$\alpha$ is usually 1

---

- <mark style="background: #ADCCFFA6;">Application of Naïve Bayes (pros/cons)</mark>

Pros:
- Simple, easy
Cons:
- Most data is not independent and this can skew the accuracy of the model
- It needs special cases for instances where not all features have been observed (laplace smoothing)

## Decision Trees (ID3)

- <mark style="background: #ADCCFFA6;">ID3 algorithm</mark>

---

- <mark style="background: #ADCCFFA6;">Entropy</mark>

---

- <mark style="background: #ADCCFFA6;">Information Gain</mark>

---

- <mark style="background: #ADCCFFA6;">Application of Decision Tree ID3 algorithm (pros/cons)</mark>

## Supervised and Unsupervised Learning

- <mark style="background: #ADCCFFA6;">Characteristics of supervised learning</mark>
There are features and labels and we know the labels of all the data. The algorithm is trained to identify labels given a set of features

---

- <mark style="background: #ADCCFFA6;">Examples of supervised algorithms</mark>
Naive Bates, Decision Tree, and K-Nearest Neighbor

---

- <mark style="background: #ADCCFFA6;">Characteristics of unsupervised learning</mark>
No labels, only features. You want to explore and learn about data 

---

- <mark style="background: #ADCCFFA6;">Examples of unsupervised algorithms</mark>
K-Means Clustering

## K-Nearest Neighbors (KNN)

- <mark style="background: #ADCCFFA6;">Steps and application of the algorithm</mark>
It clusters data and makes classification decisions based on feature locality

Steps:
1. Calculate the distance between the new sample and all other samples
$$d=\sqrt{ (x_{2}-x_{1})^2 +(y_{2}-y_{1})^2}$$
1. Sort them in ascending order (smallest to largest)
2. Select the K nearest neighboring points (k is a variable and you only look at neighbors up to k and assign this group the label that the majority of the features belong to)
3. Assign the majority class label of the nearest neighbors

---

- <mark style="background: #ADCCFFA6;">Limitations</mark>

Pros:
- Greedy algorithm
- Intuitive
Cons:
- Ties are hard to deal with (usually just check the K + 1 sample to break the tie)
- Computationally expensive
- Doesn't work well with categorical data

## K-Means

- <mark style="background: #ADCCFFA6;">Steps and application of the algorithm</mark>
Unsupervised algorithm for grouping similar features based on just locality of data

Steps:
1. Initialize K randomly placed points, called centroids
2. Compute the distance from every centroid K to every other point in the data set and assign every point in the data set to its nearest centroid
3. Move each centroid K to the new centroid based on all assigned nearest points
4. Repeat until no change in any centroid or until a max number of iterations reached

Careful not to stop the algorithm too soon

---

- <mark style="background: #ADCCFFA6;">Limitations</mark>

Pros:
- Easy, quick to train, quick to use
- Unsupervised is arguably a pro
Cons:
- Can find only a local maximum, not global maximum

---

- <mark style="background: #ADCCFFA6;">Determining optimal number of centroids</mark>
With too many clusters, you learn less about the data, but with too few, regions can become spread out and not specific enough

Basically to determine the best K you test different values of K and compare them
1. Finish the algorithm with K centroids
2. Calculate the Within-Cluster Sum of Squared Distance (WCSS) by taking all the data points assigned to a cluster and computing their distance to the centroid (sum it I think)
3. Plot the WCSS value across each attempted K. This will give you an elbow curve. The "knee" is the most optimal one
![[Pasted image 20250304183820.png]]
So in this elbow curve's instance, 3 is the most optimal centroid

## Classification and Evaluation

- <mark style="background: #ADCCFFA6;">Confusion Matrices</mark>
They are a way to evaluate model efficiency by kind of making a punnett square looking thing of Classified As and Actually A for every feature
![[Pasted image 20250304184630.png]]

If you put it into percentages you can also use a scaled confusion matrix
![[Pasted image 20250304184703.png]]

You can combine the incorrect classifications and put in a single-class confusion matrix of A or Not A
![[Pasted image 20250304184751.png]]

Error Types:
- True Positive (TP) is a correct hit. Classified as A and is A
- True Negative (TN) is correct rejection. Classified as Not A and is Not A
- False Positive (FP) is incorrect hit. Classified as A and is Not A
	- Type II Error
- False Negative (FP) is incorrect rejection. Classified as Not A and is A
	- Type I Error

---

- <mark style="background: #ADCCFFA6;">Evaluation Metrics</mark>
We want to know how accurate our model is, so we use confusion matrices to calculate various performance metrics

Accuracy is just how many things you got correct (including correct rejections, all 4 squares)
$$Accuracy=\frac{TP+TN}{Overall\ Total}$$

True Positive Rate (TPR) aka Recall is how many instances did you find out of all the instances (high TPR is good, top row)
$$TPR\ aka\ Recall=\frac{TP}{TP+FN}$$

False Positive Rate (FPR) aka Fall Out is how many instances did you NOT find out of all the instances (opposite of TPR, so high FPR is bad, bottom row)
$$FPR\ aka\ FallOut=\frac{FP}{FP+TN}$$

True Negative Rate (TNR) aka Specificity is how many incorrect instances did you find out of all the incorrect instances (bottom row)
$$TNR\ aka\ Specificity=\frac{TN}{FP+TN}$$

False Negative Rate (FNR) aka Miss Rate is how many false negatives did you get (i dont get this one, top row, 0% FNR is perfect)
$$FNR\ aka\ MissRate=\frac{FN}{TP+FN}$$

Precision is the positive predictive value. It doesn't care about what you said was Not A, it only cares about what you said was A. Precision and recall are often reported together (Left column)
$$Precision=\frac{TP}{FP+TP}$$

The F1-score aka F-measure isthe harmonic mean of precision and recall. It is a good single measure that is hard to manipulate (every square except TN)
	A harmonic mean is the reciprocal of the arithmetic mean of the reciprocals of a set of numbers
$$\text{F-measure}=\frac{2}{\frac{1}{\frac{TP}{FP+TP}}+\frac{1}{\frac{TP}{TP+FN}}}=\frac{2}{\frac{1}{precision}+\frac{1}{recall}}$$

---

- <mark style="background: #ADCCFFA6;">Training and testing best practices (i.e., train/test splits, k-fold cross validation)</mark>

Train/test splits are when you split your data into a training set and a testing set. Never train and test your data on the same data. It can inflate accuracy rates and make your model very good at ONLY predicting this set of data

K-Fold Cross Validation is a technique to train and test your data along different folds. Helps test how your model will work across data it didn't train on
1. Separates data into k different groups
2. The algorithm is trained on all but 1 fold, which is used for testing
You can select any number of folds but 10-fold is common

---

- <mark style="background: #ADCCFFA6;">ROC and PR curves; Area Under the Curve</mark>

This is when you graph things instead of putting it in a confusion matrix

For ROC, you:
- Put the x-axis as $\frac{FP}{AN}$ where AN is $\text{Actual Negative}=FP+TN$ under different probability thresholds
- Put the y-axis as $\frac{TP}{AP}$ where AP is $\text{Actual Positive}=TP+FN$ under different probability thresholds
Traits:
- Monotonic to x (only increases as x increases)
- Bends upwards and smoothly
- NOT GOOD AT MEASURING HIGHLY UNBALANCED DATA because then x and y become not sensitive to change
![[Pasted image 20250304194255.png]]

PRC shows the tradeoff between precision and recall. For it:
- Put the x-axis as recall ($\frac{TP}{TP+FN}$) levels under different probability thresholds
- Put the y-axis as precision ($\frac{TP}{TP+FP}$)
Traits:
- y is NOT MONOTONIC to x
- For highly imbalanced data, it is still sensitive to changes, so it is more suited for it than ROC
- Looks like a jagged decline
![[Pasted image 20250304195104.png]]

## Matrix Math
Remember can only add/subtract matrices with the same dimensions

You can multiply n x m * m x y matrices as long as they both have that m. Dot product is just everything multiplied and summed

We need matrix operations because matrices are a really fast and convenient way to represent features and labels