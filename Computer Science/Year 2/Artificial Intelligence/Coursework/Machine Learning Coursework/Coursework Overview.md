 #ai 

# Overview (What the project is about)

In this coursework, you’ll be working with the **BraVL dataset**, which includes **both images and text**. This means you’ll be exploring how AI can understand information from **two types of data at once** — pictures and language.

You’ll learn how to:
- Explore and understand a dataset
- Build and train machine learning (ML) models
- Analyse model performance
- Write a short scientific-style report

By the end, you’ll understand how real-world ML projects are built from start to finish.

---

## ✅ Step-by-Step Guide

### **STEP 1: Explore the Dataset**

**Goal:** Understand what the data looks like and what challenges it presents.

**What to do:**

1. Load the BraVL dataset in Colab (the starter code will help).
    
2. Look at:
    
    - How many images and text samples there are
        
    - The number of classes (categories)
        
    - The balance between them (e.g., are some classes much bigger than others?)
        
3. Use **plots** to visualise this information:
    
    - Histograms, scatter plots, or heatmaps
        
4. Write short notes on:
    
    - Any imbalances or patterns you see
        
    - What might make training a model on this data difficult
        

---

### **STEP 2: Design a Data “Paradigm” (How You Split the Data)**

**Goal:** Decide how you will divide the data for training and testing your model.

**What to do:**

1. Choose or design a way to split the data.  
    Examples:
    
    - 70% train / 30% test
        
    - 60% train / 40% test
        
    - Or advanced options like **few-shot**, **zero-shot**, or **federated learning**.
        
2. Explain **why** your chosen split is useful (e.g., “Few-shot helps test model generalisation with less data”).
    
3. Discuss how this split could **affect results** (e.g., “If classes are unbalanced, the model might be biased.”)
    

---

### **STEP 3: Build Your Models**

**Goal:** Train two types of models — one standard, one custom.

**What to do:**

1. **Baseline model (easy start):**
    
    - Use an existing ML algorithm (e.g., Logistic Regression, SVM, or KNN).
        
    - Train it on your dataset split.
        
2. **Custom model (from scratch):**
    
    - Build your own simple model using Python (e.g., manually implement gradient descent).
        
    - Compare how this performs versus the baseline.
        
3. **Improvements:**
    
    - Try to make the model perform better (e.g., tuning hyperparameters, changing features, or adjusting data preprocessing).
        
    - Explain why you made those changes and how they affect performance.
        

---

### **STEP 4: Analyse and Visualise Your Results**

**Goal:** Evaluate how well your models performed and explain the results.

**What to do:**

1. Use **evaluation metrics** such as:
    
    - Accuracy
        
    - Precision
        
    - Recall
        
    - F1-score
        
2. Use **visual tools** to help explain results:
    
    - Confusion matrix
        
    - Precision–recall curve
        
3. Compare models:
    
    - Did your custom/improved model fix issues from before (like class imbalance)?
        
    - What does each result tell you about the model’s strengths and weaknesses?
        

---

### **STEP 5: Write Your Report**

**Goal:** Create a 4-page report that explains what you did and what you found.

**What to do:**

1. Use the **arXiv or bio-arXiv LaTeX template** (recommended).
    
2. Include the following sections:
    
    - **Introduction:** What the project is about
    - **Dataset & Paradigm:** How you explored and split the data
    - **Model Development:** How you built and improved your models
    - **Results & Analysis:** What you found and what it means
        
3. Save the report as a **PDF** named `[your_CIS_username].pdf`.

---

### **STEP 6: Submit Your Work**

**What to submit:**

- A **code archive** (e.g., `[your_CIS_username].zip` or `.tar`)
	- Include all your Jupyter Notebooks (`.ipynb`) or Python files (`.py`).
    - Add comments so the code is clear.
- A **PDF report** (4 pages) compiled from LaTeX.

**Important:**

- Your code won’t be directly marked, but it must **run properly**.
- All submissions will be checked for **plagiarism and collusion**.
- You may be invited to a short **viva** (oral check) to confirm it’s your work.

---

## 💯 Mark Breakdown

|Section|What’s assessed|Marks|
|---|---|---|
|**Data & Paradigm**|Dataset exploration, visualisations, and data splitting design|**30%**|
|**Model Development**|Baseline model, custom model, and justified improvements|**40%**|
|**Result Analysis**|Metrics, visualisations, and interpretation of results|**30%**|

>[!tip] ⭐ **Tip:**
>Doing something _advanced_ (like a new data paradigm or model improvement) can earn extra marks for a First-Class grade.


