#ds 

# Descriptive Statistics 

Organising and summarising the data in ways that facilitate interpretation and analysis
- summary methods highlight important data features (e.g. central tendency, variability)
- numerical and graphical methods 

# Numerical Summarisation

Computation of some statistics of the data 
- mean
- s.d. 
- variance 
- median
- mode 
- range 

# Scatter Plots 

Great for large datasets 
- simplest graphical representation 
![[Screenshot 2025-11-07 at 12.52.28.png]]

# Histograms 

$$\text{Rectange Height}=\frac{\text{Bin frequency}}{\text{Bin width}}$$
![[Screenshot 2025-11-07 at 12.53.24.png]]
- if data are independent samples from continuous dist, histogram is estimate of underlying density function

# Box(-Whisker) Plots

![[Screenshot 2025-11-07 at 12.54.25.png]]

# Modified Whisker Plots 

More advanced box plot
- whisker extends from each end of box 
- data father from box than whiskers plotted individually: **outlier**
![[Screenshot 2025-11-07 at 12.55.20.png]]

# Time-Sequence Plots 

Temporal trends can be ignored in other representations 
- order of data matters 
![[Screenshot 2025-11-07 at 12.56.07.png]]

# Quantile-Quantile Plots 

Compare order statistics to expected values for others dists.
- order data, find corresponding standardised normal quantile values $$i^{th} quantile=\varphi^{-1}(\frac{i}{n+1})$$
- plot observed values against normal quantile values 
- evaluate plot linearity 
- if most points lay on straight line, normal modelling assumption reasonable

# Multivariate Scatter Plot 

Plot each pair of observations with one measurement per axis
- explores covariance (correlation)
- presence of outliers 
- $r=$ correlation coefficient 
![[Screenshot 2025-11-07 at 13.33.56.png]]

**Correlation coefficient** measures relationship strength between continuous variables ($-1\leq r\leq 1$)

# Method of Moments 

Should choose model parameters that match data 
- match sample moments to those of model
- start with lowest moments 
![[Screenshot 2025-11-07 at 13.37.15.png]]

# Testing Model Fit 

Testing model fit is a type of **hypothesis testing**
- specify some statistic of data that is sensitive to model fit and doesn't directly estimate parameters
- compare observed data to repeated simulations 

# Nonparametric 

Some situations, can make inference without specifying dist that data has been drawn from.
- e.g sign tests, rank-based, bootstrap etc 
- more robust but have lower power 