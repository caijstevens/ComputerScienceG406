 #ai 

Raw/source data can be directly collected from source
- may contain useful info and errors
- different formats
- XML, JSON, database records etc

# Feature Engineering 

Need to put heterogeneous data sources together and create **Feature Vectors** from it for learning algorithms 

>[!info] Feature Engineering 
>The process of selecting and extracting features from raw data

![[Screenshot 2025-10-20 at 18.02.10.png]]

# Data Binning 

Transform numeric features into categorical ones based on range
- equal spaced binning cannot capture skewed distribution
- dividing into quantile bins (dynamic width) helps, each bin has similar number of instances 

# Feature Scaling 

Helps transform values numeric features to be on similar scale without distorting differences in ranges of values
- necessary for many ML algorithms 
- gradient descent converges faster with feature scaling

### Min-Max Normalisation 

Simplest technique for scaling
- rescale feature into range of $[0,1]$
$$x^{(i)}_{norm}=\frac{x^{(i)}-min(x)}{max(x)-min(x)}$$
- can be used to rescale feature into other ranges

### Mean Normalisation

Rescale feature values around mean value 
$$x^{(i)}_{norm}=\frac{x^{(i)}-mean(x)}{max(x)-min(x)}$$

### Standardisation (Z-Score Normalisation)

Rescale feature values to have $\mu=0$ and $\sigma=1$
$$z=\frac{x-\mu}{\sigma}$$
Normalisation can generate smaller $\sigma$ than Standardisation, can scale out data to be more concentrated around mean
- Normalisation does not require Gaussian distribution therefore good for neural networks but not for outliers; Standardisation can help when Gaussian distribution needed

### Unit-Length Scaling 

Rescale components of feature vector, so complete vector's length is one.
$$x^{(i)}_{unit\space len}=\frac{x^{(i)}}{||x^{(i)}||}$$
- normalise $N$-dimensional vector features to have length 1

### Log Scaling 

Rescale feature values to narrow range
- may skew features to normal distribution
$$x^{(i)}_{scaled}=log(x^{(i)})$$

### Clipping 

Caps all feature values above specific max value or below specific min value
- set max/min values to avoid outliers
- used when dataset has extreme outliers

# Transforming Categorical Data 

Categorical data is **discrete**
- **Nominal/labelled** data values not comparable or calculatable
- **Ordinal** data is with a set order/scale to it

# Encoding 

ML algorithms require features to be numbers, requires **encoding**

### Ordinal Encoding 

To transform categorical features into ordinal numbers in ordered set
- map each unique label to integer value
- only use ordinal when there is known relationship between categories

### Nominal Encoding 

ML algorithms don't assume ordering in class labels
- have to use ordering tools

### One-Hot Encoding 

Converts categorical data into numerical format 
- creates binary vector for each category

Example: ["red","green","blue"] $\rightarrow$ ["100","010","001"]

Prevents model from assuming order or magnitude

### Feature Crossing 

Synthetic feature formed by multiplying 2 or more features
- bring predictive abilities beyond what those individual features can provide
- works when data are linearly separable $$y=\theta_0+\theta_1x_1+\theta_2x_2$$

For nonlinear problem:
- create feature cross $x_3=x_1x_2$
- linear model becomes: $$y=\theta_0+\theta_1x_1+\theta_2x_2+\theta_3x_3$$
Different types:
- $[A\times B]$: multiplying values of two features
- $[A\times B\times C\times D]$: multiplying values of multiple features
- $[A\times A]$: squaring single feature
- $[A\times A\times A\times A]$: multiplying values of single feature multiple times

# Dealing with Missing Data 

Missing data occurs when no value stored for variable in example 
- common, can affect conclusions 
- many different methods for dealing with

Methods:
- dropping rows/columns with missing values 
- replacing with mean/median/mode
- predicting missing values e,g, regression 
- using ML algorithms that support missing values 