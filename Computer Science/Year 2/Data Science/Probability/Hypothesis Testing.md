#ds 

# Test Statistic and Rejection Criteria 

Specify test statistic to be used:
- $z$-score if normal distribution usable 
- $t$-score if t-distribution can be used (sample size $n<30$, or standard deviation not known)

Specify criteria for rejection of $H_0$:
- set of values of test statistic where rejection should occur (depends on significance $\alpha$)
- determined via $Z$-table or $T$-table 
- can be represented as **critical region**

### Test Statistics for $Z$-Test 

Value used for making decision about $H_0$

Test statistic for proportions: $$z=\frac{\hat{p}-p}{\sqrt{\frac{pq}{n}}}$$
Test statistic for mean: $$z=\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}$$
# Criteria for Rejection 

**Critical region** is set of all values where $H_0$ is rejected 
- **significance level** $\alpha$ is probability that TS will fall in critical region 
- **critical value** is value that separates critical region from values that do not lead to rejection.
![[Screenshot 2025-11-06 at 17.36.20.png]]
- for a two-tailed test, $\alpha$ is divided equally between two tails 

# $p$-Values 

The $p$-value is probability of getting TS value that is at least as extreme as value representing sample data
- assumes $H_0$ true 
- reject $H_0$ if $p$-value $\leq\alpha$
- fail to reject $H_0$ if $p$-value $>\alpha$
![[Screenshot 2025-11-06 at 17.38.43.png]]

# Testing Claims about Population Mean (with $\sigma$ not known)

For simple random sample with unknown population $\sigma$:
- Test statistics ($s$ is s.d of sample): $$z=\frac{\overline{X}-\mu_{\overline{X}}}{\frac{s}{\sqrt{n}}} \text{ where }n>30$$$$t=\frac{\overline{X}-\mu_{\overline{X}}}{\frac{s}{\sqrt{n}}} \text{ where }n<30$$
# T-Distribution 

For modest sample sizes, correction needed because sample mean distribution not normal.
- family of distributions for each sample size 
- lower peak and wider tails than normal dist as small samples have more inaccurate estimates 
- degree of freedom: $n-1$ (where $n$ is sample size)

Properties:
- different for different sample sizes 
- still bell shape but wider as expected when $s$ used to estimate $\sigma$
- $t$-dist has mean of $t=0$, s.d varies with sample size 
- as $n$ increases, $t$-dist gets closer to standard normal dist 

Example $T$-test:
![[Screenshot 2025-11-06 at 17.46.37.png]]

# Wording Test Conclusion 

![[Screenshot 2025-11-06 at 17.47.31.png]]

# Hypothesis Test Errors 

![[Screenshot 2025-11-06 at 17.48.00.png]]
- $\alpha=P(\text{type I error})=P(\text{Reject }H_0,\text{ when }H_0\text{ is true})$
- $\beta=P(\text{type II error})=P(\text{Fail to Reject }H_0,\text{ when }H_0\text{ is false})$

Type I error is mistake of rejecting null hypothesis when it is true.
- Type II error is mistake of not rejecting null hypothesis when it should be 

### Mitigations 

For fixed $\alpha$, increasing $n$ will cause decrease in $\beta$
- for fixed $n$, decrease in $\alpha$ will cause increase in $\beta$ and vice versa 
- to decrease both, increase $n$.

# Power of Hypothesis Test 

Probability $(1-\beta)$ of rejecting false null hypothesis 
- uses particular significance level and particular population parameter value 
- **the probability of supporting an alternative hypothesis that is true**
$$\text{Statistical Power}=1-\beta=P(\text{Reject }H_0\text{ when }H_1\text{ is true})$$
