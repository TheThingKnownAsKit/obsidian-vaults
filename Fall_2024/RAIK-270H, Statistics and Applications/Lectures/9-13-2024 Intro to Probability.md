![[59.txt]]

<mark style="background: #ADCCFFA6;">Degrees of Freedom</mark> is the number of independent values that can vary without breaking any constraints. Aka if I change one value will it change the standard deviation or mean?
	Constraints are like values you have already calculated based on the existing data. It constrains what you can and cannot change

<mark style="background: #ADCCFFA6;">Probability</mark> is how likely an event is to occur
An <mark style="background: #ADCCFFA6;">event</mark> is specifically (in this class) a subset of sample space
	For example, an event could be the possible outcomes that the number is odd and less than 4 if you roll a 6-sided die -> A = {1, 3} which is also actually a <mark style="background: #ADCCFFA6;">compound event</mark> because it contains multiple outcomes
<mark style="background: #ADCCFFA6;">Sample space</mark> is the set of all possible outcomes
And an <mark style="background: #ADCCFFA6;">outcome</mark> is the result of an experiment
	The side that ends up facing up will be the outcome
And an <mark style="background: #ADCCFFA6;">experiment</mark> is a procedure resulting in an outcome
	Roll dice is an experiment

A <mark style="background: #ADCCFFA6;">set</mark> is a data structure that stores unique elements of the same type. Can be sorted or unsorted depending on the implementation (unsorted in Python)
SET NOTATION:
S = {1,2,3,4,5,6}
<mark style="background: #ADCCFFA6;">Union</mark> is the joining of sets (no duplicates)
<mark style="background: #ADCCFFA6;">Intersection</mark> only includes the outcomes that are in both sets
The <mark style="background: #ADCCFFA6;">complement</mark> is not the set. It is all the outcomes that are NOT in a set
Two events are considered <mark style="background: #ADCCFFA6;">mutually exclusive</mark>  if they contain no shared outcomes (the Venn diagram for the subsets has no overlap). Basically the intersection of A and B = empty set

<mark style="background: #ADCCFFA6;">The Axioms of Probability</mark> are the three fundamental properties that form the basis of probability theory. They are called probability axioms or the Kolmogorov axioms
<mark style="background: #BBFABBA6;">For A and B mutually exclusive events in sample space S</mark> (where P(A) means probability of A):
1. 0 $\le$ P(A) $\le$ 1 - the probability of an outcome from an event is between 0% and 100%
2. P(S) = 1 - the probability of AN outcome at all is 100%. Something will always happen
3. P(A $\cup$ B) = P(A) + P(B) - For mutually exclusive events, the probability of an outcome from either event is the sum of probabilities for each event

If the events are NOT MUTUALLY EXCLUSIVE, the axioms do not apply and 