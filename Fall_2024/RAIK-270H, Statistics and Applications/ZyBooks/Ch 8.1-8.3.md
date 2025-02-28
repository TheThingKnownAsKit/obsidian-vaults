## 8.1 Introduction to simple linear regression (SLR)
A <mark style="background: #ADCCFFA6;">simple linear regression</mark> is a way to model the linear relationship between two quantitative variables, using a line drawn through those variables' data points, known as a <mark style="background: #ADCCFFA6;">regression line</mark>

In a linear regression involving two variables, the <mark style="background: #ADCCFFA6;">response variable</mark> is the variable being modeled or predicted, while the <mark style="background: #ADCCFFA6;">predictor variable</mark> is the variable used to predict the response.
	In a linear regression, the response variable is sometimes called the dependent variable or output or outcome. Also, in a linear regression, a predictor variable is sometimes called an independent variable or input or covariate

The <mark style="background: #ADCCFFA6;">population simple linear regression function</mark> is
$$E(Y)=\beta_0+\beta_1X$$ where $\beta_0$ and $\beta_1$ are regression parameters

E is the <mark style="background: #ADCCFFA6;">expected value</mark>
- _above_ the line: Y>E⁡(Y)
- _below_ the line: Y<E⁡(Y), or
- _on_ the line: Y=E⁡(Y)

The <mark style="background: #ADCCFFA6;">simple linear regression model</mark> is
$$Y=\beta_0+\beta_1X+\epsilon$$
where $\epsilon$ is the regression error term

A <mark style="background: #ADCCFFA6;">regression error</mark>,
$$\epsilon=Y-E(Y)$$
 is a statistical error modeled as a random variable with a normal distribution that has zero mean and constant variance. The regression error is:
- positive for points that lie above the regression line,
- negative for points that lie below the regression line, and
- zero for points that lie on the regression line.

![[Pasted image 20241124143535.png]]

The <mark style="background: #ADCCFFA6;">method of least squares</mark> derives a linear regression model by minimizing the sum of squared errors. For a sample with n observations, the sum of squared errors is
$$\sum\limits^n_{i=1}(Y_i-\beta_0-\beta_1X_i)^2$$

The <mark style="background: #ADCCFFA6;">sample simple linear regression function</mark> is
$$\hat{Y}=b_0+b_1X$$
Where $\hat{Y}$ are the predicted or fitted response values based on the simple linear regression model, and the regression parameter estimators, b0 and b1 are the values of the regression parameters, β0 and β1 that minimize the sum of squared errors.
	Hat denotes sample

A <mark style="background: #ADCCFFA6;">simple linear regression fitted value</mark>,
$$\hat{Y}_i=b_0+b_1X_i$$
is the predicted value of Y for the ith sample value of X based on the sample simple linear regression line.

A <mark style="background: #ADCCFFA6;">simple linear regression residual</mark>,
$$\epsilon_i=Y_i-\hat{Y}_i$$
is the ith estimated regression error based on the sample simple linear regression line.

```Python
import numpy as np
import scipy.stats as st

x = np.array([0, 3, 7, 10])
y = np.array([5, 5, 27, 31])

model = st.linregress(x,y)

print(model)

print("Predicted value for X=3:",np.dot([3, 1],[model[0], model[1]]))
```

## 8.2 SLR assumptions
The simple linear regression model assumes that at each value of the predictor, X, the probability distribution of the regression error, $\epsilon=Y-E(Y)=Y-\beta_0-\beta_1X$:
- has a mean of zero
- has equal variance
- is normal
In addition, the value of ε for one observation is assumed to be independent of the value of ε for any other observation.
![[Pasted image 20241124144733.png]]

![[Pasted image 20241124144809.png]]
![[Pasted image 20241124144939.png]]

![[Pasted image 20241124144958.png]]

![[Pasted image 20241124145012.png]]

![[Pasted image 20241124145029.png]]

## 8.3 Correlation and coefficient of determination
<mark style="background: #ADCCFFA6;">Correlation</mark> describes the association or dependence between two variables. A <mark style="background: #ADCCFFA6;">positive correlation</mark> between two variables means that as one variable increases, the other variable increases as well. A <mark style="background: #ADCCFFA6;">negative correlation</mark> between two variables means that as one variable increases, the other variable decreases

![[Pasted image 20241124145759.png]]

![[Pasted image 20241124145835.png]]

A <mark style="background: #ADCCFFA6;">correlation matrix</mark> is a table that shows the correlation coefficients between each pair of variables

```Python
import pandas as pd
scores = pd.read_csv("ExamScores.csv")
print(scores[['Exam1','Exam2']].corr())
print(scores[['Exam1','Exam2','Exam3','Exam4']].corr())
```
![[Pasted image 20241124145928.png]]

![[Pasted image 20241124150021.png]]
![[Pasted image 20241124150037.png]]

The <mark style="background: #ADCCFFA6;">coefficient of determination</mark>, denoted by $R^2$, gives the ratio of the variance in the response variable explained by the predictor variable. Conceptually, the coefficient of determination is a measure of how closely the regression line follows the pattern of the data. The farther the actual data points are from the regression line, the less useful the line actually is in predicting the value of the response variable
$$R^2=\frac{\sum\limits(\hat{Y}_i-\overline{Y})^2}{\sum\limits(Y_i-\overline{Y})^2}$$
Where $\hat{Y}_i$ is the estimated value of $Y_i$ and $\overline{Y}$ is the mean. It will be between 0 and 1

You can also use the statsmodels excel pack or 
```Python
# The necessary packages are imported
import pandas as pd
import scipy.stats as stats
import statsmodels.api as sm
from statsmodels.formula.api import ols

# The ExamScores dataset is loaded
scores = pd.read_csv('ExamScores.csv')

# Creates a linear regression model
results = ols('Exam4 ~ Exam1', data=scores).fit()

# Creates an analysis of variance table
aov_table = sm.stats.anova_lm(results, typ=2)

# Prints the analysis of variance table and results
print(aov_table)
print(results.summary())
```