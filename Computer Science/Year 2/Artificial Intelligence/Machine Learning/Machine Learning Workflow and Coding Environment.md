 #ai 

# Workflow

1. Learn from data **to**
2. train a model **to**
3. perform tasks **to**
4. infer/predict 

>[!info] Training a Model 
>**Training a model** means using the data to create a model and fine-tune the model to make better predictions. 
>We can then use this predictive model to make predictions on previously unseen data in order to perform specific tasks.

# How Does Machine Learning Work 

### Problem Framing

Identifying training sets, features and labels
- possibly a measure of success
### Data Preparation 

Construct data and transform data
- model is only as good as our data

**Clean and setup data**:
- remove anomalies, missing values and irrelevant features
- transform labels into binary values if possible (numeric value)

### Algorithm Selection 

Types of algorithms:
- Regression
- Regularisation
- Instance-based
- Tree-based
- Clustering 
- Bayesian
- Ensemble
- Dimensionality Reduction

### Model Training 

Data preparation and model selection important
- more time spent on data preparation than model training
- training data used to incrementally improve model performance 
- training aims to find specific pair of **bias** and **weight** values so line can be positioned to divide outcomes
- process iterative, values updated, performance calculated and compared
- process stops when new values do not improve model performance

### Model Testing 

Once training process stops, evaluate model using test set
- aims to see if trained model good for unseen data
- tests accuracy

### Hyperparameter Tuning

See if there is any way to improve training process to improve model.
$$y=b+w\cdot x$$
- where $y$ is output, $b$ is bias, $w$ is weight and $x$ is input

**Learning rate**: how big the change to make in parameter values.
- how accurate a model can become
- how long training process takes 

Hyperparameter tuning is experimental.

### Inference / Prediction 

Taking training and testing data, for a fine-tuned model, and using it to predict the outcome from mystery data.

