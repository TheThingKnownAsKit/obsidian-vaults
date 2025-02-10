## Introduction to Probability
An <mark style="background: #ADCCFFA6;">experiment</mark> is a procedure that results in one out of a number of possible outcomes
An <mark style="background: #ADCCFFA6;">outcome</mark> is the result of an experiment
The set of all possible outcomes is the <mark style="background: #ADCCFFA6;">sample space</mark>

A subset of the sample space is called an <mark style="background: #ADCCFFA6;">event</mark>
A <mark style="background: #ADCCFFA6;">compound event</mark> is a subset of the sample space consisting of more than one outcome
A <mark style="background: #ADCCFFA6;">simple event</mark> is a subset with a single outcome

## Addition Rule and Complements
### Sets
![[Pasted image 20241007171355.png]]

The <mark style="background: #ADCCFFA6;">union</mark> of two events A and  B is denoted as $A\cup B$ (cup) and is the event that includes outcomes in A or B or both
![[Pasted image 20241007171437.png]]

The <mark style="background: #ADCCFFA6;">intersection</mark> of two events A and B is denoted $A\cap B$ (cap) and is the event consisting of outcomes that are in both A and B
![[Pasted image 20241007171528.png]]

The <mark style="background: #ADCCFFA6;">complement</mark> of an event A is denoted $\overline{A}$ and is the event consisting of outcomes that are not in A
![[Pasted image 20241007171618.png]]

### Addition Rules
Two events A and B are <mark style="background: #ADCCFFA6;">mutually exclusive</mark> if $A\cap B=\emptyset$. They have NOTHING in common
![[Pasted image 20241007171749.png]]

<mark style="background: #BBFABBA6;">Probability has three fundamental properties, or axioms:</mark>
Let A and B be mutually exclusive events in the sample space S
1. $0\le P(A) \le 1$
2. $P(S)=1$
3. $P(A\cup B)=P(A)+P(B)$

The axioms have two important consequences, the complement rule and the addition rule of probability

The <mark style="background: #ADCCFFA6;">complement rule</mark> relates the probability of an event to the probability of the complement of the event:
For any event A, if the probability of A is P(A), the probability of $\overline{A}$ is $$P(\overline{A})=1-P(A)$$

The <mark style="background: #ADCCFFA6;">addition rule</mark> generalizes axiom 3 to events that are NOT MUTUALLY EXCLUSIVE
	For any events A and B
$$P(A\cup B)=P(A)+P(B)-P(A\cap B)$$
If A and B are mutually exclusive events, and it reduces to axiom 3 which is = 0

## Multiplication Rule and Independence
Two events are <mark style="background: #ADCCFFA6;">independent</mark> if the probability of one event does not affect the probability of the other

The <mark style="background: #ADCCFFA6;">multiplication rule</mark> gives the probability of 2 independent events happening together
Let A and B be independent events. The probability that both A and B occur is
$$P(A\text{ and }B)=P(A)P(B)$$
You can also generalize the multiplication rule to more than 2 independent events, just multiply everything together

## Conditional Probability
The <mark style="background: #ADCCFFA6;">conditional probability</mark> of an event A given event B HAS OCCURRED is denoted as $P(A|B)$ and is equivalent to $\frac{P(A\cap B)}{P(B)}$

Note: If they are mutually exclusive events, and you already know B has occurred, than the probability of A becomes 0

The <mark style="background: #ADCCFFA6;">law of total probability</mark> states that if the sample space is partitioned into two or more mutually exclusive subevents, the probability of an event B can be expressed in terms of conditional probabilities given each of the subevents
![[Pasted image 20241007173302.png]]
