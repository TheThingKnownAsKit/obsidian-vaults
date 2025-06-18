![[18 Ensemble Methods.pdf]]

# Bootstrapping
<mark style="background: #ADCCFFA6;">Bootstrapping</mark> is another technique related to cross validation, but instead of generalization, it's focused on estimating statistical descriptors of your model
- Create n subsamples of data with replacement
- Train n models
- Build a probability distribution from the performance of each model
- Define variance and confidence intervals of the model
![[Pasted image 20250422130916.png]]

# Bagging
In <mark style="background: #ADCCFFA6;">bagging</mark>, you sample smaller data subsets and in cross validation it's used to test generalizability of the model (and other things). It is useful for bootstrapping as it helps us estimate statistical parameters
- Create the bootstrapped subsets
- Train n models on those subsets and combine them
It combines multiple weak learners in parallel to make a stronger learner. Select them with majority vote (classifiers) or averaging (regression)

Random forests are one of the best traditional methods we have
https://www.analyticsvidhya.com/blog/2021/06/understanding-random-forest/

# Bias-Variance Tradeoff
![[Pasted image 20250422131805.png]]

![[Pasted image 20250422131950.png]]

# Boosting
Bagging is useful for weak learners operating in PARALLEL
<mark style="background: #ADCCFFA6;">Boosting</mark> is a sequential technique. The selection of the data is one of the steps of the process and it focuses on reducing bias to any one class or another by better coverage of all data
- Let's train the first model and see how it goes
- Then train another model on the data it got wrong
- Repeat

Good base models for boosting have low variance and high bias

![[Pasted image 20250422132408.png]]

# How to decide the parameters for model and data weights?
Optimization. One common method is to build the ensemble one model at a time, adaptively adding new weak leaners when necessary (sometimes called adaptive boosting or adaboost)

You ca also update the weight parameters with gradient descent like Extreme Gradient Boosting (XGBoost)

# Stacking
Bagging and boosting both used multiple weak learners of the same type

<mark style="background: #ADCCFFA6;">Stacking</mark> is a sequential ensemble method that uses another machine learning model at the end. Supports heterogeneous weak learners and can be arranged in multiple layers

![[Pasted image 20250422132926.png]]
