# **Personalized Medicine: Redefining Cancer Treatment**

## **1. Business Problem**

### **1.1 Description**

Source: https://kaggle.com/competitions/msk-redefining-cancer-treatment

Problem Statement:
Classify the given genetic variations/mutations based on evidence from text-based clinical literature.

### **1.2 Real-world/Business objectives and constraints**

*   No low-latency requirement
*   Errors can be very costly.
*   Interpretability is important.
*   Probability of a data-point belonging to each class is needed.

## **2. Machine Learning Problem Formulation**

### **2.1 Data Overview**

**Data:**
*   We have two data files: one conatins the information about the genetic mutations and the other contains the clinical evidence (text) that human experts/pathologists use to classify the genetic mutations.
*   Both these data files are have a common column called ID
*   Data file's information:

  - training_variants (ID , Gene, Variations, Class)

  - training_text (ID, Text)

**Type of Machine Learning Problem:**

There are nine different classes a genetic mutation can be classified into => Multi class classification problem

**Performance Metric:**

Metric(s): Multi class log loss, Confusion matrix 

**Machine Learing Objectives and Constraints:**

Objective: Predict the probability of each data-point belonging to each of the nine classes.

Constraints:

* Interpretability 
* Class probabilities are needed. 
* Penalize the errors in class probabilites => Metric is Log-loss. 
* No Latency constraints.

## **3. Results**

| Model | Train Error | Cross Validation Error | Test Error | Best Hyperparameter |
| :---: | :---: | :---: |:---: |:---: |
| Naive Bayes | 0.8458 | 1.2871 | 1.286 | 0.1 
| K-Nearest Neighbors | 0.791 | 1.045 | 1.097 | 31 |
| Logistic Regression with class balancing | 0.478 | 1.183 | 1.089 | 0.0001 |  
| Logistic Regression without class balancing | 0.510 | 1.202 | 1.061 | 0.001 |
| Linear Support Vector Machines | 0.719 | 1.206 | 1.133 | 0.01 |
| Random Forest with one hot encoding | 0.680 | 1.165 | 1.149 | 500 |
| Random Forest with response coding  | 0.058 | 1.286 | 1.302 | 100 |
| Stacking Classifier | 0.493 | 1.258 | 1.142 | best of all models |
| Maximum Voting Classifier | 0.852 | 1.219 | 1.183 | best of all models |

## **4. Conclusion**

From the results, we can observe that Logistic Regression with class balancing is a better model because cross validation error and test error are very close with Log loss error of this model.
