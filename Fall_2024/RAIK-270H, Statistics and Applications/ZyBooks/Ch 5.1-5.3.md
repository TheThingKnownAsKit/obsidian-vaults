## Confidence Intervals
A <mark style="background: #ADCCFFA6;">point estimate</mark> is a single value estimate for an unknown parameter
An <mark style="background: #ADCCFFA6;">interval estimate</mark> is a range of possible values for the parameter being estimated

<mark style="background: #ADCCFFA6;">Accuracy</mark> is measured in terms of bias, or how close on average the estimate is to the population parameter being estimated. Numerically, bias is the distance between the mean of the sampling distribution and the population parameter being estimated
<mark style="background: #ADCCFFA6;">Precision</mark> is how variable estimates are to one another if the estimation process is repeated. Precision is measured in terms of the standard error of the sampling distribution

A <mark style="background: #ADCCFFA6;">confidence interval</mark> is an interval estimate constructed such that the probability the method produces an interval that contains the population parameter is given
Given by:
$$[\overline{x}-m,\overline{x}+m]$$
Where m is the margin of error. If the margin of error is not known, use margin of error calculations using t*

The percentage of times the method produces a confidence interval containing the parameter is called the <mark style="background: #ADCCFFA6;">confidence level</mark>, which is denoted by c. Common values for c are 90%, 95%, and 98%
The <mark style="background: #ADCCFFA6;">margin of error</mark>, denoted by m, is a measure of the estimate's precision and is constructed from a multiplier and the standard error of the statistic's sampling distribution
The <mark style="background: #ADCCFFA6;">multiplier</mark>, or critical value, for a c% confidence interval is the number of standard deviations about the mean of the sampling distribution that would capture c% of the distribution
$$m=(multiplier)(standard\ error)$$

## Confidence Intervals for Population Means
![[Pasted image 20241105113043.png]]
(see [[Ch 4.6-4.8]]) for z-score details

![[Pasted image 20241105113150.png]]

norm.interval() is used to find a confidence interval for a normally distributed variable
```Python
import scipy.stats as st
import pandas as pd
import math
print(st.norm.interval(0.95, 0, 1))

scores = pd.read_csv('ExamScores.csv')
sigma = 2.5
mean = scores['Exam1'].mean()
stderr = sigma/math.sqrt(len(scores['Exam1']))
print(st.norm.interval(0.99, mean, stderr))
```

<mark style="background: #BBFABBA6;">MARGIN OF ERROR AND SAMPLE SIZE WHEN STDEV $\sigma$ IS KNOWN</mark>
$$n=(\frac{z^*\sigma}{m})^2$$
Where n is the sample size needed to guarantee a margin of error of m, z is the critical score, $\sigma$ is the standard population deviation, and m is the margin of error
![[Pasted image 20241105113519.png]]

<mark style="background: #BBFABBA6;">MARGIN OF ERROR AND SAMPLE SIZE FOR MEANS WHEN STEDEV IS UNKNOWN</mark>
In this situation, you use the t* instead
$$n=(\frac{t^*s}{m})^2$$
![[Pasted image 20241105114706.png]]

<mark style="background: #ADCCFFA6;">t*</mark> is the critical value that depends on the degrees of freedom and significance level. Calculated similarly to the z-score:
$$t^*\frac{s}{\sqrt{n}}$$
Where t* is the critical value from the table below, n is the sample size, and s is the sample standard deviation
![[Pasted image 20241105114044.png]]
Where df is the degrees of freedom (sample size - 1) and $\alpha$ is the signifance level (usually given)

![[Pasted image 20241105114241.png]]

```Python
import scipy.stats as st

n = 100

# Degrees of freedom is number of samples minus 1
df = n - 1

mean = 219

# The standard error is standard deviation/sqrt(number of samples)
stderr = 35.0/(n ** 0.5)

print(st.t.interval(0.95, df, mean, stderr))
```

```Python
import pandas as pd
import scipy.stats as st
scores = pd.read_csv('ExamScores.csv')

# Let n be the number of students who took Exam 1.
n = scores[['Exam1']].count()

# Degrees of freedom is number of samples minus 1
df = n - 1

# The mean of Exam1 scores are obtained
mean = scores[['Exam1']].mean()

# The standard error is standard deviation/sqrt(number of samples)
stdev = scores[['Exam1']].std()
stderr = stdev/(n ** 0.5)

print(st.t.interval(0.95, df, mean, stderr))
```

## Hypothesis Testing
A <mark style="background: #ADCCFFA6;">hypothesis</mark> is a proposed explanation of a phenomenon, usually as a starting point for further analysis
<mark style="background: #ADCCFFA6;">Hypothesis testing</mark> is the formal process by which a hypothesis is retained or rejected. Hypothesis testing compares two competing hypotheses about a population, the null hypothesis and the alternative hypothesis

A <mark style="background: #ADCCFFA6;">null hypothesis</mark>, denoted $H_0$, is a statement assumed to be true unless sufficient data indicates otherwise. Typically, a null hypothesis is a statement of equality between the true value of the population parameter and the hypothesized value or a statement of no difference between the parameters of two populations
An <mark style="background: #ADCCFFA6;">alternative hypothesis</mark>, denoted $H_\alpha$, is a statement that contradicts $H_0$. Typically, an alternative hypothesis asserts that the true value of the population parameter is not the same as the hypothesized value or that the parameters for two populations are different
- A <mark style="background: #ADCCFFA6;">left-tailed alternative hypothesis</mark> asserts that the value of a parameter is less than the value asserted in the null hypothesis.
- A <mark style="background: #ADCCFFA6;">right-tailed alternative hypothesis</mark> asserts that the value of a parameter is greater than the value asserted in the null hypothesis.
- A <mark style="background: #ADCCFFA6;">two-tailed alternative hypothesis</mark> asserts that the value of a parameter is not equal to, that is, either less than or greater than the value asserted in the null hypothesis.

A <mark style="background: #ADCCFFA6;">test statistic</mark> is a value calculated from sample data during hypothesis testing that measures the degree of agreement between the sample data and the null hypothesis. Mathematically, the test statistic is the difference between the estimate and the value asserted in the null hypothesis divided by the standard error
![[Pasted image 20241105115222.png]]

In hypothesis testing, the probability of obtaining a result that is as extreme or more extreme than the data if the null hypothesis were true is known as the <mark style="background: #ADCCFFA6;">p-value</mark>. The p-value of a result is determined from the test statistic. If the p-value is less than a specified significance level, denoted by α, then two possibilities exist
- The null hypothesis is true and the observed data is relatively unusual with a sample statistic that is extreme simply due to chance.
- The null hypothesis is false and the alternative hypothesis provides a more reasonable explanation for the population parameter.
In most fields, $\alpha=0.05$ is used most often as the significance level for hypothesis testing. The probability that a result with an extreme deviation from the null hypothesis is due to chance must be 5% or less to be statistically significant

A <mark style="background: #ADCCFFA6;">type I error</mark> is the incorrect rejection of a true null hypothesis, and a <mark style="background: #ADCCFFA6;">type II error</mark> is the failure to reject a false null hypothesis. In other words, a type I error is a false positive and a type II error is a false negative