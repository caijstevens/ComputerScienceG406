#ai 

# Intuition 

Example: Annual Income Predicting Happiness
- Independent variable: annual income
- Dependent variable: happiness
- Supervised learning task: we know "right answer"
- **Regression task**: want to predict real-valued output in a continuous scale

# Linear Regression 

**Task**: to train linear regression model on the training set and evaluate the trained model on the test set.

Mathematically:
- $m$: the number of training instances
- $x$: input/independent variable/feature 
- $y$: output/dependent variable/target
- $(x,y)$: a single training instance
- $(x^{(i)},y^{(i)})$: the $i^{th}$ training instance 

Hypothesis function $h$ maps from $x$ to $y$:

$$h_\theta(x)=\theta_0+\theta_1x$$
- $\theta_0$ is $y$-intercept (bias)
- $\theta_1$ is slope (weight, regression coefficient)

$\hat{y}=h(x)$: predicted value for specific $x$

# Cost Function 

**Cost** measures how bad model performs on whole training set
- **Loss** (error) measures how bad model performs on single training example 
	- difference between prediction and actual for given $x$
	- either 0 or positive 
- we want a straight line so that all have small/zero loss

Squared Error Cost:
$$\sum\limits^m_{i=1}(predicted^{(i)}-actual^{(i)})^2$$

Normalising factor brings back to individual instance level
- even having different dataset with different size, can judge which hypothesis function performs best
$$\frac{1}{m}\sum\limits^m_{i=1}(predicted^{(i)}-actual^{(i)})^2=\frac{1}{m}\sum\limits^m_{i=1}(h(x)^{(i)}-y^{(i)})^2$$
- can halve each side for mathematical convenience

$$=\frac{1}{2m}\sum\limits^m_{i=1}(\theta_0+\theta_1x^{(i)}-y^{(i)})^2$$
- uses hypothesis equation from earlier 
- $x^{(i)}$ and $y^{(i)}$ are constants

**Mean Squared Error Cost Function**:
$$MSE(\theta_0,\theta_1)=\frac{1}{2m}\sum\limits^m_{i=1}(\theta_0+\theta_1x^{(i)}-y^{(i)})^2$$
**Goal**: to solve minimisation problem
$$argmin_{\theta_0,\theta_1}=J(\theta_0,\theta_1)=\frac{1}{2m}\sum\limits^m_{i=1}(\theta_0+\theta_1x^{(i)}-y^{(i)})^2$$
- want to find theta variables such that $J(\theta_0,\theta_1)$ is closest to zero 

# Gradient Descent 

Try different pairs of theta variables in iterations to reduce the cost 
- **Gradient Descent** helps us on how to change theta variable values and when to stop 
- Hyperparameter: learning rate (size of step)

Problems are either:
- steps too small: too many iterations to converge 
- steps too large: never converge, overshoot

Pitfalls:
- learning algorithm may end up with local minima not global minima 
- learning algorithm may stop before reaching minima 
- MSE cost function for LR model always convex, shaped like giant bowl with one global minimum.
- if start on bowl and take steps in reasonable size while following gradient, guaranteed to approach to global minimum.

If training set features have very different scales, meaning parameters and CF variables have very different sizes, learning algorithm take much longer time to converge ![[Screenshot 2025-10-27 at 15.03.32.png]]
To reach minimum as quickly as possible, change model parameters in direction of steepest slope
- for surface, measure steepness in specific directions independently.
- partial derivative of $y$ wrt $x_1$: $\frac{\delta y}{\delta x_1}$

For two partial derivatives:
$$grad \space y:\frac{\delta}{\delta x_1}i + \frac{\delta}{\delta x_2}j$$

Gradient is slope in higher dimensions. Points in direction of maximum change of function. $$\nabla y=<\frac{\delta y}{\delta x_1},\frac{\delta y}{\delta x_2}>$$
![[Screenshot 2025-10-27 at 15.09.53.png]]

$\alpha$ can define hyperparameter of learning algorithm, defining learning rate 
- large value: huge steps to a minimum
- small value: takes tiny steps to a minimum

Repeat until convergence:::

$$\theta_0:=\theta_0-\alpha\cdot\frac{\delta J}{\delta\theta+0}(\theta_0,\theta_1)$$
$$\theta_1:=\theta_1-\alpha\cdot\frac{\delta J}{\delta\theta+1}(\theta_0,\theta_1)$$

