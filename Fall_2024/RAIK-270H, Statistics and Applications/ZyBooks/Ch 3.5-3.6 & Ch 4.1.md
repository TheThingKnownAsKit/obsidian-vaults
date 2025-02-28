## Bayes' Theorem
<mark style="background: #ADCCFFA6;">Bayes' Theorem</mark> relates the probability of an event A given a condition B to the probability of the condition B given that the event A has occurred. <mark style="background: #BBFABBA6;">It flips the probabilities so if you know one probability but not the other, you can solve for what's missing</mark>
Let A and B be events in the sample space such that P(A) != 0 and P(B) != 0/ Then,
$$P(A|B)=\frac{P(B|A)P(A)}{P(B)}=\frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|\overline{A})P(\overline{A})}$$

![[Pasted image 20241007174059.png]]![[Pasted image 20241007174112.png]]

## Combinations and Permutations
<mark style="background: #ADCCFFA6;">Counting methods</mark> or <mark style="background: #ADCCFFA6;">combinatorics</mark> are mathematical approaches to determining the number of possible outcomes

The <mark style="background: #ADCCFFA6;">multiplication rule of counting</mark> states that if one event can occur in A ways and another event in B ways, the number of possible ways both events can occur is A x B

A <mark style="background: #ADCCFFA6;">permutation</mark> is a possible ordering of a set of objects. Uses the multiplication rule to define number of possible permutations. The number of possible permutations is n! where n is the number of objects
	In python, use `math.factorial(n)`

A <mark style="background: #ADCCFFA6;">sub-permutation</mark> is a list of possible permutations given not all the possible objects are included in the ordering. For example, you can have no repeat values
The formula for the number of ways to produce ordered sets of size k from a collection of n objects is:
$$P_{n,k}=\frac{n!}{(n-k)!}$$

A <mark style="background: #ADCCFFA6;">combination</mark> is a possible set of objects chosen in any order; the order of selection does not matter. Permutation usually places things in order. The formula for the number of ways to select unordered sets of size k from a collection of n objects is:
$$C_{n,k}=\frac{n!}{k!(n-k)!}$$
Read as n choose k; since order does not matter, the expression counts the number of ways to simply "choose" a set of k objects at once from a group of n objects

Note: This is all for permutations and combinations; ie the number of ways something can happen. <mark style="background: #BBFABBA6;">If you want the PROBABILITY of all this, you have to divide the number of permutations/combinations by the total number of possible outcomes</mark>

## Introduction to Random Variables
A <mark style="background: #ADCCFFA6;">random variable</mark> is a rule that assigns a number to every outcome in the sample space of an experiment. The number is the likelihood for it to happen. Usually denoted with a capital letter

A <mark style="background: #ADCCFFA6;">discrete random variable</mark> can take on a countable number of distinct values like integers between 0 and 100 or 0 and 1

A <mark style="background: #ADCCFFA6;">continuous random variable</mark> can take on any value within a range of values (allowed to be floats basically)
