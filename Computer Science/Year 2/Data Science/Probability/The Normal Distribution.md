 #ds 

# Normal Distribution (= Gaussian Distribution)

Sum of many independent random variables looks like a bell curve with different centres and spreads

>[!info] The Normal Distribution 
>A random variable $X$ is said to have normal distribution with parameters mean $\mu (-\infty<\mu<+\infty)$ and variance $\sigma^2(\sigma>0), written as $X\sim N(\mu,\sigma^2)$. The PDF is defined as:
>$$f(x)=\frac{1}{\sqrt{2\pi\sigma^2}}e^\frac{(x-\mu)^2}{2\sigma^2}$$
>Also: $E(X)=\mu$ and $Var(X)=\sigma^2$
- $\mu$ controls location
- $\sigma$ controls spread 

The relationship between sum of many random variables and normal distribution is called the **Central Limit Theorem**

### Features 

Regardless of $\mu$ and $\sigma$ values:
- area between $\mu-\sigma$ and $\mu+\sigma$ is about 68%
- area between $\mu-2\sigma$ and $\mu+2\sigma$ is about 95%
- area between $\mu-3\sigma$ and $\mu+3\sigma$ is about 99.7%

Tail symmetry:
- normal curve symmetric and area under curve = 1, easy to determine auc in tails

# Standard Normal Distribution 

>[!info] Standard Normal Distribution 
>Random variable $Z$ with PDF as follows is a standard normal random variable:
>$$f(z)=\frac{1}{\sqrt{2\pi}}e^{-\frac{z^2}{2}}$$
>This is a normal random variable with parameters $\mu=0$ and $\sigma^2=1$
>Corresponding CDF is:
>$$\Phi(z)=P(Z\leq z)$$

All normal distributions $X$ can be converted into the standard normal using:
$$Z=\frac{X-\mu}{\sigma}$$
- this is called $z$-score 
- tells you how many $\sigma$s  an $X$ value is from the mean
- helps determine relationship between scores

### Z-Table 

$Z$-table used to find probabilities for standard normal distribution 
- cumulative $Z$-table: gives proportion of population that is to left or below $Z$-score 
- complementary cumulative: proportion to right or above
- cumulative from mean: proportion of population to left of $z$-score to the mean only 

Z-table values all for $z>0$
- standard normal PDF $f$ for $\Phi$ symmetric around 0, so $f(-z)=f(z)$:
$$\Phi(z)=1-\Phi(-z)$$
- where $\Phi(z)=P(Z\leq z)$ is CDF of standard normal distribution 

# Normal Approximation to the Binomial 

For binomial distribution where $n$ is large and $p$ is middling (close to .5) then binomial tends to look like normal:
$$X\sim Bin(n,p)\implies P(X\leq x)\approx \Phi(\frac{x-np}{\sqrt{npq}})$$
- approximation good for $np>5$ and $n(1-p)>5$

**Continuity correction**: change $P(X\leq x)$ to $P(X\leq x+0.5)$ before using Normal approximation

# Normal Approximation to the Poisson 

If $X$ is a Poisson random variable with $E(X)=\lambda$ and $Var(X)=\lambda$:
$$X\sim Poisson(\lambda)\implies P(X\leq x)\approx\Phi(\frac{x-\lambda}{\sqrt{\lambda}})$$
- Same continuity correction applied as before
- approximation good for $\lambda>5$

