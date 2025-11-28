 #ai 

# Machine Learning Models and Algorithms 

Need a ML **algorithm** to train model 
- model and algorithm selection picks best performance 
![[Screenshot 2025-10-24 at 13.24.10.png]]

### Classification 

Models used to predict discrete class label 
- classification algorithms need to learn from very large training set 
- supervised learning 
- e.g. diagnostics, fraud detection

### Regression 

Models used to predict specific value in **continuous** distribution
- regression algorithms need to learn from very large training set 
- supervised learning 
- e.g. weather forecasting, population growth 

### Clustering 

Models used to discover patterns in data 
- need to learn from many inputs and unlabelled outputs 
- unsupervised learning 
- e.g. customer segmentation, recommender systems 

### Dimensionality Reduction 

Models used to decrease number of input features, transforming data from high to low dimensional space 
- simplifies dataset with fewer features, reduces overfitting 
- unsupervised learning 
- e.g. pre-processing data, big data visualisation

# Different Machine Learning Algorithms 

Choose algorithm based on kind of inference we want to see in data
- based on function similarity ![[Screenshot 2025-10-24 at 13.32.23.png]]
### Regression Algorithms 

To find approximation function mapping input to continuous output 
- output variable real values
- predicts quantities
- learns in iterations using measure of error in predictions 

### Regularisation 

Form of regression
- shrinking the coefficient estimates towards zero
- penalise models based on complexity and flexibility
- favouring simpler models to prevent overfitting 

### Instance-Based Algorithms 

Compares new problem instances with training ones, rather than generalising like model-based algorithms
- storing all training instances, then predictions made by comparing using similarity measures
- can adapt to unseen data 

### Tree-Based Algorithms 

Construct tree-based models of decisions based on actual attribute values 
- decision flow goes along tree until reaches leaf 
- easy to interpret 
- large trees are complex, slow and less accurate 

### Clustering Algorithms 

Uses inherent structures in data to group for maximum commonality
- no specific labels
- group instances based on centroid, density, distribution or hierarchy 
- unsupervised learning to find natural groups 

### Bayesian Algorithms 

To create models that apply Bayes' Theorem 
![[Screenshot 2025-10-24 at 14.06.12.png]]

### Association Rule Learning Algorithms 

Rule-based to discover relations between variables 
- seeking strong rules discovered in databases 
![[Screenshot 2025-10-24 at 14.13.26.png]]

### Dimensionality Reduction Algorithms 

To find inherent structure in data to reduce number of random variables.
- feature selection to find subset of original variable set to get smaller subset for particular problem
- feature extraction to reduce data to have space with fewer dimensions 

### Ensemble Algorithms 

Combining several models into one optimal model
- decreases variance and bias or improves predictions 

### Artificial Neural Network Algorithms 

Inspired by structure and function of neural networks of animal brains 
- based on collection of units/nodes (artificial neurones)
- each neurone can transmit signal to others 

### Deep Learning Algorithms 

Extension of Artificial Neural Networks 
- to build larger, more complex networks 
- deals with unstructured dataset 

### Reinforcement Learning Algorithms 

Concerned with how AI takes actions to maximise rewards
- agents are rewarded/punished for actions 
- environment stated using Markov decision process 
-  can be model-based or model-free

# Decomposition of Machine Learning Algorithms 

**Representation**: The hypothesis space of the learner, represented in some formal language that computer can handle 
- Instances 
- Hyperplanes
- Decision trees
- Sets of rules
- Neural networks
- Graphical models 

**Evaluation**: An evaluation function to distinguish good models from bad ones 
- Accuracy/error rate
- precision
- Posterior probability
- Cost/utility 

**Optimisation**: A method to search among the models in the language for the highest-scoring one
- Combinatorial optimisation 
- Continuous optimisation 

# Supervised Learning 

Learning a function, which is inferred from labelled training data containing a set of training examples, to map an input to an output

>[!info] Supervised Learning 
>Called supervised because there are labelled examples for learning algorithm to learn from or train on.

$m \space n$-dimensional feature vectors (each vector has $n$ elements):
$$x^{(i)}=\begin{bmatrix}
x_1^{(i)} \\ x_2^{(i)} \\ x_3^{(i)} \\ \dots \\ x_n^{(i)}
\end{bmatrix} \in\mathbb{R}^n, i\in(1,2,\dots,m)$$
A collection of corresponding labels $y$:
$$y=\begin{bmatrix}
y^{(1)} \\ y^{(2)} \\ y^{(3)} \\ \dots \\ y^{(m)}
\end{bmatrix}$$
Goal is to build model (real-valued function)

$$\text{credit score } = f(\text{total credit, short term loan, credit utilisation, missing payments)}$$
$$\hat{y}=h(X)$$
Hypothesis function $h$ is defined on set of feature vectors $X$ to make a prediction of $y$ ($\hat{y}$)

# Regression vs Classification 

### Regression 

**Regression**: predicting a continuous quantity output for an input
- trying to learn from labelled pairs of instances 
- find approx function that maps input to numerical and continuous output
- output variables are real-valued data

Can have real-value or discrete input variables 
- univariate if input is single value 
- is multivariate if input is a vector containing group of single values

Root Mean Squared Error used to estimate regression model performance:
$$RMSE=\sqrt{\frac{1}{n}\sum\limits^n_{i=1}(\hat{y}_i-y_i)^2}$$
**Residuals**: measure of how far regression line is from data points 
- RMSE: measure of how spread out residuals are 

### Classification

**Classification**: predicting a discrete class label output for an input 
- trying to learn from labelled pairs of examples 
- find approx function that maps input to categorical and discrete ouptut
- output variables are categories

Can have real-value or discrete input variables 
- binary classification if output variable could be 2 classes
- multi-class classification if output variable could be >2 classes

$$\text{accuracy} = \text{correct predictions / total predictions}$$
### Comparison 

**Difference**: prediction result / output variable 
- Regression: continuous
- Classification: discrete 

**Overlap**:
- Regression may predict discrete values but as integer quantity
- Classification may predict continuous values but as probability for class label

No overlap in performance estimation methods:
- Regression can be RMSE, but classification not
- Classification can be accuracy, but regression not
