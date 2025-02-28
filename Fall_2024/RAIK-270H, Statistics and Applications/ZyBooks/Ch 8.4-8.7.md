## 8.4 Interpreting SLR models
![[Pasted image 20241126113121.png]]

![[Pasted image 20241126113222.png]]

Basically the estimated linear regression equation is $\hat{Y}=b_0+b_1X$ where b0 is the y-intercept, b1 is the slope

## 8.5 Confidence and prediction intervals for SLR models
![[Pasted image 20241126115201.png]]

![[Pasted image 20241126115215.png]]
Number of drinks as the x-axis (didn't fit on screen)

```Python
import statsmodels.formula.api as smf
import pandas as pd 
import numpy as np

df = pd.read_csv('Reaction.csv')
model = smf.ols('Reaction ~ Drinks', data = df).fit()

# Regression parameter estimators b0 and b1:
print('Parameter estimates:\n', model.params)

# Residual standard error:
print('\nResidual standard error:\n', np.sqrt(model.scale))

# Predicting Y (Reaction) when X (Drinks) is 4:
x0 = pd.DataFrame(dict(Drinks=[4]))
print('\nPrediction:\n', model.predict(x0))

# Alternative code to predict Y when X = 4:
#model.predict(exog=x0)

intervals = model.get_prediction(x0)
print('\nIntervals:\n', intervals.summary_frame())
```

## 8.6 Testing SLR parameters
![[Pasted image 20241126115340.png]]

```Python
import pandas as pd
import statsmodels.formula.api as smf
scores = pd.read_csv('ExamScores.csv')

model = smf.ols('Exam4 ~ Exam2', scores).fit()
print(model.summary())
```

![[Pasted image 20241126115431.png]]

![[Pasted image 20241126115456.png]]

![[Pasted image 20241126115529.png]]

```Python
from statsmodels.formula.api import ols
import statsmodels.api as sm
import pandas as pd
df=pd.read_csv("ExamScores.csv")

mod = ols('Exam4 ~ Exam1',df).fit()
print(sm.stats.anova_lm(mod, typ=2))
```

![[Pasted image 20241126115617.png]]

## 8.7 Linear regression example
```Python
import statsmodels.formula.api as sms
import pandas as pd
import matplotlib.pyplot as plt
import warnings
warnings.simplefilter('ignore') 


Y = [90, 66, 78, 65, 65, 60, 63, 72, 54, 81, 58, 71, 70, 92]
X1 = [82, 66, 72, 59, 86, 50, 60, 91, 46, 80, 68, 58, 88, 82]
math = ["yes", "no", "yes", "yes", "no", "yes", "no", "no", "no", "yes", "no", "yes", "no", "yes"]

df1 = pd.DataFrame(Y, columns = ["Y"])
df2 = pd.DataFrame(X1, columns = ["X1"])

M = pd.concat([df1, df2], axis=1)

model1 = sms.ols('Y ~ X1', data = M).fit()

print(model1.summary())
```

Output of that code:
```
                            OLS Regression Results                            
==============================================================================
Dep. Variable:                      Y   R-squared:                       0.376
Model:                            OLS   Adj. R-squared:                  0.324
Method:                 Least Squares   F-statistic:                     7.242
Date:                Tue, 26 Nov 2024   Prob (F-statistic):             0.0196
Time:                        17:56:59   Log-Likelihood:                -50.102
No. Observations:                  14   AIC:                             104.2
Df Residuals:                      12   BIC:                             105.5
Df Model:                           1                                         
Covariance Type:            nonrobust                                         
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
Intercept     36.5640     12.804      2.856      0.014       8.666      64.462
X1             0.4789      0.178      2.691      0.020       0.091       0.867
==============================================================================
Omnibus:                        0.805   Durbin-Watson:                   2.230
Prob(Omnibus):                  0.669   Jarque-Bera (JB):                0.746
Skew:                           0.348   Prob(JB):                        0.689
Kurtosis:                       2.109   Cond. No.                         368.
==============================================================================

Notes:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
```

```Python
import statsmodels.formula.api as sms
import pandas as pd
import matplotlib.pyplot as plt
import warnings
warnings.simplefilter('ignore') 

Y = [90, 66, 78, 65, 65, 60, 63, 72, 54, 81, 58, 71, 70, 92]
X1 = [82, 66, 72, 59, 86, 50, 60, 91, 46, 80, 68, 58, 88, 82]
math = ["yes", "no", "yes", "yes", "no", "yes", "no", "no", "no", "yes", "no", "yes", "no", "yes"]

df1 = pd.DataFrame(Y, columns = ["Y"])
df2 = pd.DataFrame(X1, columns = ["X1"])
df3 = pd.DataFrame(math, columns = ["X2"])

M = pd.concat([df1, df2, df3], axis=1)

model2 = sms.ols('Y ~ X1 + X2 + X1*X2', data = M).fit()
print(model2.summary())
```
```
                            OLS Regression Results                            
==============================================================================
Dep. Variable:                      Y   R-squared:                       0.918
Model:                            OLS   Adj. R-squared:                  0.893
Method:                 Least Squares   F-statistic:                     37.30
Date:                Tue, 26 Nov 2024   Prob (F-statistic):           9.70e-06
Time:                        17:57:54   Log-Likelihood:                -35.903
No. Observations:                  14   AIC:                             79.81
Df Residuals:                      10   BIC:                             82.36
Df Model:                           3                                         
Covariance Type:            nonrobust                                         
================================================================================
                   coef    std err          t      P>|t|      [0.025      0.975]
--------------------------------------------------------------------------------
Intercept       40.6212      6.688      6.074      0.000      25.720      55.523
X2[T.yes]      -24.3640     10.462     -2.329      0.042     -47.675      -1.053
X1               0.3241      0.091      3.576      0.005       0.122       0.526
X1:X2[T.yes]     0.5521      0.146      3.775      0.004       0.226       0.878
==============================================================================
Omnibus:                        2.444   Durbin-Watson:                   1.276
Prob(Omnibus):                  0.295   Jarque-Bera (JB):                1.103
Skew:                          -0.244   Prob(JB):                        0.576
Kurtosis:                       1.715   Cond. No.                         942.
==============================================================================

Notes:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
```