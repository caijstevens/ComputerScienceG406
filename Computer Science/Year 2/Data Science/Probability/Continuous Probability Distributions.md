#ds 

# Probability Density Functions 

A continuous random variable described by PDF
- maps probability of range of events from sample space to function 
- PDF of $X$ is denoted by $f_x$ or just $f$

For continuous random variable $X$, a probability density function is a function $f(x)$ such that:
1. $f(x)\geq 0$, for all $x\in\mathbb{R}$
2. $\int^{+\infty}_{-\infty}f(x)dx=1$
3. $P(a\leq X\leq b)=\int^b_af(x)dx$, for any $a,b\in\mathbb{R}$ such that $a\leq b$
![[Screenshot 2025-10-20 at 17.12.37.png]]

# Cumulative Distribution Function (CDF)

CDF of a random variable $X$ is denoted by $F(x): \mathbb{R}\rightarrow [0,1]$, where $x\in\mathbb{R}$ and is given by: $$F(x)=P(X\leq x)=\int^x_{-\infty}f(t)dt$$
CDF properties:
- $F(x)$ is nondecreasing: if $x\leq y$, then $F(x)\leq F(y)$
- $0\leq F(x)\leq 1; \lim_{x\rightarrow +\infty}F(x)=1$
- For $a\leq b$ we have: $P(a\leq X\leq b)=F(b)-F(a)$

If $F(x)$ is CDF of variable, derivative is PDF.

# Mean and Variance 

**Mean**: centre of probability distribution
- mean or expected value of CRV $X$:
$$\mu=E(X)=\int^{+\infty}_{-\infty}xf(x)dx$$

**Variance**: measure of dispersion or variability in a distribution
- variance of $X$
$$\sigma^2=V(X)=E[(X-\mu)^2]=\int^{+\infty}_{-\infty}(x-\mu)^2f(x)dx$$
$$\text{Also: }V(X)=E[X^2]-\mu^2=\int^{+\infty}_{-\infty}x^2f(x)dx-\mu^2$$
CRVs have same mean and variance properties as DRVs
# Functions of Random Variables 

For arbitrary function $h:\mathbb{R}\rightarrow\mathbb{R}$:
- If $X$ is CRV and $Y=h(X)$:
$$E(Y)=E(h(X))=\int^{+\infty}_{-\infty}h(x)f(x)dx$$

# Continuous Uniform Distributions 

Let $X$ be CRV with density function
![[Screenshot 2025-10-20 at 17.37.05.png]]
- $X$ is a CRV with range $[a,b]$

For a CRV $X$ with range $[a,b]$, then:
$$E(X)=\frac{b+a}{2}$$
$$V(X)=\frac{(b-a)^2}{12}$$
# Exponential Distribution 

Models time elapsing between events
- probability of occurrence of an event after period of time
- has parameter $\lambda$ that is called **rate parameter** and is average number of events occurring in period of one time unit.

A random variable $X$ is called an exponential random variable with parameter $\lambda>0$ when probability density function is:![[Screenshot 2025-10-20 at 17.42.50.png]]
For CERV $X$ with rate parameter $\lambda$:
$$E(X)=\frac{1}{\lambda}$$
$$V(X)=\frac{1}{\lambda^2}$$
Exponential distribution is **memoryless**. For any $t_1,t_2\geq 0$:
$$P(X>t_1+t_2|X>t_1)=P(X>t_2)$$

