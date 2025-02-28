![[01 Naive Bayes.pdf]]

## Classification Tasks
<mark style="background: #ADCCFFA6;">Classification tasks</mark> are cases where you have features that can be used to predict a label or class
	Tumor size and thickness can be used to predict benign or malignant tumors

If you know all the data, you can predict classification using simple conditional probability
$$P(A|B)=\frac{P(A\cap B)}{P(B)}$$

If you want to predict future data, you can solve for P(B|A) using Bayes' Rule
$$P(B|A)=\frac{P(A|B)P(B)}{P(A)}$$

## Naive Bayes
<mark style="background: #ADCCFFA6;">Naive Bayes</mark> is trying to use features X to predict class y using Bayes' theorem. <mark style="background: #BBFABBA6;">You have to assume all features are independent of one another</mark>
	Without assumed independence this does not work because every dependent term means that more occurrences have to be observed of all feature combinations. You have to make some assumptions to make it work
Given a feature vector X, we must calculate P(y|X) for all classes y:
$$P(y|X)=\frac{P(X|y)P(y)}{P(X)}=\propto P(y)\prod^n_{i=1}P(X_{i}|y)$$
$$\text{Final Calculation} \to y=argmax_{y}\left( P(y)\prod^n_{i=1}P(X_{i}|y) \right)$$

### Example 1 - Working with Data Points
![[Pasted image 20250123125021.png]]
![[Pasted image 20250123125058.png]]
![[Pasted image 20250123125111.png]]

### Example 2 - Frequency Tables
![[Pasted image 20250123132324.png]]
![[Pasted image 20250123132350.png]]
Select BANANA in this case since it has the highest probability

### Example 3 - Text Classification
![[Pasted image 20250123133408.png]]
![[Pasted image 20250123133428.png]]

You can alleviate the problem of 0's happening in probability using <mark style="background: #ADCCFFA6;">Laplace Smoothing</mark>. You add some value $\alpha$ to the count of each word so words that don't occur for a given class can still be non-zero
$$P(\text{word}|\text{class})=\frac{\text{occurrences of word in class}+\alpha}{(\text{total words in class} +\alpha*(\text{size of corpus}))}$$

![[Pasted image 20250123133442.png]]
![[Pasted image 20250123133451.png]]
A very close game is classified as sports given it is larger

If you have vanishing probabilities, make $\alpha$ smaller than 1. If you still have issues, process the word more:
1. <mark style="background: #ADCCFFA6;">Stopword removal</mark> removing words like a, the, of, etc 
2. <mark style="background: #ADCCFFA6;">Lemmatization</mark> which is extracting the roots of words. Walking becomes walk