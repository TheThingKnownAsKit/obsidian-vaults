![[06 K-Nearest Neighbor.pdf]]

## Clustering Algorithms
<mark style="background: #ADCCFFA6;">Clustering algorithms</mark> are greedy algorithms that take a more geometric approach

K-Nearest is an example of this

## K-Nearest Neighbors (KNN)
<mark style="background: #ADCCFFA6;">K-Nearest Neighbor</mark> is a supervised clustering approach that can make intuitive and explainable classification decisions. It uses the concept of feature locality
1. Calculate the distance between the new sample and all other samples
2. Sort them in ascending order
3. Select the K nearest neighboring points
4. Assign the majority class label of the nearest neighbors

Cons: Ties are hard to deal with, it is computationally expensive, and it doesn't work well with categorical data
	For binary classifications, ties are solved with an odd value of K
	For multi-class labeling, check the K+1 sample to break the tie