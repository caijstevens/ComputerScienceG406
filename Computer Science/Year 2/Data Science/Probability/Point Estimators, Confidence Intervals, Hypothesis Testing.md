 #ds 


# Standard Error 

Standard error of sample statistic is standard deviation of sampling distribution 

| Statistic                                                       | Standard Error                             |
| --------------------------------------------------------------- | ------------------------------------------ |
| Mean $(\overline{X})$                                           | $\sigma_X=\frac{\sigma}{\sqrt{n}}$         |
| Proportion $(\hat{p})$ (fraction of sample with same condition) | $\sigma_{\hat{p}}=\sqrt{\frac{p(1-p)}{n}}$ |

# Types of Statistical Inference 

Estimating population parameters:
- **point estimation**: using sample statistic to estimate pop parameter 
- **interval estimation**: estimation of amount of variability in sample statistic

**Hypothesis testing**:
- comparison of sample results with known or hypothesised pop parameter 
![[Screenshot 2025-11-03 at 16.40.10.png]]

### Point Estimator 

Draws inference about population by estimating value of unknown parameter using single value or point
![[Screenshot 2025-11-03 at 16.42.31.png]]

**Bias** of the estimator: $b(\hat{\theta})=E(\hat{\theta})-\theta$
- unbiased estimator: $b(\hat{\theta})=0$

**Variance** of estimator measures amount of divergence from mean: $$V(\hat{\theta})=E[(\hat{\theta}-E(\hat{\theta}))^2]$$
### Interval Estimator 

>[!tip] 
>Confidence interval: point estimate $\pm$ (measure of how confident we want to be) $\times$ (standard error)
- plausible range of values 
- goal: capture true effect 

Calculating confidence interval:
$$point\space estimate(\hat{\theta})\pm(z)\times(\sigma)$$
$$P(\hat{\theta}-|z_{\frac{\alpha}{2}}|\times s.e\leq\theta\leq\hat{\theta}+|z_{\frac{\alpha}{2}}|\times s.e)=1-\alpha$$
If you hear confidence interval, assume **two-sided**
- sometimes one-sided better 

# Hypothesis Testing 

Uses sample data to evaluate hypothesis about pop parameter 
- differentiates between real and random patterns 

>[!info] Hypothesis 
>An assumption about the population parameter. 
- $H_0$ is **null hypothesis**: states assumption to be tested
- $H_1$ is **alternative hypothesis**: opposite of null hypothesis 

Assume $H_0$ and $H_1$ are both about parameter $\theta$
- take random sample and compute sample statistic $\hat{\theta}$
- calculate probability (**p-value**) that random sample statistic $\leq or \geq \hat{\theta}$ assuming $H_0$ true 
- if p-value $<$ significance level, reject $H_0$
- otherwise no significant evidence to reject $H_0$

