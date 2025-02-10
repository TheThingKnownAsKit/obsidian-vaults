## Data collection and description
<mark style="background: #ADCCFFA6;">Types and collection methods</mark>

Quantitative data is measurable
Qualitative data is harder to measure (usually in text form not numbers)
Objective data is not up for interpretation
Subjective data is up for interpretation

Active collection is like an experiment or survey etc
Passive collection is observation

---

<mark style="background: #ADCCFFA6;">Descriptive Statistics</mark>
	Mean, median, and mode
	Variance and standard deviation

Mean is the average. Sum everything and divide it by 2
Median is the middle number. If the amount of numbers is even, sum the middle two and divide by 2
Mode is the most frequent number. If there is a tie it is multi-modal

Variance is just how much the data varies
$$\text{var}_p=\frac{\sum\limits^n_{i=1}(x_i-\overline{x})^2}{n}$$
$$\text{var}_s=\frac{\sum\limits^n_{i=1}(x_i-\overline{x})^2}{n-1}$$
We square it because:
1. We don't care if the value is below or above the mean (pos/neg)
2. We want to exacerbate the huge differences from the mean

Standard deviation is variance square root. This is to put it back into the original units. NOT the same thing as just the original equation without the square. We need the square to get rid of negatives
$$\sigma_p=\sqrt{\text{var}_p}=\sqrt{\frac{\sum\limits^n_{i=1}(x_i-\overline{x})^2}{n}}$$
$$\sigma_s=\sqrt{\text{var}_s}=\sqrt{\frac{\sum\limits^n_{i=1}(x_i-\overline{x})^2}{n-1}}$$

---

<mark style="background: #ADCCFFA6;">Visualization types</mark>
You know what graphs are
## Probability principles
<mark style="background: #ADCCFFA6;">Sets, events, and Venn diagrams</mark>

An event is exactly what it sounds like. Something happens. An event is a subset of sample space (the set of all possible outcomes)

A set is a data structure that stores unique elements of the same type. S = {1,2,3,4,5,6}

Union is the joining of sets (no duplicates). A or B. A $\cup$ B
Intersection only includes the outcomes that are in both sets. A and B. A $\cap$ B
The complement is not the set. It is all the outcomes that are NOT in a set. $\overline{A}$

You know Venn diagrams


---

<mark style="background: #ADCCFFA6;">Addition rule</mark>

The general addition rule for any events A and B is
$$P(A\cup B)=P(A)+P(B)-P(A\cap B)$$


---

<mark style="background: #ADCCFFA6;">Multiplication rule</mark>

For independent events
$$P(A\cap B)=P(A)*P(B)$$

For any event:
$$P(A\cap B)=P(A)*P(B|A)$$
Read as probability of B given A. Note if there is no known information to determine P(B|A), it defaults to pretending they're independent


---

<mark style="background: #ADCCFFA6;">Independence and mutual exclusion</mark>

Sets are mutually exclusive if they have no events in common. Their intersection is an empty set

Independence just means the occurrence of one event does not impact the occurrence of another

---

<mark style="background: #ADCCFFA6;">Conditional probability and Bayes’ Theorem</mark>

Conditional probability, the probability of A given B, is
$$P(A|B)=\frac{P(A\cap B)}{P(B)}$$

Note:
For mutually exclusive events A and B, P(A|B) = P(B|A) = 0
For independent events A and B, P(A|B) = A and P(B|A) = B

Bayes' Theorem is for when we know P(B|A) but we want to solve for P(A|B)
$$P(A|B)=\frac{P(B|A)P(A)}{P(B)}=\frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|\overline{A})P(\overline{A})}$$
Both equations work, depends on known information
## Probability distributions
<mark style="background: #ADCCFFA6;">Random variables (concept)</mark>
A random variable will take on some probability described. Usually denoted as a capital letter. Like the variable A has a 50% chance of happening

---

<mark style="background: #ADCCFFA6;">Central limit theorem</mark>
The distributions of sample means approximates a normal distribution as the sample size increases, regardless of the population's distribution

It allows us to use normal distributions to evaluate sample questions without regard to the underlying distributions or other factors

---

<mark style="background: #ADCCFFA6;">Distributions</mark>
	Discrete Distributions (PMFs):
		Binomial
		Hypergeometric
		Poisson
	Continuous Distributions (PDFs):
		Normal
		Exponential

| A        | 0   | 1   | 2   | 3   |
| -------- | --- | --- | --- | --- |
| **P(A)** | 1/8 | 3/8 | 3/8 | 1/8 |
A probability mass function (pmf) is a table of discrete random variables and the probability of them having a specific value. For example above, the discrete random variable A has a 1/8th chance of being 3
$$\mu=\sum\limits(x*p(x))$$
$$\sigma^2=\sum\limits((x-\mu)^2*p(x))$$

A binomial distribution is used for discrete random variable distributions with TWO POSSIBLE VALUES that have fixed probabilities that add up to 1. A or B will happen
$$P(k)=C\left(\begin{array}{c} n \\ k\end{array} \right)p^k(1-p)^{n-k}$$
- n is the number of trials
- k is the number of successes desired
- p is the probability of success for each trial
$$\mu=n*p$$
$$\sigma^2=np(1-p)$$

The hypergeometric distribution is for when sampling a population WITHOUT REPLACEMENT
$$P(k)=\frac{C\left(\begin{array}{c}K \\ k \end{array}\right)C\left(\begin{array}{c}(N-K) \\ (n-k) \end{array}\right)}{C\left(\begin{array}{c}N \\ n \end{array}\right)}$$
- K is the success population
- k is the total successes you want
- N is the total sample size
- n is the number of things chosen out of the sample
$$\mu=\frac{nk}{N}$$
$$\sigma^2=\frac{nk(N-k)(N-n)}{N^2(N-1)}$$

A Poisson distribution is for k independent, randomly occurring events happening over a PERIOD or AREA with an average rate
$$P(k)=e^{-\lambda}\frac{\lambda^k}{k!}$$
- k is the number of successes desired
- $\lambda$ is the average frequency of success
- NOTE: THEY HAVE TO BE IN THE SAME TIME UNITS. You can't compare minutes to hours, etc
$$\mu=\lambda$$
$$\sigma^2=\lambda$$

A probability density function (pdf) describes the likelihood of all values for a continuous random variable. Usually represented with an f(x) graph. THE PROBABILITY IS THE AREA UNDER THE CURVE OF THE GRAPH (integral)

A normal distribution (bell-curve, Gaussian distribution) is a pdf with a bell-shaped graph and is symmetric around the mean $\mu$
For unimodal distributions, the mean, median, and mode are equal. It's just the middle value
$$f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^{2}}\to X\sim N(\mu,\sigma^2)$$
Not told how to calculate expected value or variance, should be given it

An exponential probability distribution is basically the continuous version of the Poisson distribution. Except here, lambda represents the inter-arrival times. Instead of saying we have outcomes per x minutes, we say every x minutes we get the outcome (on average)
$$f(x)=\lambda e^{-\lambda x}$$
Note: This is a memoryless model which means the time intervals are independent, non-overlapping events. The success/failure of previous intervals will not impact the rates (think the bus problem from class)
$$\mu=\frac{1}{\lambda}$$
$$\sigma^2=\frac{1}{\lambda^2}$$

---

<mark style="background: #ADCCFFA6;">Cumulative distribution functions</mark>
	Cumulative probabilities over ranges for discrete and continuous distributions (summation and integration)
	How to check for a valid distribution (total probability should sum to 1)
	For reference sheet: list of common integrals on slide 15 of slide deck 1

For normal distributions:
The empirical rule stats that for any unimodal and symmetric distribution, 68% of data is located within one stdev, 95% in two stdevs, and 99.7% in three stdevs. Within 2 stdevs is considered "normal"

To find the value that makes something a valid pdf, find the integral, set it = 1 and solve
$$\mu=\int xf(x)$$
For a pdf to be valid, the total sum of probabilities from a to b must = 1

For a continuous random variable:
$$\mu=\int^{max}_{min}x*f(x)dx$$
$$\sigma^2=\left(\int^{max}_{min}x^2*f(x)dx\right)-\mu^2$$
The max and min is usually 0-1
## Statistical testing
<mark style="background: #ADCCFFA6;">Calculate Z-score and read z-table probabilities</mark>
	Confidence intervals

The z-score is the number of standard deviations a single value is from the population mean. This specific formula can only be used when you have the POPULATION
$$z=\frac{x-\mu}{\sigma}$$

There's usually a positive and negative table
The negative table is the total probability up to a given z-score. Basically the left side of the graph if you split down the middle
The positive table is the total probability down to a given z-score. On the right hand side if you split it down the middle

You use a table to convert a z-score into a probability
![[Pasted image 20241025162446.png]]
If your z-score has two decimal places, just find the intersection. So a z-score of 0.54 is a probability of about 70.54%

If you want the probability that $Z>0.54$ (to the right of the z-score), subtract the cumulative probability from 1:
$P(Z > 0.54) = 1 - P(Z \leq 0.54) = 1 - 0.7054 = 0.2946$
So there is a 29.46% chance that a value is greater than $z=0.54$

A confidence interval is
$$[\overline{x}-m,\overline{x}+m]$$
Where m is the margin of error $m=(multiplier)(standard\ error)$
The multiplier is the number of standard deviations about the mean that would capture c% of the distribution. Read the z* from the relevant table below and put it into the formulas below:

If standard deviation is known:
$$m=z^*\frac{\sigma}{\sqrt n}$$

| Confidence Level | Critical Value |
| ---------------- | -------------- |
| c = 0.90         | z* = 1.645     |
| c = 0.95         | z* = 1.960     |
| c = 0.99         | z* = 2.576     |

If standard deviation is UNKNOWN:
$$m=\left(\frac{t^*s}{m}\right)^2$$

|         | $\alpha=0.1$ | $\alpha=0.05$ | $\alpha=0.01$ |
| ------- | ------------ | ------------- | ------------- |
| $df=5$  | 2.015        | 2.571         | 4.032         |
| $df=10$ | 1.812        | 2.228         | 3.169         |
| $df=15$ | 1.753        | 2.131         | 2.947         |
| $df=24$ | 1.711        | 2.064         | 2.797         |
| $df=32$ | 1.694        | 2.037         | 2.738         |

---

<mark style="background: #ADCCFFA6;">T-test</mark>
	Conduct T-test for paired (pre/post) or unpaired (Student’s only) data by hand
	Read t-table probabilities

If you want to know how different the two groups are: use a two-tailed test with alpha (threshold for significance) of 0.05
	Usually use two-tailed unless you have a reason not to
If you want to know if one group is better than the other: use the one-tailed test with an alpha of 0.025

A paired t-test is when a sample is taken from a population exposed to two different treatments. Same study participants two different tests. We use pre/post testing for this
$$t_{paired}=\frac{\overline{\Delta}}{\sqrt{\frac{var_{\Delta}}{N}}}$$
$$\overline{\Delta}=\frac{\sum\limits^N_1(post_i-pre_i)}{n}$$
$$var_{\Delta}=\frac{\sum\limits^N_1(\Delta_i-\overline{\Delta})^2}{N-1}$$
$$df=N-1$$
- Where $\Delta$ is the change between pre and post
To calculate it by hand:
1. Put everything into a table (will need ~5 columns)
2. Calculate the mean of pre and post groups
3. Calculate the $\Delta$ (post - pre)
4. Find $\overline{\Delta}$
5. Calculate the variance
6. Plug these values into the $t_{paired}$ equation and plug it into a t-table to find the p-value
![[Pasted image 20241217152710.png]]

An unpaired t-test is when the sample test is applied to two different populations. We use Student's t-test for this
$$t=\frac{\overline{x_1}-\overline{x_2}}{\overline{\sigma_s}\sqrt{\frac{1}{N_1}+\frac{1}{N_2}}}$$
- where $\overline{x}$ and $n_1$ are the mean and sample size of the sample drawn from the first sample respectively; and the 2's are the second sample
- $\overline{\sigma_s}$ is the pooled standard deviation
$$df=(N_1-1)+(N_2-1)$$
$$\overline{\sigma_s}=\sqrt{\frac{var_{s1}+var_{s2}}{2}}$$
To calculate it by hand:
1. Put everything into a table (will need ~6 columns)
2. Calculate the mean of each group
3. Calculate the difference from the mean of each row ($x_i-\overline{x}$)
4. Square this difference for each row
5. Sum the squared difference to find the variance
6. Use the $\overline{\sigma_s}$ equation to find the pooled stdev
7. Plug into the main t equation
![[Pasted image 20241217145515.png]]

Take this t-statistic, the df, and if it's one-tailed or two-tailed and plug it into the table
![[Pasted image 20241217145642.png]]
This gives the t-value. You compare this with your t-statistic to determine significance. If it EXCEEDS the t-value it is significant
	In this example, the t-statistic was -2.849 does not exceed 2.878 or -2.878 so it is not significant

---

<mark style="background: #ADCCFFA6;">Non-parametric</mark>
	Intuition
	Wilcoxon Signed Rank and Mann-Whitney U-test (no tie cases) by hand
	Chi-Squared ((observed-expected)^2/expected)

Non-parametric tests are those that are not normally distributed (they fail the Shapiro-Wilk test)

Wilcoxon Signed-Rank test is an alternative to paired t-tests. It applies ranks to the data so we can make minimal assumptions but retain ordinality
$$E(W^+)=E(W^-)=\sum\limits^n_{i=1}i*p$$
$$\text{note:}\sum\limits^{n}_{i=1}i*p\to p\sum\limits^{n}_{i=1}i\to p\frac{n(n+1)}{2}$$
$$\mu_W=\frac{n(n+1)}{4}$$
$$\sigma^2_W=\frac{n(n+1)(2n+1)-\sum\limits^k_{i=1}\frac{t_i^3-t_i}{2}}{24}$$
$$z=\frac{W-\mu_W}{\sigma_W}$$
Where p is the likelihood of a value having a positive/negative rank. In most cases, p = 0.5 because the null hypothesis will expect 50% to be positive and 50% to be negative so the overall difference is 0
To do it by hand:
1. Put in a table
2. Calculate the Delta (pre-post)
3. Order the delta's from least to greatest (absolute value)
4. Rank them 1 through x (use average ranking for tie cases but there shouldn't be any on the test)
5. Sign the ranks based on the direction of change. If the delta is positive, so is the rank, if it's negative, so is the rank
6. Calculate $W^+=\text{sum of positive ranks}$
7. Calculate $W^-=\text{sum of negative ranks}$
8. Calculate $W=min(W^+,W^-)$
9. Plug this W statistic into the above formulas for $\mu_W$, $\sigma^2_W$, and $z$
10. If there are more than 30 samples, determine significance using a table as normal. If not, read the W statistic directly from a table of critical values (reject null hypothesis if the W statistic is less than the critical value)

Mann-Whitney U-test is an alternative to unpaired t-tests. It assigns ranks similarly to Wilcoxon with a very similar basic idea. Is there a difference in the rank sum?
$$U_x=n_1*n_2+\frac{n_x*(n_x+1)}{2}-T_x$$
$$\mu_U=\frac{n_1*n_2}{2}$$
$$\sigma_U^2=\frac{n_1*n_2*(n_1+n_2+1)}{12}$$
$$z=\frac{U-\mu_U}{\sigma_U}$$
To do it by hand:
1. Put it in a table
2. Assign ranks 1 through x based on least to greatest
3. Calculate $T_1$ and $T_2$ which is just the sum of the ranks for the two groups, respectively
4. Calculate $U_1$ and $U_2$ using the above formula, substituting in 1 and 2
5. Calculate $U=min(U_1,U_2)$
6. If there are more than 20-25 samples, use a z-table. Otherwise, read the U-Statistic directly from a table of critical values (reject null hypothesis if the U statistic is less than the critical value)

CHI-squared is a non-parametric test for categorical data. It's like a variance comparison metric that is non-parametric. Basically just
$$\frac{(Observed-Expected)^2}{Expected}$$
$$\chi^2=\sum\limits\frac{(O_i-E_i)^2}{E_i}$$
$$df=(number\ of\ columns-1)*(number\ of\ rows-1)$$
To do it by hand:
1. Set up the expected table if everything was RANDOM
   ![[Pasted image 20241217162702.png]]
2. You should be given the observed data. Calculate observed - expected
3. Square the values in each cell
4. Divide them by the expected value
5. Sum everything
6. It is statistically significant if the test statistic is greater than the critical value found in the table
The higher the p value, the more independent the features are

---

<mark style="background: #ADCCFFA6;">Conceptually what models apply under what conditions (including single-factor ANOVA)</mark>

![[Pasted image 20241217163052.png]]
Note: post-hoc analysis just means you can run additional statistical tests after your initial one. We did x test so then we did y test

Student's vs Welch's:
Student's t-test compares means with pooled variance, Welch does not pool variance
	Welch's test has messy degrees of freedom specifically because of this

Single-factor ANOVA is when there is a single variable being compared across 3 or more groups. Tests for variance between populations
## Data modeling
<mark style="background: #ADCCFFA6;">Covariance and correlation</mark>
<mark style="background: #ADCCFFA6;">Linear regression (simple linear regression only) slope and intercept calculation</mark>

Covariance is how values vary WITH EACH OTHER. Two features rather than just one like regular variance
$$\text{covar}_p(x,y)=\frac{\sum\limits^n_{i=1}(x_i-\overline{x})*(y_i-\overline{y})}{n}$$
$$\text{covar}_s(x,y)=\frac{\sum\limits^n_{i=1}(x_i-\overline{x})*(y_i-\overline{y})}{n-1}$$
Note: covariance is UNIT DEPENDENT. Convert accordingly

You usually arrange these into a covariance matrix. It is a symmetric matrix with the variance down the diagonal
![[Pasted image 20241217163955.png]]

Correlation is just covariance without the units. You compute the correlation coefficients (specifically Pearson's correlation). It's the covariance normalized by the standard deviations
$$\rho_{A,B}=corrA,B=\frac{cov(A,B)}{\sigma_A\sigma_B}$$
Sometimes rho means population and r is for sample
Very easy to find the stdev of each thing, just square root the diagonal
You can also put this into a correlation matrix the same way as above. Note that the diagonal should always be 1
Independent of units

A linear regression is basically just a line through the covariance trends. It makes a best of fit line for this correlation
$$y=mx+b$$
$$m=\frac{\sum\limits^n_{i=1}(x_i-\overline x)*(y_i-\overline y)}{\sum\limits^n_{i=1}(x_i-\overline x)^2}$$
Note that this is just the covariance of x with y divided by the variance of x. Can be quickly calculated if you have the matrix
$$b=\frac{\sum\limits^n_{i=1}y_i-(m*x_i)}{n}$$

You can calculated R^2 or the goodness of fit of the line by squaring the correlation between the two variables
The Adjusted R-Squared accounts for the number of data points, which regular does not
$$AdjR^2=1-\frac{(1-R^2)(n-1)}{n-k-1}$$
- n = number of data points
- k = number of variables we are considering besides the constant