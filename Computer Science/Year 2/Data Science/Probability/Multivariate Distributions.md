#ds 

# Multiple Random Variables 

Joint distributions can reason relationship between multiple events
- means multivariate PDFs

# Bivariate Distribution

For two events $A$ and $B$ with RVs $X$ and $Y$:
$$P(A\cap B)=P(\{X=x\}\cap\{Y=y\})=P(X=x,Y=y)$$
- this is the **joint probability** of $X=x$ and $Y=y$

If $X$ and $Y$ jointly distributed RVs:
- if discrete: Joint Probability Mass Function (PMF)
- if continuous: Joint Probability Density Function (PDF)
- both: Join Cumulative Distribution Function (CDF)

### Discrete Bivariate Joint Distribution 

Joint PMF of two discrete RVs describes proportion of prob. mass placed on each possible value pair $(x,y)$
- extends to Joint CDF as:
$$F(x,y)=P(X\leq x, Y\leq y)=\sum\limits_{s\leq x}\sum\limits_{t\leq y}f(s,t) \text{ for } -\infty<x,y<+\infty$$

Joint PMF properties:
1. $f_{xy}(x,y)\geq 0$
2. $\sum_{x\in R}\sum_{y\in S}f_{XY}(x,y)=1$
3. $f_{XY}(x,y)=P(X=x,Y=y)\equiv P(\{X=x\}\cap\{Y=y\})$
# Marginal Probability Distributions 

Although bivariate probability distribution describes joint probability, might need to view $X$ and $Y$ separately
- marginal probability distributions:
$$f_X(x)=P(X=x)=\sum\limits_{y\in S}P(X=x,Y=y)=\sum\limits_{y\in S}f_{XY}(x,y)$$
$$f_Y(y)=P(Y=y)=\sum\limits_{x\in R}P(X=x,Y=y)=\sum\limits_{x\in R}f_{XY}(x,y)$$
# Discrete Conditional Distributions 

For two discrete RVs taking values in range $R$ and $S$ respectively with joint PMF $f_{XY}(x,y)$. Assume $F_X(x)>0$, then:
$$F_{Y|X=x}(y)=P(Y=y|X=x)=\frac{P(X=x,Y=y)}{P(X=x)}=\frac{f_{XY}(x,y)}{f_X(x)}$$
Reverse if $f_Y(y)>0$

Properties:
1. $\sum_{y\in Y}f_{Y|X=x}(y)=1$
2. For any set $B$: $$P(Y\in B|X=x)=\sum\limits_{y\in B}f_{Y|X=x}(y)$$
To model the joint behaviour of more than two RVs, extend concept of joint distribution to more than two variables. $$f(x_1,x_2,\dots,x_n)=P(X_1=x_1,X_2=x_2,\dots,X_n=x_n)$$
# Continuous Bivariate Random Variables 

Discrete functions applicable to continuous RVs
- **replace summations with integrals**

If joint PDF is $f_{XY}(x,y)$ then: $$P(a\leq X\leq b, c\leq Y\leq d)=\int^b_a\int^d_cf_{XY}(x,y)dydx$$
- can be thought of as the chance of lying in a small rectangle 

Properties:
1. $f_{XY}(x,y)\geq 0$
2. $\int^{+\infty}_{-\infty}\int^{+\infty}_{-\infty}f_{XY}(x,y)dydx=1$
3. For any set $R$ in the $\mathbb{R}^2$ plane: $$P((X,Y\in R) = \int\int_Rf_{XY}(x,y)dydx$$
# Continuous Marginal Probability Distributions 

For separating $X$ and $Y$:
$$f_X(x)=\int f_{XY}(x,y)dy$$
$$f_Y(y)=\int f_{XY}(x,y)dx$$

# Continuous Conditional Probability Distributions 

If $f_X(x)>0$:
$$F_{Y|X=x}(y)=\frac{f_{XY}(x,y)}{f_X(x)}$$
Reverse if $f_Y(y)>0$

Properties:
1. $\int f_{Y|X=x}(y)dy=1$
2. For any set $B\subseteq\mathbb{R}$: $$P(Y\in B|X=x)=\int_B f_{Y|X=x}(y)dy$$
# Continuous Multivariate Distribution 

For continuous RVs, joint PDF of $X_1,\dots,X_n$ is function $f(x_1,x_2,\dots,x_n)$ such that for any $n$ intervals $[a_1,b_1],\dots,[a_n,b_n]$: $$P(a_1\leq X\leq b_1,\dots,a_n\leq X_n\leq b_n)=\int^{b_1}_{a_1}\dots\int^{b_n}_{a_n}f(x_1,\dots,x_n)dx_n\dots dx_1$$
# Multivariate Marginal Probability Distributions 

For joint density function $f(x,y,z,a,b)$ for RVs $X,Y,Z,A,B$, marginal distribution $f_{YA}$ on random variables $Y$ and $A$ is: $$f_{YA}(y,a)=\int\limits_{x\in\mathbb{R}}\int\limits_{z\in\mathbb{R}}\int\limits_{b\in\mathbb{R}}f(x,y,z,a,b)db dzdx$$
# Independence of RVs

$X$ and $Y$ are independent if one of following holds:
![[Screenshot 2025-10-24 at 18.10.45.png]]

# Mean and Variance of JRVs

For Joint RVs $X$ and $Y$:
$$E(X)=\mu_X=\sum\limits_{x\in R}xf_X(x)$$
$$E(Y)=\mu_Y=\sum\limits_{y\in S}yf_Y(y)$$
$$Var(X)=\sum\limits_{x\in R}x^2f_X(x)-(E(X))^2$$
$$Var(Y)=\sum\limits_{y\in S}y^2f_Y(y)-(E(Y))^2$$
# Covariance 

Measures strength of linear relationship between two variables 
- $X,Y$ are RVs with means $\mu_X$ and $\mu_Y$
$$cov(X,Y)=\sigma_{XY}=E[XY]-E[X]E[Y]$$
$$cov(X,Y)=E[(X-\mu_X)(Y-\mu_Y)],$$
where $\mu_X=E(X)$ and $\mu_Y=E(Y)$

Properties:
$$Cov(aX+b, cY+d)=acCov(X,Y)$$
$$Cov(X_1+X_2,Y)=Cov(X_1,Y)+Cov(X_2,Y)$$
$$Cov(X,X)=V(X)$$
If $X$ and $Y$ are independent then $Cov(X,Y)=0$
- converse not necessarily true

# Correlation Coefficient 

Normalised covariance measure. $$Corr(X,Y)=\rho_{XY}=\frac{cov(X,Y)}{\sqrt{V(X)V(Y)}}$$
- always between -1 and 1
- if $X$ and $Y$ independent then uncorrelated, $\rho_{XY}=0$
- converse not necessarily true 
