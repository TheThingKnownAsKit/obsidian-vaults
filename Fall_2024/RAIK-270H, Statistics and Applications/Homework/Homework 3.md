## Parts 1-2 printed in VSCode console

## Part 3: Combinations and Permutations
a. $8.8921857024\times10^{12}$
Sub-permutations given that there can be no repeat people selected. 12 of 18
$$P_{n,k}=\frac{n!}{(n-k)!}$$
n = 18, k = 12
$$\frac{18!}{6!}$$
= $8.8921857024\times10^{12}$
\
b. 375
Sub-permutations given that there are no repeat shirts and you can have 2, 3, or 4 shirts
n = 10, k = 2 or 3 or 4. Use choose notation
$$\frac{10!}{10!(10-2)!}+\frac{10!}{10!(10-3)!}+\frac{10!}{10!(10-4)!}$$
Aka $\operatorname{nCr}\left(10,2\right)+\operatorname{nCr}\left(10,3\right)+\operatorname{nCr}\left(10,4\right)$

= 375
Fix this

## Part 4: Bayesian Probability
a. 1/2
given that Y is uniformly distributed incrementing up to x, and x = 2, than y can ether be 1 or 2. This means the probability of y being 2 is 1/2

b. 13/48

Probabilities of y given x
x = 1: y can never equal 2 if x = 1 since y is distributed up to x. The probability of this is 0
x = 2: Calculated above as 1/2
x = 3: if x = 3, than y can be 1, 2, or 3, which makes the probability 1/3
x = 4: using the same logic above as x = 3, the probability is 1/4

x is uniformly distributed over 1-4 so the probability of x being anything in particular is 1/4

Using the given formula of $P(Y=2)=\sum_xP(Y=2|X=x)*P(X=x)$
x = 1 -> 0 * 1/4 = 0
x = 2 -> 1/2 * 1/4 = 1/8
x = 3 -> 1/3 * 1/4 = 1/12
x = 4 -> 1/4 * 1/4 = 1/16

Sum: 13/48 <--- final answer

c. 6/13
Use Bayes' Theorem: $P(A|B)=\frac{P(B|A)P(A)}{P(B)}$ where:
	P(A|B) is P(X = 2 | Y = 2)
	P(B|A) is P(Y = 2 | X = 2) which is 1/2, found in part a
	P(A) = is the probability of x = 2, which is 1/4
	P(B) = of y = 2 which is 13/48 from part b

So given all that above, then
$$\frac{1/2*1/4}{13/48}=6/13$$

## Part 5: More Probabilities
### a
Probability of any ticket being a winner is 4/100 = 0.04

BINOMAL DISTRIBUTION
$$P(k)=C_{n,k}p^k(1-p)^{n-k}$$
where n is the number of trials, k is the number of successes, and p is the probability of a success for each trial

HYPERGEOMETRIC DISTRIBUTION
$$P(k)=\frac{(C_{x,k})(C_{(N-x),(n-k)})}{C_{N,n}}$$
* k is the total successes you want
* n is the number of things chosen out of the sample
* N is the total sample size
* x is the success population

CHOOSE
$$C_{n,k}=\frac{n!}{k!(n-k)!}$$

i. 0.00000892578212166
k = 4
n = 7
N = 100
x = 4
N - x = 96, n - k = 3

Hypergeometric
$\frac{\frac{4!}{4!(4-4)!}*\frac{96!}{3!(96-3)!}}{\frac{100!}{7!(100-7)!}}=0.00000892578212166$

ii. 0.23165
k = 1
n = 7
N = 100
x = 4
N - x = 96, n - k = 6

$\frac{\frac{4!}{1!(4-1)!}*\frac{96!}{6!(96-6)!}}{\frac{100!}{7!(100-7)!}}=0.23165$

iii. 0.25540
Probability of at least 1 prize is 1 - the probability of getting 0
k = 0
n = 7
N = 100
x = 4
N - x = 96, n - k = 7

$\frac{\frac{4!}{0!(4-0)!}*\frac{96!}{7!(96-7)!}}{\frac{100!}{7!(100-7)!}}=0.744597670371$

$1 - 0.744597670371=0.25540$

### b
Every prime number known (except 2) is odd, and if you add an even amount of odd numbers together, the result is always even
So essentially, we're calculating the probability of picking 2

probability of picking 2 = 1/30 = 0.3

Still hypergeometric distribution
k = 1
n = 6
N = 30
x = 1
N - x = 29, n - k = 5

$\frac{\frac{1!}{1!(1-1)!}*\frac{29!}{5!(29-5)!}}{\frac{30!}{6!(30-6)!}}=1/5$

