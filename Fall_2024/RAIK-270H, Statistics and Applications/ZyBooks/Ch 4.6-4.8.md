## 4.6 Properties of continuous probability distributions
A <mark style="background: #ADCCFFA6;">probability density function (pdf)</mark> describes the relative likelihood of all values for a continuous random variable
	The notation f⁡(x) is typically used for the pdf
	Usually represented as a graph
	The probability is the area under the curve of the graph (integral)

A <mark style="background: #ADCCFFA6;">cumulative distribution function (cdf)</mark> of a continuous random variable is the probability that for any number x, the observed value of the random variable will be at most x or p⁡(X≤x)
	The notation F⁡(x) is typically used for the cdf of X, in contrast to lower-case f⁡(x) for the pdf
	Basically the integral of pdf. Directly is the probability

The <mark style="background: #ADCCFFA6;">mean</mark> $\mu$ <mark style="background: #ADCCFFA6;">or expected value</mark> E⁡(X) of a continuous random variable X is a measure of the center of the distribution. The mean is a weighted average of the possible values of the random variable, with the pdf providing the weights
	Graphically, the mean is where a pivot is placed so that the pdf balances

The <mark style="background: #ADCCFFA6;">variance</mark> $\sigma^2$ of a continuous random variable X is a measure of the spread of a distribution. The variance, like the mean, is a weighted average. The variance averages the squared distance of each possible value of X from the mean, with weights provided by the pdf

The <mark style="background: #ADCCFFA6;">standard deviation</mark> $\sigma$ is another measure of the spread of the distribution. The standard deviation is the square root of the variance, $\sigma=\sqrt{\sigma^2}$

## 4.7 Normal distribution
### Normal Distribution
The <mark style="background: #ADCCFFA6;">normal distribution</mark> is a continuous probability distribution characterized by a bell-shaped probability distribution function and is symmetric around the mean $\mu$
	Bell curve, Gaussian distribution
![[Pasted image 20241024135854.png]]

Unimodal and symmetric distributions, such as the normal distribution, follow a definite pattern useful for obtaining probabilities and interpreting outcomes. A <mark style="background: #ADCCFFA6;">unimodal distribution</mark> is a distribution with exactly one mode. In such distributions, the mean, median, and mode are equal

The <mark style="background: #ADCCFFA6;">empirical rule</mark> states that for any unimodal and symmetric distribution: (1) 68% of the data fall within one standard deviation of the mean, (2) 95% of the data fall within two standard deviations of the mean, and (3) 99.7% of the data fall within three standard deviations of the mean. Mathematically,
![[Pasted image 20241024140042.png]]
Within 2 standard deviations is normal, more than two is abnormal

A <mark style="background: #ADCCFFA6;">z-score</mark> is a signed value that indicates the number of standard deviations a quantity is from the mean
	A positive z-score indicates that the quantity is above the mean
	a negative z-score indicates that the quantity is below the mean
	A z-score with high absolute value implies that the quantity is farther from the mean, so more unusual
	Used for comparing things with different unimodal symmetric distributions and determining if something is unusual
$$z=\frac{x-\mu}{\sigma}$$
where x is the raw score, $\mu$ is the mean, and $\sigma$ is the standard deviation

z-score example:
![[Pasted image 20241024140415.png]]![[Pasted image 20241024140436.png]]

```Python
import pandas as pd

# Create a DataFrame containing the eps data
earnings_surprise = pd.DataFrame([11.36, 7.89, 1.96, 0, -3.12, -9.52])
print(earnings_surprise.mean())
print(earnings_surprise.std())

# Compute z-score
print((11.36-earnings_surprise.mean())/earnings_surprise.std())
```

```Python
import scipy.stats as st

# For a normal distribution, if the mean is 0 
# and the standard deviation is 1, 
# what is P(z <= -0.25)?
print(st.norm.cdf(-0.25, 0, 1))

# For a normal distribution, if the mean is 0 
# and the standard deviation is 1,
# what is P(z <= 1.5)?
print(st.norm.cdf(1.5, 0, 1))

# For a normal distribution, if the mean is 0
# and the standard deviation is 1, 
# what is P(z >= -0.25)?
print(st.norm.sf(-0.25, 0, 1))

# For a normal distribution, if the mean is 0 
# and the standard deviation is 1, 
# what is P(z >= 1.5)?
print(st.norm.sf(1.5, 0, 1))

# To find the probability between two values, the
# difference between the two probabilities is calculated.
# For a normal distribution, if the mean is 0 
# and the standard deviation is 1, 
#what is P(-0.25 <= z <= 1.5)?
print(st.norm.cdf(1.5, 0, 1) - st.norm.cdf(-0.25, 0, 1))

# For a normal distribution, if the mean is 0 
# and the standard deviation is 1, 
# what is P(1.5 <= z <= 2.85)?
print(st.norm.cdf(2.85, 0, 1) - st.norm.cdf(1.5, 0, 1))

# Both norm.cdf() and norm.sf() can also be 
# used for non-standard normal distributions, 
# that is, when the mean is not 0  or the 
# standard deviation is not 1.
# For a normal distribution, if the mean is 55
# and the standard deviation is 7.5, 
# what is P(x <= 62)?
print(st.norm.cdf(62, 55, 7.5))

# For a normal distribution, if the mean is 55
# and the standard deviation is 7.5, 
# what is P(x >= 51)?
print(st.norm.sf(51, 55, 7.5))

# For a normal distribution, if the mean is 55 
# and the standard deviation is 7.5, 
# what is P(49 <= x <= 60)?
print(st.norm.cdf(60, 55, 7.5) - st.norm.cdf(49, 55, 7.5))
```

```Python
import scipy.stats as st

# For a normal distribution, if the mean is 0 and 
# the standard deviation is 1, what is z* if P(z < z*) = 0.135?
print(st.norm.ppf(0.135, 0, 1))

# For a normal distribution, if the mean is 0 and 
# the standard deviation is 1, what is z* if P(z > z*) = 0.405?
print(st.norm.isf(0.405, 0, 1))

# Both norm.ppf() and norm.isf() can also be used with non-standard normal distributions.
# For a normal distribution, if the mean is 55 and 
# the standard deviation is 7.5, what is x* if P(x < x*) = 0.8247?
print(st.norm.ppf(0.8247, 55, 7.5))

# For a normal distribution, if the mean is 55 and 
# the standard deviation is 7.5, what is x* if P(x > x*) = 0.95?
print(st.norm.isf(0.95, 55, 7.5))
```

### Sampling Distributions
The <mark style="background: #ADCCFFA6;">sampling distribution</mark> of the mean, denoted as $\overline{X}$ is the distribution of sample means when taking random samples of the same size
The <mark style="background: #ADCCFFA6;">mean of the sample means</mark>, denoted as $\mu_{\overline{X}}$ is the population mean. That is, $\mu_{\overline{X}}=\mu$
The <mark style="background: #ADCCFFA6;">standard error (SE)</mark> is the standard deviation of the sampling distribution, denoted by $\sigma_{\overline{X}}$, when sampling WITH REPLACEMENT. That is, $\sigma_{\overline{X}}=\frac{\sigma}{\sqrt{n}}$ 

Note, the <mark style="background: #BBFABBA6;">standard deviation requires a correction factor when sampling without replacement.</mark> This correction factor is $\sqrt\frac{N-n}{N-1}$ where N is population size and n is sample size

![[Pasted image 20241024141102.png]]
![[Pasted image 20241024141118.png]]
![[Pasted image 20241024141130.png]]

![[Pasted image 20241024141202.png]]
![[Pasted image 20241024141315.png]]
![[Pasted image 20241024141331.png]]

A <mark style="background: #ADCCFFA6;">binary categorical variable</mark> is a random variable that can only take on two possible names or labels.

![[Pasted image 20241024141504.png]]
![[Pasted image 20241024141522.png]]
![[Pasted image 20241024141539.png]]

## 4.8 Student's t-Distribution
The <mark style="background: #ADCCFFA6;">Student's t-distribution or t-distribution</mark> is used in place of the normal distribution in situations where the sample size is too small or the population standard deviation is unknown
	One parameter. Degrees of freedom (df) equal to n - 1 of sample size n
	As n increases it approaches the normal distribution with a mean of 0 and standard deviation of 1
![[Pasted image 20241024142248.png]]
Calculated with:
$$t=\frac{\overline{x}-\mu}{\frac{s}{\sqrt{n}}}$$
where $\overline{x}$ is the sample mean, s is the sample standard deviation, and n is the sample size

```Python
import scipy.stats as st

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t < -0.25)?
print(st.t.cdf(-0.25, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t < 1.5)?
print(st.t.cdf(1.5, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t > -0.25)?
print(st.t.sf(-0.25, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t > 1.5)?
print(st.t.sf(1.5, 30, 0, 1))

# To find the probability between two critical values, 
# the difference between the two probabilities is calculated.
# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(-0.25 < t < 1.5)?
print(st.t.cdf(1.5, 30, 0, 1) - st.t.cdf(-0.25, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(1.5 < t < 2.85)?
print(st.t.cdf(2.85, 30, 0, 1) - st.t.cdf(1.5, 30, 0, 1))

# Both t.cdf() and t.sf() can also be used for t-distributions 
# with different degrees of freedom and when the mean is 
# not 0 or the standard deviation is not 1.
# For a t-distribution, if the degrees of freedom is 59, the mean is 55,
# and the standard deviation is 7.5, what is P(t < 62)?
print(st.t.cdf(62, 59, 55, 7.5))

# For a t-distribution, if the degrees of freedom is 34, the mean is 55,
# and the standard deviation is 7.5, what is P(t > 51)?
print(st.t.sf(51, 34, 55, 7.5))

# For a t-distribution, if the degrees of freedom is 59, the mean is 55,
# and the standard deviation is 7.5, what is P(49 < t < 60)?
print(st.t.cdf(60, 59, 55, 7.5) - st.t.cdf(49, 59, 55, 7.5))import scipy.stats as st

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t < -0.25)?
print(st.t.cdf(-0.25, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t < 1.5)?
print(st.t.cdf(1.5, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t > -0.25)?
print(st.t.sf(-0.25, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(t > 1.5)?
print(st.t.sf(1.5, 30, 0, 1))

# To find the probability between two critical values, 
# the difference between the two probabilities is calculated.
# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(-0.25 < t < 1.5)?
print(st.t.cdf(1.5, 30, 0, 1) - st.t.cdf(-0.25, 30, 0, 1))

# For a t-distribution, if the degrees of freedom is 30, the mean is 0,
# and the standard deviation is 1, what is P(1.5 < t < 2.85)?
print(st.t.cdf(2.85, 30, 0, 1) - st.t.cdf(1.5, 30, 0, 1))

# Both t.cdf() and t.sf() can also be used for t-distributions 
# with different degrees of freedom and when the mean is 
# not 0 or the standard deviation is not 1.
# For a t-distribution, if the degrees of freedom is 59, the mean is 55,
# and the standard deviation is 7.5, what is P(t < 62)?
print(st.t.cdf(62, 59, 55, 7.5))

# For a t-distribution, if the degrees of freedom is 34, the mean is 55,
# and the standard deviation is 7.5, what is P(t > 51)?
print(st.t.sf(51, 34, 55, 7.5))

# For a t-distribution, if the degrees of freedom is 59, the mean is 55,
# and the standard deviation is 7.5, what is P(49 < t < 60)?
print(st.t.cdf(60, 59, 55, 7.5) - st.t.cdf(49, 59, 55, 7.5))
```

![[Pasted image 20241024142422.png]]
![[Pasted image 20241024142443.png]]

```Python
import scipy.stats as st

# For a t-distribution, if the degrees of freedom is 49, the mean is 0 and 
# the standard deviation is 1, what is t* if P(t < t*) = 0.135?
print(st.t.ppf(0.135, 49, 0, 1))

# For a t-distribution, if the degrees of freedom is 49, the mean is 0 and 
# the standard deviation is 1, what is t* if P(t > t*) = 0.405?
print(st.t.isf(0.405, 49, 0, 1))

# Both t.ppf() and t.isf() can also be used with non-standard t-distributions.
# For a t-distribution, if the degrees of freedom is 24, the mean is 55 and 
# the standard deviation is 7.5, what is t* if P(t < t*) = 0.8247?
print(st.t.ppf(0.8247, 24, 55, 7.5))

# For a t-distribution, if the degrees of freedom is 24, the mean is 55 and 
# the standard deviation is 7.5, what is t* if P(t > t*) = 0.95?
print(st.t.isf(0.95, 24, 55, 7.5))
```