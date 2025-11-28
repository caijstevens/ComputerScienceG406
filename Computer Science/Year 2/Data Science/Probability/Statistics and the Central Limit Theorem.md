 #ds 

**Parameter**: a numerical feature of a population

**Statistic**: a numerical valued function of the sample observation
- every statistic is a random variable 

# Sample vs Population 

Use $\mu$ for mean of population and $\sigma$ for standard deviation of population
- use $\overline{x}$ for mean of sample and $s$ for for standard deviation 
- true proportion of population with trait is $p$
- proportion of sample with trait is $\hat{p}$ (used to estimate $p$)


| Value                 | Population (Size N)                          | Sample (Size n)                                    |
| --------------------- | -------------------------------------------- | -------------------------------------------------- |
| Expected Value (Mean) | $\mu=\frac{\sum^N_{i=1}x_i}{N}$              | $\overline{x}=\frac{\sum^n_{i=1}x_i}{n}$           |
| Variance              | $\sigma^2=\frac{\sum^N_{i=1}(x_i-\mu)^2}{N}$ | $s^2=\frac{\sum^n_{i=1}(x_i-\overline{x})^2}{n-1}$ |

# Sample Median

Splits dataset in half.
![[Screenshot 2025-10-31 at 13.18.49.png]]

# Sampling vs Population Distribution 

**Population** dist is distribution of values of variable for all individuals
- **sampling** dist is distribution of values taken by statistic in all samples of same size from same population 

Variability of sample statistics is measured by **standard error**

# Statistical Inference 

Uses info from sample to draw conclusions about population 
- collect data from sample to make inference 

# Inequalities and Bounds 

### Markov's Inequality 

Let $X$ be a non-neg random variable:
$$P(X\geq a)\leq \frac{E(X)}{a}, for\space all\space a>0$$
Can give very loose bound but makes no assumption about form of distribution 

### Chebyshev's Inequality 

Let $X$ be a RV with $E(X)=\mu$ and $V(X)=\sigma^2$
$$P(|X-\mu|\geq k)\leq\frac{\sigma^2}{k^2}, for\space all\space k>0$$

Since $(X-\mu)^2$ is non-negative RV, we can apply Markov's inequality with $a=k^2$

# Distribution of Sample Mean 

$\overline{X}$ is mean of sample (size $n$) from large population (mean $\mu$ and SD $\sigma$). 
- sampling dist of $\overline{X}$ has mean $\mu$ and SD $\sigma/\sqrt{n}$
$$E(\overline{X})=E\bigg(\frac{X_1+X_2+\dots+X_n}{n}\bigg) = \mu$$
$$V(\overline{X})=V\bigg(\frac{X_1+X_2+\dots+X_n}{n}\bigg) = \frac{\sigma^2}{n}$$
# Weak Law of Large Numbers 

For RVs $X_1,X_2,\dots$, suppose all $X_i$ have distribution $F$ with $E(X_i)=\mu$ and $V(X_i)=\sigma^2$ and let $\overline{X}=\frac{\sum^n_{i=1}x_i}{n}$. For any $\epsilon > 0$, we will have:
$$P(|\overline{X}-\mu|\geq\epsilon)\Rightarrow^{n\rightarrow+\infty}0$$

# Strong Law of Large Numbers 

For RVs $X_1,X_2,\dots$, suppose all $X_i$ have distribution $F$ with $E(X_i)=\mu$. Let $\overline{X}=\frac{\sum^n_{i=1}x_i}{n}$. We will have:
$$P\Bigg(\lim_{n\rightarrow+\infty}\Bigg(\frac{X_1+X_2+\dots+X_n}{n}\Bigg)=\mu\Bigg)=1$$
- as number of observations drawn increases, mean $\overline{x}$ of observed values converges to mean $\mu$ of population.

# Central Limit Theorem

For RVs $X_1,X_2,\dots$, suppose all the $X_i$ have distribution $F$ with $E(X_i)=\mu$ and $V(X_i)=\sigma^2$ and let $\overline{X}=\frac{\sum^n_{i=1}x_i}{n}$. As $n\rightarrow\infty$, we will have $\overline{X}\sim N(\mu,\frac{\sigma^2}{n})$
$$Z=\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}$$
- CLT is reason why real world things appear to be normally distributed
- explains binomial approximation 
- further from normal distribution, larger the sample size needed 
- if population normal, $n\geq 1$

