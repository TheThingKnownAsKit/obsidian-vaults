## Properties of Discrete Probability Distributions
A <mark style="background: #ADCCFFA6;">probability mass function (pmf)</mark> assigns the probability that a discrete random variable is exactly equal to some value (typically depicted as a table, plot, or equation). Usually denoted with $P(X=x)$ or $p(x)$ for variable x
![[Pasted image 20241007175529.png]]
Basically using discrete values as categories and saying how close variable is to being that value

The <mark style="background: #ADCCFFA6;">cumulative distribution function (cdf)</mark> of a discrete random variable is the probability that for any number x, the observed value of the random variable will be at most x or $p(X\le x)$. Always starts at 0 and ends at 1 and never decreases as the value of X increases
	Example, $F(3)=o(X\le 3)=1/2$ read as the probability that X is less than or equal to 3 is one half
![[Pasted image 20241007175822.png]]
Basically a cdf combines different pmf values. What is the probability that someone will be either 0 or 1? just add it together. Depends on the value given in <=, could add multiple probabilities or none

The <mark style="background: #ADCCFFA6;">mean</mark> or <mark style="background: #ADCCFFA6;">expected value</mark> of a discrete random variable X is the sum of the possible values of X multiplied by the probability of the value. `$\mu$`
![[Pasted image 20241007180430.png]]
The mean is a weighted average of the possible values of X with the probabilities as weights

![[Pasted image 20241007180512.png]]First, construct a pmf, then sun the products of each categories probability and variable X. Sum of category x value

The <mark style="background: #ADCCFFA6;">variance</mark> of a discrete random variable X is a measure of the spread of a distribution. It is calculated with:
$$\sigma^2=V(X)=\sum\limits((x-\mu)^2*p(x))$$
The variance is a weighted average with the probabilities as the weights. Measures the average of the squared distance of each possible value of X from the mean

The <mark style="background: #ADCCFFA6;">standard deviation</mark> is the square root of the variance
$$\sigma=\sqrt{\sigma^2}$$
![[Pasted image 20241007181539.png]]

```python
from scipy.stats import rv_discrete

# Defines a list containing the outcomes in the sample space
x = [0,1,2,3,4,5,6]

# Defines a list containing the probabilities for each outcome
p = [0.1,0.2,0.3,0.1,0.1,0.0,0.2]

# Links the values in x to the probabilities in p
discvar = rv_discrete(values=(x,p))

# To find the mean, the .mean() method is used.
# Returns the mean of the discrete random variable
print(discvar.mean())

# To find the variance, the .var() method is used.

# Returns the variance of the discrete random variable 
print(discvar.var())

# To find the standard deviation, the .std() method is used.

# Returns the standard deviation of the discrete random variable
print(discvar.std())
```

## Binomial Distribution
### Binomial
A <mark style="background: #ADCCFFA6;">binomial distribution</mark> is a discrete random variable distribution with two possible values that have fixed probabilities that add up to 1. The probability for the value of a random variable with a binomial distribution is:
$$P(k)=C_{n,k}p^k(1-p)^{n-k}$$
where n is the number of trials, k is the number of successes, and p is the probability of a success for each trial. Remember that C is choose notation

![[Pasted image 20241007182010.png]]
![[Pasted image 20241007182042.png]]

The mean of one trial in a binomial distribution is:
$$\mu=\sum\limits(x*p(x))=0(1-p)+1(p)=p$$
Which means the distribution over n trials is the sum of the individual means, and is therefore:
$$\mu=np$$
The variance of one trial is:
$$\sigma^2=p(1-p)$$
And the variance of the distribution is:
$$\sigma^2=np(1-p)$$
The standard deviation of the binomial distribution is the square root of the variance,
$$\sigma=\sqrt{np(1-p)}$$
![[Pasted image 20241007182413.png]]

```python
from scipy.stats import binom

# Defines the number of successes, the number of trials, and the probability of a success in each trial
k, n, p = 5,10, 0.7
# binom.pmf can be used to calculate the probability of k successes for a given n and p.

# Calculates the probability of k successes given the defined n and p
P = binom.pmf(k, n, p)
print(P)

# binom.cdf gives the cumulative probability of k or fewer successes for a given n and p

# Calculates the cumulative probability of k or fewer successes
cp = binom.cdf(k, n, p)
print(cp)

# The mean and variance are calculated using binom.stats.

# Returns the mean of the distribution
mean  =  binom.stats(n, p, moments = 'm')
print(mean)

# Returns the variance of the distribution 
var = binom.stats(n, p, moments='v')
print(var)
```

### Bernoulli
The <mark style="background: #ADCCFFA6;">Bernoulli distribution</mark> is the special case of a binomial distribution where n = 1. It is the probability distribution of a single trial with two possible outcomes

The mean is:
$$\mu=p$$
The variance of the distribution is
$$\sigma^2=p(1-p)$$
The standard deviation is:
$$\sigma=\sqrt{p(1-p)}$$
![[Pasted image 20241007182615.png]]

## Hypergeometric Distribution
The <mark style="background: #ADCCFFA6;">hypergeometric distribution</mark> gives the probability of k successes when choosing a sample of n objects without replacement out of a population of N objects, of which x are successes
Similar to binomial in that only two possibilities (x or z) exist per trial. <mark style="background: #BBFABBA6;">The difference is the probabilities change each trial in hypergeometric, while they remain constant in binomial</mark>
$$P(k)=\frac{(C_{x,k})(C_{(N-x),(n-k)})}{C_{N,n}}$$
* k is the total successes you want
* n is the number of things chosen out of the sample
* N is the total sample size
* x is the success population

![[Pasted image 20241007183012.png]]
![[Pasted image 20241007183034.png]]

The mean of a hypergeometric distribution is
$$\mu=\frac{nx}{N}$$
and the variance and standard deviation are:
$$\sigma^2=\frac{nx(N-x)(N-n)}{N^2(N-1)}$$
$$\sigma=\sqrt{\frac{nx(N-x)(N-n)}{N^2(N-1)}}$$

![[Pasted image 20241007183234.png]]
![[Pasted image 20241007183246.png]]

```python
from scipy.stats import hypergeom
import matplotlib.pyplot as plt

# Defines the number of successes in the sample, size of the population, number of successes in the population, and size of the sample
k, N, x, n = 12, 52, 26, 20

# hypergeom.pmf can be used to calculate the probability of k successes for a given N, x, and n.
# Calculates the probability of k successes given the defined N, x, and n
P = hypergeom.pmf(k, N, x, n, loc=0)
print(P)

# hypergeom.cdf gives the cumulative probability of k or fewer successes for a given N, x, and n.
# Calculates the cumulative probability of k or fewer successes
cp = hypergeom.cdf(k, N, x, n)
print(cp)

# The mean and variance are calculated using hypergeom.stats.
# Returns the mean of the distribution
mean = hypergeom.stats(N, x, n, loc=0, moments='m')
print(mean)

# Returns the variance of the distribution
var = hypergeom.stats(N, x, n, loc=0, moments='v')
print(var)
```

## Poisson Distribution
The <mark style="background: #ADCCFFA6;">Poisson distribution</mark> gives the probability of k independent, randomly occurring events happening over a period or area where $\lambda$ events happen on average. The constant e (Euler's number) is what that is
$$P(k)=e^{-\lambda}\frac{\lambda^k}{k!}$$
* k is the number of successes you're looking for
* $\lambda$ is the average frequency of successes
* NOTE: $\lambda$ and k have to be in the same time units

Used for situations where the average count is fairly low
![[Pasted image 20241007183627.png]]

![[Pasted image 20241007183702.png]]

The distribution is skewed to the right since the probability of fewer than zero events occurring is always zero, but the probabilities to the right of the mean only ASYMPTOTE to zero
![[Pasted image 20241007183800.png]]

![[Pasted image 20241007183821.png]]

```python
from scipy.stats import poisson

# Defines the desired number of successes and the mean of the distribution
x, lam= 12, 9

# poisson.pmf can be used to calculate the probability of x successes for a given lambda.
# Calculates the probability of x successes given the defined lambda
P = poisson.pmf(x, lam)
print(P)

# poisson.cdf gives the cumulative probability of x or fewer successes for a given lambda.
# Calculates the cumulative probability of x or fewer successes given the defined lambda
cp = poisson.cdf(x, lam)
print(cp)

# The mean and variance are calculated using poisson.stats.
# Returns the mean of the distribution
mean = poisson.stats(lam, moments='m')
print(mean)

# Returns the variance of the distribution 
var = poisson.stats(lam, moments='v')
print(var)

# poisson.rvs can be used to generate a set of random numbers with the Poisson distribution defined by lambda.
# Generates 10 random numbers with a Poisson distribution with a mean of lam
r = poisson.rvs(lam, size=10)
print(r)
```