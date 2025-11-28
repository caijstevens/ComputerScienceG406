 #ai

We can decide what is considered input and output, as well as definitions of input and output to make helpful in specific use case.

Methods:
- **Manual Labelling**: time costly, must label every individual item
- **Behaviour Tracking**: use real-life behaviour as data 

# Data Sampling

Want minimum amount of data with sufficient information required for proper learning without wasting time.
- reduce info redundancy (data with no useful info or no business value)
- high-level comparison between samples and population to see if sample represents population
- make a sub-sampling of large dataset while keeping statistics intact

**Sample size too small** = not enough info to learn from
**Sample size too large** = too time-consuming
- must compromise 

Statistical framework:
- take random subset from whole population. If same distribution, use as training set
- if using **multivariate** data, consider each independently, each univariate distribution should be comparable with that of population

Comparison methods:
- Categorical variables: Pearson's chi-squared test
- Numerical variables: Kolmogorov-Smirnov test 
- test **null** hypothesis that distributions are consistent
- in multivariate case, all variables need to be significative
	- reject null hypothesis if p-value of at least one test is lower than 5% confidence

### Imbalanced Data 

Not learning enough from minority classes 
- low efficiency but of most interest, causes problem 
- model may have excellent accuracy but bad performance if just reflecting class distribution

Techniques to avoid imbalance:
- try training on whole dataset (true distribution)
- **down-sampling**: training model on disproportionately low subset of majority class examples
- **up-weighting**: adding example weight to down-sampled class equal to factor by which we down-sampled 

# Data Splitting

Splitting data between training set and test set 

Training/test data compromise:
- larger training set = better model will be able to learn
- larger test set = more confidence in evaluation metrics and tighter confidence intervals

Bare minimum, test set must be:
- large enough to yield meaningful results
- representative of whole dataset

### Solution to Overfitting

![[Screenshot 2025-10-17 at 12.50.45.png]]

1. Put test set aside completely unused
2. Pick model that works best on validation set
3. check that model against test set
- useful as creates fewer exposures to test set

### Validation Set vs Test Set 

Validation set:
- compare hyperparameter combinations 
- want to train model with performance depending on hyperparameters (e.g. learning rate)
- validation set used to evaluate model performance for different combinations of values of hyperparameters

Test set:
- compare different models 
- compare trained models in unbiased way by comparing model performance using unseen data 
- test set kept apart from training process, so unseen for comparisons



