 #ai 

# Polynomial Linear Regression 

>[!info] Polynomial Linear Regression 
>A linear regression model with higher order. 
$$h(x)=\theta_0+\theta_1x+\theta_2x^2+\dots+\theta_nx^k$$

### Polynomial to Multivariate

$$h(x)=\theta_0+\theta_1x+\theta_2x^2+\theta_3x^3$$
$$h(X)=\theta_0+\theta_1x_1+\theta_2x_2+\theta_3x_3$$

### Different Orders 

![[Screenshot 2025-11-05 at 13.43.47.png]]

Deciding on order uses **Bayesian Information Criterion**:
$$BIC_k=m\cdot \ln(SS_\epsilon)+k\cdot\ln(m)$$
- $k$: order of polynomial regression model 
- $m$: number of examples in training set 
- $\ln$: natural log 
- $SS_\epsilon$: sum of the squares of the errors
- run series of model orders to fit training data, to get different BIC values for models.

# Underfitting vs Overfitting 

Underfitting:
![[Screenshot 2025-11-05 at 13.52.28.png]]
- algorithm can't capture underlying trend of data 
- polynomial order too small
- $J(\theta)=\frac{1}{2m}\sum\limits^m_{i=1}(h_\theta(X^{(i)})-y^{(i)})^2>>0$ 

Good solution:
![[Screenshot 2025-11-05 at 13.52.49.png]]

Overfitting:
![[Screenshot 2025-11-05 at 13.53.03.png]]
- algorithm captures too much noise from data 
- polynomial order too high 
- $J(\theta)=\frac{1}{2m}\sum\limits^m_{i=1}(h_\theta(X^{(i)})-y^{(i)})^2\approx0$  

### Tackling Overfitting 

![[Screenshot 2025-11-05 at 14.15.18.png]]
- $x_1$: annual income
- $x_2$: age 
- $x_3$: number of children 
- $x_4$: cups of tea per week 
- up to $x_{50}$ is too many features, unable to plot them in graph 

Methods:
- **Include more data**: collect more data, data augmentation 
- **Cross-validation**: k-fold cross validation, leave-one-out cross validation 
- **Feature selection/reduction**: manually, feature selection algorithms 
- **Regularisation**: keep all the features, regularise parameters 

### Tackling Underfitting 

Methods:
- **Include more features**: increase complexity, relevant and decisive features 
- **Increase model complexity**: higher order polynomial, linear to non-linear 
- **Reduce regularisation**: reduce penalty, reduce regularisation values 
- **Increase training time**: keep all the features, regularise parameters 

# Bias vs Variance 

![[Screenshot 2025-11-05 at 14.27.07.png]]

