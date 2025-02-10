## Hypothesis Test for a Population Mean
The <mark style="background: #ADCCFFA6;">z-test</mark> is for a hypothesis in which the z-statistic follows a normal distribution. The z-test for a population mean can be used to determine whether the population mean is the same as the hypothesized mean $\mu_0$, assuming that the POPULATION (not sample) standard deviation $\sigma$ is known
$$\left( \frac{\overline{x}-\mu_0}{\frac{\sigma}{\sqrt{n}}}\right)$$
Is assumed to be N(0, 1)

![[Pasted image 20241108104923.png]]
![[Pasted image 20241108104937.png]]
[p-value with z-score](https://www.socscistatistics.com/pvalues/normaldistribution.aspx)

```Python
from statsmodels.stats.weightstats import ztest
import pandas as pd
scores = pd.read_csv('ExamScores.csv')
print(ztest(x1 = scores['Exam1'],  value = 86))
```

Because the population standard deviation is rarely known, Student's T-Test is used to compare the observed sample mean to a hypothesized mean

![[Pasted image 20241108110616.png]]
![[Pasted image 20241108110733.png]]
[p-value with t-test](https://www.socscistatistics.com/pvalues/tdistribution.aspx)

```Python
import pandas as pd
import scipy.stats as st
scores = pd.read_csv('ExamScores.csv')
print(st.ttest_1samp(scores['Exam1'], 82))
```

## Hypothesis test for the difference between two population means
![[Pasted image 20241108114816.png]]

![[Pasted image 20241108114836.png]]
Procedure for testing for two population means

```Python
from statsmodels.stats.weightstats import ztest
sample1 = [21, 28, 40, 55, 58, 60]
sample2 = [13, 29, 50, 55, 71, 90]
print(ztest(x1 = sample1, x2 = sample2))
```

The <mark style="background: #ADCCFFA6;">two-sample t-test</mark> is used to determine if a statistically significant difference exists between two population means. Two types of two-sample t-tests exist: paired and unpaired
- In a <mark style="background: #ADCCFFA6;">paired t-test</mark> or dependent t-test, a sample taken from one population is exposed to two different treatments. Same study participants two different tests
$$t=\frac{\overline{d}-\mu_d}{\frac{s_d}{\sqrt{n}}}$$
where $s_d$ is the sample standard deviation of the differences, $\overline{d}$ is the mean difference between the samples, and n is the sample size
Most common hypothesis mean difference is 0
![[Pasted image 20241108115452.png]]
```Python
import scipy.stats as st
import pandas as pd
df = pd.read_csv('ExamScores.csv')
print(st.ttest_rel(df['Exam1'],df['Exam2']))
```

- In an <mark style="background: #ADCCFFA6;">unpaired t-test</mark> or independent t-test, a sample taken from one population is not related to a different sample taken from another population. Different study participants
$$t=\frac{\overline{x_1}-\overline{x_2}-(\mu_1-\mu_2)}{\sqrt{\frac{(s_1)^2}{n_1}+\frac{(s_2)^2}{n_2}}}$$
where $\overline{x}$, $s_1$, and $n_1$ are the mean, standard deviation, and sample size of the sample drawn from the first population respectively; and the 2's are the second population
Degrees of freedom are $df=n_1+n_2-2$
The most common accepted difference between two means is 0 (mu - mu)
![[Pasted image 20241108120101.png]]
```Python
import scipy.stats as st
import pandas as pd
df = pd.read_csv('Machine.csv')

# Two-tailed test
print(st.ttest_ind(df['Old'],df['New'],equal_var=False, alternative="two-sided"))

# One-tailed test
print(st.ttest_ind(df['Old'],df['New'],equal_var=False, alternative="greater"))
```

## One-way analysis of variance (one-way ANOVA)
<mark style="background: #ADCCFFA6;">One-way analysis of variance (one-way ANOVA)</mark> determines whether a statistically significant difference exists among the means of three or more populations. Equivalently, ANOVA tests for an association between a categorical predictor variable and a response variable (often referred to as a level)

![[Pasted image 20241108125003.png]]
![[Pasted image 20241108125014.png]]

If the null hypothesis is not rejected, then no further work is necessary. However, if the null hypothesis is rejected, further analysis is required because the F-test does not determine which groups have different means. <mark style="background: #ADCCFFA6;">Post-hoc analysis</mark> determines which groups have different means, which group has the highest or lowest mean, and other relationships between the groups

The <mark style="background: #ADCCFFA6;">Tukey Honestly Significant Difference (HSD)</mark> procedure gives the 95% confidence intervals for the mean difference between pairwise groups and determines which mean difference is statistically significant.
	If 0 falls in the confidence interval, then the difference between the means is not statistically significant. In other words, the null hypothesis that the means of the two groups are the same should not be rejected
```Python
import pandas as pd
from statsmodels.stats.multicomp import (pairwise_tukeyhsd,MultiComparison)
df = pd.read_csv('ExamScoresGrouped.csv')
mod = MultiComparison(df['Scores'], df['Exam'])
print(mod.tukeyhsd())
```

## Parametric vs. nonparametric statistics
A <mark style="background: #ADCCFFA6;">parametric method</mark> makes inferences based on data assuming some statistical distribution of a population or for a statistic
	The t-test is an example of a parametric method and assumes normality in the population among other assumptions

A <mark style="background: #ADCCFFA6;">non-parametric method</mark> makes inferences based on data requiring fewer assumptions about the statistical distribution of the population

Non-parametric methods are useful when data is skewed. <mark style="background: #ADCCFFA6;">Skew</mark> is a measure of asymmetry about the mean. A distribution that is only slightly skewed may still be analyzed with a parametric method
	Too much skewness is generally around 2
$$\text{skewness}=\frac{3(\overline{x}-\tilde{x})}{S}$$
where $\overline{x}$ is the mean, $\tilde{x}$ is the median, and S is the standard deviation of the sample.

The <mark style="background: #ADCCFFA6;">standard error of skewness (SES)</mark> is the measure of the deviations that exist between random subsamples selected from the data set, given by
$$SES=\sqrt{\frac{6n(n-1)}{(n-2)(n+1)(n+3)}}$$
where n is the number of data points in the sample

![[Pasted image 20241108130142.png]]
