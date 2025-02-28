![[02 Decision Trees Part 1.pdf]]

## Decision Tree Classifier
The <mark style="background: #ADCCFFA6;">decision tree</mark> will also use probabilities to model data for classification (like Naive Bayes), but with decision branches
![[Pasted image 20250128130140.png]]

Like a branching flow chart based on feature values

To build a tree, a popular choice is <mark style="background: #ADCCFFA6;">ID3</mark> (iterative dichotomizer 3) and its extension C4.5
- It calculates how "well" each feature can separate the data
- Select the feature that maximally separates data as the new node
- Recursively, split each branch on the remaining features based on how well they each perform

## Entropy and Information
To define how well a feature can split data, we will use <mark style="background: #ADCCFFA6;">entropy</mark> from information theory. Entropy is a way to <mark style="background: #BBFABBA6;">model the uncertainty of a process</mark> (UNCERTAINTY NOT CERTAINTY). It defines the average level of uncertainty (or information) associated with a random variable's potential outcomes
$$H(X)=E[I(X)]$$
	The expected value of the Shannon information content

<mark style="background: #ADCCFFA6;">Shannon information</mark> is a metric other than raw probability to represent what he called surprise. Defined with 3 axioms
- Events with 100% probability are not surprising and yield no information
- The less probable an event, the more surprising and the more information
- For independent events, the total amount of information is the sum of self-information's from individual events
It is the negative log of probability:
$$I(X)=-\log_{b}[P(X)]$$
Defined from 0 to 1, gives: high surprise for low probabilities and low surprise for high probabilities
![[Pasted image 20250128131518.png]]

Entropy, H, the weighted sum of Shannon Information, therefore it is the uncertainty of a random variable X as defined by:
$$H(X)=-\sum^n_{i=1}p(x_{i})*\log_{b}(p(x_{i}))$$
For example, flipping a coin:
$$H(X)=-p(heads)*\log_{2}(p(heads))-p(tails)*\log_{2}(p(tails))$$
Flipping a fair coin:
$$H(X)=-0.5*\log_{2}(0.5)-0.5*\log_{2}(0.5)=1$$
Flipping a coin that always lands on heads:
$$H(X)=-1*\log_{2}(1)-0*\log_{2}(0)=0$$
This makes sense because there is NO surprise if you know it will always land on heads, but our uncertainty is 100% with a fair coin because we do not know for sure if it will be heads or tails