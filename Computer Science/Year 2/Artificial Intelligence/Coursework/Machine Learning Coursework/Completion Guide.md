#ai 

# 1: Set Up Workspace

**Tasks**:
1. ✅ Open Google Colab Starter Notebook 
2. ✅ Check that all cells run without errors 
3. ⏰ Install required Python libraries 
4. ⏰ Mount Google Drive (?)
5. ⏰ Create Drive or directories to store:
	- datasets 
	- code notebooks 
	- plots, charts, results 
	- latex report 

# 2: Explore BraVL Dataset 

**Goal**: Understand what the dataset contains and how it's structured 

**Tasks:**
1. ⏰ Load dataset into Colab 
2. ⏰ Look at info:
	- number of total samples 
	- different labels and classes 
	- number of examples per class 
3. ⏰ Check data types:
	- are there text descriptions for each image?
	- how are the images stored?
4. ⏰ Visualise a few samples, show a few images with their text captions or labels 
5. ⏰ Compute basic statistics:
	- count of samples per class 
	- length of text captions 
6. ⏰ Visualise findings:
	- bar chart for samples per class 
	- histogram for text length distribution 
	- scatter plot for image features 
7. ⏰ Summarise things learned:
	- which classes are most common/rare 
	- are there correlations or patterns between text and image data? 
	- what issues might this cause? (imbalance, bias etc)

# 3: Design Data Splitting Paradigm 

**Goal**: Decide how to divide data for training and testing

**Tasks**:
1. ⏰ Decide on a split strategy (percentages)
2. ⏰ Consider advanced options (optional for extra marks):
	- few shot: use very few examples for training 
	- zero shot: train on some classes, test on unseen ones 
	- federated learning: split data across clients (different devices)
3. ⏰ Implement split in code 
4. ⏰ Check class balance in each split (more histograms to avoid imbalance)
5. ⏰ Write short explanation:
	- why split chosen 
	- what real-world problem it represents 
	- limitations 

# 4: Build Baseline Model 

**Goal**: Train a simple model using standard machine learning tools 

**Tasks**:
1. ⏰ Choose a simple algorithm:
	- logistic regression 
	- support vector machine 
	- k-nearest neighbours 
2. ⏰ Preprocess the data:
	- convert images to numerical ffeatures 
	- convert text to embeddings 
	- combine image and text features?
3. ⏰ Train the model on training data 
4. ⏰ Validate/test it 
5. ⏰ Save results:
	- accuracy, precision, recall, F1-score 
	- confusion matrix 
6. ⏰ Plot results (e.g. confusion matrix heatmap)

# 5: Implement Custom Model 

**Goal**: build own simple ML algorithm to understand how it works internally 

**Tasks**:
1. ⏰ Pick one algorithm to implement manually:
	- linear/logistic regression 
	- simple neural network 
	- k-nearest neighbours 
2. ⏰ Write own training loop:
	- compute loss 
	- apply gradient descent manually 
	- update weights 
3. ⏰ Test and compare with baseline model 
	- does it perform better or worse?
	- how fast does it converge?
4. ⏰ Document differences: 
	- why might results differ? 
	- what was easy/hard about implementing custom model?

# 6: Improve Model 

**Goal**: Boost model's performance and justify improvements 

**Tasks**:
1. ⏰ Try different techniques: 
	- feature scaling (normalisation/standardisation)
	- regularisation 
	- changing hyperparameters 
	- better text/image features 
2. ⏰ Train and test again after each change 
3. ⏰ Keep track of all results (make a table)
4. ⏰ Write short explanations:
	- what was changed 
	- why change was made 
	- what effect it had on performance 

# 7: Analyse and Visualise Results 

**Goal**: Evaluate models thoroughly and interpret what results mean 

**Tasks**:
1. ⏰ For each model version, calculate:
	- accuracy 
	- precision 
	- recall 
	- f1-score 
2. ⏰ Plot following graphs:
	- confusion matrix 
	- precision-recall curve 
	- training vs validation performance 
3. ⏰ Compare models: 
	- baseline vs custom 
	- before vs after improvements 
4. ⏰ Write interpretations:
	 - what worked best and why? 
	 - did chosen paradigm affect results?
	 - was class imbalance or other issues solved? 

# 8: Write Report 

**Goal**: Summarise whole project in 4-page scientific report 

**Tasks**:
1. ⏰ Use LaTeX arXiv/bio-arXiv template 
2. ⏰ Include following sections:
	- Introduction: what was done and why 
	- Dataset and Paradigm: how data was explored and split 
	- Model Development: Baseline, custom, and improved models 
	- Results and Analysis: Metrics, visualisations, key findings 
	- Conclusion: What was learned and future improvements 
3. ⏰ Add plots and tables to support points 
4. ⏰ Cut report down to 4 pages 
5. ⏰ Save and compile to PDF named qvsz29.pdf 

# 9: Prepare and Submit 

**Tasks**:
1. ⏰ Zip all code files into one archive (qvsz29.zip)
2. ⏰ Check that code runs properly in Colab 
3. ⏰ Upload PDF report to Ultra 
4. ⏰ Upload code archive to Ultra 
5. ⏰ Keep a copy of everything in case of being invited to a viva 