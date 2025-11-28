#ai 

# Intuition 

$$h_\theta(X)=[\theta_0,\theta_1,\theta_2,\dots,\theta_n]\begin{bmatrix}
1\\x_1\\x_2\\\dots\\x_n
\end{bmatrix}$$
    hypothesis,           coefficients,     features

Smaller coefficient = less impact of corresponding feature
- decrease in coefficients represents decrease in model flexibility 
- stop coefficients from rising high to reduce overfitting 

**Regularisation**: introducing small amount of bias to build model that doesn't fit training data as well but can drop the variance 

![[Screenshot 2025-11-10 at 16.45.59.png]]


# Ridge Regression 

Cost function: $$J(\theta)=\frac{1}{2m}\sum\limits^m_{i=1}(h_\theta(X^{(i)})-y^{(i)})^2$$
- objective of model training is to find $\theta$ that minimises $J$

**Regularised** cost function: $$J(\theta)=\frac{1}{2m}\Bigg[\sum\limits^m_{i=1}(h_\theta(X^{(i)})-y^{(i)})^2+\lambda\sum\limits^n_{j=1}\theta_j^2\Bigg]$$
- $\Sigma$ adds a **shrinkage penalty** to $\theta$, while $\lambda$ determines severity
- as $\lambda\rightarrow 0$, RCF becomes similar to usual 
- as $\lambda\rightarrow\infty$, risk of underfitting 
- do not penalise $\theta_0$

![[Screenshot 2025-11-10 at 16.50.25.png]]

Gradient Descent:![[Screenshot 2025-11-10 at 16.50.44.png]]
The regularisation term should only be added to cost function during training 
- evaluate model using un-regularised performance measure 

**Normal Equation**: $$\text{To }\min J(\theta):\text{ set }\theta=(X^TX+\lambda\begin{bmatrix}
0 & & & \\ & 1 & & \\ & & \ddots & \\ & & & 1
\end{bmatrix})^{-1}X^Ty, (\lambda>0)$$
If $n>m$ ($n$: number of features, $m$: number of examples):
- $X^TX$ not invertible, so cannot calculate $\theta=(X^TX)^{-1}X^Ty$
- Having regularisation term removes this problem

# LASSO Regression 

Least Absolute Shrinkage and Selection Operator 

$$J(\theta)=\frac{1}{2m}\Bigg[\sum\limits^m_{i=1}(h_\theta(X^{(i)})-y^{(i)})^2+\lambda\sum\limits^n_{j=1}|\theta_j|\Bigg]$$
$\lambda$ regularises model and penalises larger model parameter $\theta$s, which helps reduce model variance and the risk of overfitting.
- as $\lambda\rightarrow 0$, solution approaches linear regression
- as $\lambda\rightarrow\infty$, solution approaches global mean 
