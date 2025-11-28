#ai 

Smaller values of cost function = better model fit
- goal of ML is to create hypothesis function to minimise $J$
- cost function to compare **predicted values** and **actual values** using specific measure of goodness of fit 

# Mean Squared Error Cost Function 

Most commonly used: $$J=\frac{1}{2m}\sum\limits^m_{i=1}(y^{(i)}-\hat{y}^{(i)})^2$$
- $y$ is actual, $\hat{y}$ is predicted 
- $\frac{1}{2m}$ is normalising factor, $(y^{(i)}-\hat{y}^{(i)})$ is error 
- squared means outlier dominates cost function

![[Screenshot 2025-11-07 at 10.59.25.png]]

# Mean Absolute Error Cost Function

$$J=\frac{1}{m}\sum\limits^m_{i=1}|y^{(i)}-\hat{y}^{(i)}|$$
- $\frac{1}{m}$ is normalising factor 
- $|y^{(i)}-\hat{y}^{(i)}|$ is absolute value 
- more robust for outliers 
- some computational challenges as not differentiable when predicted = actual 
- gradient doesn't change with fixed learning rate 
- MSE: outliers are anomalies, MAE: outliers are corrupted data 
- MSE skewed towards outliers, MAE has unrealistic high accuracy 
![[Screenshot 2025-11-07 at 10.59.38.png]]


# Huber-M Cost Function 

![[Screenshot 2025-11-07 at 10.59.04.png]]

![[Screenshot 2025-11-07 at 10.59.59.png]]
- choice of $\delta$ very important, as determines what are considered as outliers 
- errors smaller than $\delta$ minimised with MSE
- errors larger than $\delta$ minimised with MAE

# Log-Cosh Cost Function 

$$J=\frac{1}{m}\sum\limits^m_{i=1}\log(\cosh(y^{(i)}-\hat{y}^{(i)}))$$
$$f(x)=\log(\cosh(x))=\log\cosh(x)=\ln\frac{e^x+e^{-x}}{2}$$
- if $x$ very large, $x>0$, $=\ln\frac{e^x+e^{-x}}{2}=\ln\frac{e^x}{2}=\ln(e^x)-\ln2=x-\ln2$
- for $x<0$, $=\ln\frac{e^x+e^{-x}}{2}=\ln\frac{e^{-x}}{2}=\ln(e^{-x})-\ln2=-x-\ln2$ 
$$\log(\cosh(x))=|x|-\ln2$$
- if $x$ is very small, $\log(\cosh(x))=\frac{x^2}{2}$ 
![[Screenshot 2025-11-07 at 11.07.10.png]]
- twice differentiable everywhere 

# Prediction Interval 

Alternative to Point Prediction 
- predicts interval in which future data point will fall (certain probability)
- different from confidence interval 
	- confidence interval: quantifies uncertainty on predicted pop variable (mean, s.d. etc)
	- prediction interval: quantifies uncertainty on single data point predicted from population 
- can be used as measure of likeliness of correctness
- determines interval of possible values ![[Screenshot 2025-11-07 at 11.10.10.png]]
# Quantile Cost Function 

$$J=\frac{1}{m}(\sum\limits_{y^{(i)}<\hat{y}^{(i)}}(\gamma-1)|y^{(i)}-\hat{y}^{(i)}|+\sum\limits_{y^{(i)}>\hat{y}^{(i)}}\gamma|y^{(i)}-\hat{y}^{(i)}|), \space\space \gamma\in(0,1)$$
- like MAE but with extra hyperparameter $\gamma$, which specifies the $\gamma$-th quantile of dependent variable 
- differs depending upon evaluated quantile:
	- more negative errors penalised when higher quantile specified 
	- more positive errors penalised when lower quantile specified
![[Screenshot 2025-11-07 at 11.16.09.png]]
- penalise equally on under-predictions and over-predictions (green line)
- fit the model using both cost functions 
![[Screenshot 2025-11-07 at 11.16.56.png]]
- quantile regression for 5th and 95th quantiles tries to find bounds $y_0(x)$ and $y_1(x)$ such that:$$\mathbb{P}(Y\leq y_0(X))=0.05, \mathbb{P}(Y\leq y_1(X))=0.95$$$$\mathbb{P}(y_0(X)\leq Y\leq y_1(X))=0.90$$
