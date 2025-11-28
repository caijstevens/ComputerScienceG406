#ds 

>[!info] Random Variable 
>A **random variable** is a function that assigns a number to each outcome in the sample space of a random experiment.
- discrete means to have countably many values 

# Probability Distribution 

>[!info] Probability Distribution 
>The **probability distribution** of a random variable $X$ describes the probabilities associated with each possible outcome of $X$.
>List possible values of $X$ e.g. $x_1,x_2,\dots$
>These values are associated with probabilities given by $$P(X=x_k)=f(x_k),k=1,2,\dots,n$$
- $f$ is the **Probability Mass Function**.

>[!info] Probability Mass Function 
>For a discrete random variable $X$ with possible values of $x_1,x_2,\dots$ the PMF is a function $f:\{x_1,x_2,\dots\}\rightarrow [0,1]$ satisfying three properties:
>1. $f(x_1)\geq 0$
>2. $\Sigma^{\infty}_{k=1}f(x_i)=1$
>3. $P(X=x_i)=f(x_i)$

# Cumulative Distribution Function 

$$F(x)=P(X\leq x)=\Sigma_{x_i\leq x} P(X=x_i) = \Sigma_{x_i\leq x} f(x_i) \text{, where } x\in \mathbb{R}$$
- for discrete variable, we use PMF more than CDF
- $F$ has interesting properties:
	- $F(x)$ is nondecreasing (if $x\leq y$, then $F(x)\leq F(y)$)
	- $0\leq F(x)\leq 1(\lim\limits_{x\rightarrow -\infty} F(x)=0; \lim\limits_{x\rightarrow +\infty} F(x) = 1)$

# Mean and Variance 

**Mean**: centre or middle of the probability distribution
- $\mu = E(X) = \sum\limits_{x} xf(x)$

**Variance**: measure of variability in distribution
- $\sigma^2 = V(X) = E[(X-\mu)^2] = \sum\limits_{x}(x-\mu)^2f(x)=\sum\limits_{x}x^2f(x)-\mu^2$
- standard deviation of $X$ is $\sigma = \sqrt{\sigma^2}$

# Transformed Random Variables 

- $E(aX+b) = aE(X) + b$
- $E[h(X)]=\Sigma_x h(x)f(x)$
- $V(aX+b) = a^2V(X)$
- $V(X)=E(X^2) - [E(X)]^2$

# Independence of Random Variables 

Two random variables are independent if for sets $A$ and $B$ we have: $$P(\{X\in A\}\cap\{Y\in B\}\equiv P(X\in A, Y\in B) = P(X\in A)P(Y\in B)$$
For independent variables **only**, we have:
$$V(X_1+X_2+\dots+X_n)=V(X_1)+V(X_2)+\dots+V(X_n)$$

# Discrete Uniform Distribution 

Assumes only a finite number of possible values with equal probability.
- the PMF of $X$ is given by $(X\sim {Uni(n)})$:
$$P(X=k)=f(k)=\frac{1}{n}$$
# Bernoulli Distribution

Most commonly appearing discrete distributions associated with Bernoulli trials
- a Bernoulli trial has **two** possible outcomes

$$P(A)=p, P(B) = P(\overline{A}) = 1-P(A) = 1-p=q$$

For a distribution $X\sim Ber(p)$:
- $E(X) = p$
- $V(X)=p(1-p)=pq$

# Discrete Binomial Distribution 

The random variable $X$ that equals the number of trials that result in success is a **Binomial Random Variable** with parameters $n$ and $p$. The PMF of $X$ is given by $(X\sim Bin(n,p$))$
- $P(X=k)=f(k)=\binom{n}{k}p^k(1-p)^{n-k}, k=0,1,\dots,n$
- $E(X) = np$
- $V(X) = np(1-p)$

# Discrete Geometric Distribution

Independent trials with constant success probability $p$. For $(X\sim Geom(p))$:
- $P(X=k)=f(k)=p(1-p)^{k-1}, k=1,2,\dots$
- $E(X)=\frac{1}{p}$
- $V(X)=\frac{1-p}{p^2}$

If you have waited $k$ trials without seeing a success, you must wait $m$ more trials to get success with probability of $p(1-p)^{m-1}$
- **no memory**, no number of trials makes success more likely
- unique property to Geometric
- for objects for which there is no wear during normal operation, lifespan well modelled by Geometric

# Negative Binomial Distribution 

Defines the number of trials until $r\in\mathbb{N}$ successes achieved

$X\sim NegBin(r,p)$:
![[Screenshot 2025-10-16 at 10.55.04.png]]
- $E(X)=\frac{r}{p}$
- $V(X)=r\frac{1-p}{p^2}$

# Poisson Distribution 

Derived from binomial distribution, modelling number of events in set period of time
- events independent, expected events per unit time is constant

$X$ is a Poisson random variable with parameter $\lambda > 0$. $X\sim Poisson(\lambda)$:
$$P(X=k) = f(k) = \frac{e^{-\lambda}\lambda^k}{k!},k=0,1,2,\dots$$
$$E[X]=\lambda$$
$$V(X)=\lambda$$
