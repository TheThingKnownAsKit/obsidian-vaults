## 6.2 Resampling: Randomization and bootstrapping
<mark style="background: #ADCCFFA6;">Resampling</mark> is a nonparametric technique for determining statistical significance by comparing an outcome with a set of outcomes obtained by randomly assigning the data points among groups
A <mark style="background: #ADCCFFA6;">randomization test</mark> (<mark style="background: #ADCCFFA6;">permutation test</mark>) is a particular resampling technique that permutes the data points to obtain the comparison set of random outcomes, selecting each data point only once. A randomization test is classified as random resampling without replacement, because the data point can no longer be drawn from the population

![[Pasted image 20241115133534.png]]
![[Pasted image 20241115133612.png]]

<mark style="background: #ADCCFFA6;">Bootstrapping</mark> is a resampling technique that randomly selects a set of data points, allowing the same data point to potentially be selected more than once, to create an approximate sampling distribution

![[Pasted image 20241115152824.png]]

![[Pasted image 20241115153021.png]]

## 6.3 Wilcoxon rank-sum test
Given a set of data points, <mark style="background: #ADCCFFA6;">ranking</mark> orders the data such that for any two data points, one is either greater than, less than, or equal to the other

![[Pasted image 20241115154504.png]]

The <mark style="background: #ADCCFFA6;">Wilcoxon rank-sum test</mark> can be performed using ranked data. This method ignores the values of the original data and compares the sum of the two groups' ranks . The test statistic for the Wilcoxon rank-sum test, W, is the minimum of the sum of the ranks for each group
$$\mu_W=\frac{n_1n_2}{2}$$
![[Pasted image 20241115154637.png]]
![[Pasted image 20241115154650.png]]

```Python
import numpy as np
from scipy import stats

x = np.array([9.84,9.40,8.20, 8.24, 9.20,8.55,8.52,8.12])
y = np.array([8.27,8.20,8.25,8.14,9.00,8.10,7.20,8.32,7.70])

W, p = stats.mannwhitneyu(x, y, alternative = 'two-sided')
print("W = ", W)
print("p-value = ", p)
```

## 7.1 Categorical data
<mark style="background: #ADCCFFA6;">Categorical data</mark> is data that can only take on the value (usually a label) of one of several categories
Two types of categorical variables are often distinguished:
- A <mark style="background: #ADCCFFA6;">nominal</mark> variable's categories have no ordering, existing in name only, like apples, oranges, and grapes. ("Nominal" means "in name only").
- An <mark style="background: #ADCCFFA6;">ordinal</mark> variable's categories have an ordering, like disagree, neutral, and agree.

A <mark style="background: #ADCCFFA6;">contingency</mark> table displays the number of observations in each category.
![[Pasted image 20241115154936.png]]

## 7.2 Fisher's exact test
<mark style="background: #ADCCFFA6;"> Fisher's exact test</mark> is a method of calculating the exact p-value for contingency tables. This hypothesis test is often used with 2×2 contingency tables where each of the two variables studied has exactly two categories

![[Pasted image 20241115155516.png]]![[Pasted image 20241115155614.png]]

One-sided
```Python
from scipy import stats
from scipy.stats import fisher_exact
import numpy as np

orangejuice = np.array([[7,4],[3,6]])
print(orangejuice)

oddsratio, pvalue = fisher_exact(orangejuice, alternative='greater')

print(pvalue)
print(oddsratio)
```
Two-sided
```Python
from scipy import stats
from scipy.stats import fisher_exact
import numpy as np

orangejuice = np.array([[7,4],[3,6]])

oddsratio, pvalue = fisher_exact(orangejuice)

print(pvalue)
print(oddsratio)
```

## 7.3 Introduction to chi-square tests
![[Pasted image 20241115155851.png]]

![[Pasted image 20241115155948.png]]

```Python
from scipy import stats
from scipy.stats import chi2_contingency
import numpy as np

gilbert = np.array([[40,217],[34,1350]])
print(gilbert)

chi, pvalue, dof, ex = chi2_contingency(gilbert, correction=False)

print(chi)
print(pvalue)
print(dof)
```

## 7.4 Chi-square test for homogeneity and independence
![[Pasted image 20241115160154.png]]

```Python
from scipy import stats
from scipy.stats import chi2_contingency
import numpy as np

parole = np.array([[405,1422],[240, 470], [151, 275]])
print(parole)

chi, pvalue, dof, ex = chi2_contingency(parole)

print(chi)
print(pvalue)
print(dof)
```

![[Pasted image 20241115160245.png]]
![[Pasted image 20241115160256.png]]
