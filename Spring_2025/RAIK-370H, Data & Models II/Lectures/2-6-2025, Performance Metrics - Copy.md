![[04 Performance Metrics.pdf]]

## Confusion Matrix
![[Pasted image 20250206153418.png]]
![[Pasted image 20250206153503.png]]

## Percentage Classes
![[Pasted image 20250206153432.png]]
![[Pasted image 20250206153446.png]]

## Evaluation Metrics
<mark style="background: #ADCCFFA6;">True Positive (TP)</mark> (correct hit) is when something IS x and classified as x
<mark style="background: #ADCCFFA6;">True Negative (TN)</mark> (correct rejection) is when something IS NOT x and is classified as not x
<mark style="background: #ADCCFFA6;">False Positive (FP)</mark> is a type 1 error or false alarm error. Object of NOT x was classified as x
<mark style="background: #ADCCFFA6;">False Negative (FP)</mark> is a type 2 error or miss. Object of x was classified as not x

$$Accuracy=\frac{TP+TN}{Overall\ Total}$$
So correct classifications over all classifications. In a confusion matrix, it is the sum of the diagonals divided by the sum of all the other elements
![[Pasted image 20250206153854.png]]
![[Pasted image 20250206153923.png]]

<mark style="background: #ADCCFFA6;">True Positive Rate/Recall/Sensitivity</mark> is how many instances did you find out all of the instances. High TPR is good. Recall considers of the _actual_ objects of that class, how many were labeled as such.
$$TPR=\frac{TP}{TP+FN}$$
![[Pasted image 20250206154017.png]]

<mark style="background: #ADCCFFA6;">False Positive Rate/Fall Out</mark> is how many instances did you NOT find all the instances. The opposite of TPR. High FPR is bad
$$FPR=\frac{FP}{FP+TN}$$
![[Pasted image 20250206154153.png]]

<mark style="background: #ADCCFFA6;">True Negative Rate/Specificity</mark> This is similar to TPR. FPR + TNR = 1
$$TNR=\frac{TN}{FP+TN}$$
![[Pasted image 20250206154249.png]]

<mark style="background: #ADCCFFA6;">False Negative Rate/Miss Rate</mark> is TPR + FNR = 1. Both top row equations
$$FNR=\frac{FN}{TP+FN}$$
![[Pasted image 20250206154345.png]]

<mark style="background: #ADCCFFA6;">Precision</mark> is the positive predictive value. It reports on a column of the confusion matrix. Precision and recall are often reported together
$$Precision=\frac{TP}{FP+TP}$$
![[Pasted image 20250206154514.png]]

## F-Measure
The <mark style="background: #ADCCFFA6;">Harmonic Mean</mark> is the reciprocal of the arithmetic mean of the reciprocals of a set of numbers. In the case of 2 numbers, it is $\frac{2}{\frac{1}{x_{1}}+\frac{1}{x_{2}}}$

$$F-measure=\frac{2TP}{(FP+2TP+FN)}$$
![[Pasted image 20250206154746.png]]
