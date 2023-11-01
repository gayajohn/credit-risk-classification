# Module 20: Credit Risk Report

## Overview of the Analysis

### Objective
The purpose of this analysis is to classify loans as 'healthy' or 'high-risk' based on data about the loan being taken out and information about the borrower.

### The Data
There are 77,536 rows of data. The columns include the following:

 0   loan_size          The size of the loan      
 1   interest_rate      The interest rate of the loan in percentage
 2   borrower_income    The borrower's annual income
 3   debt_to_income     The borrower's debt-to-income ratio
 4   num_of_accounts    The number of bank accounts the borrower has
 5   derogatory_marks   The number of derogatory marks the borrower has received
 6   total_debt         The borrower's total value of pre-existing debt
 7   loan_status        The status of the loan, 'healthy' or 'high-risk'

Our model aims to predict 'loan_status'

**Data Breakdown**

Healthy      75036  97%
High-Risk    2500   3%

Healthy loans constitute 97% of the data set, while high-risk loans make up only 3%.

### The Model
This analysis will use a Logistic Regression Model to classify the loans. This model was chosen as it outputs a value between 0 and 1, making it ideal for classification. 

#### Model 1

The first model randomly splits the data into training and testing data sets. About 75% of the data is used for training and 25% of the data is used for testing. Due to the totally random nature of the split, the training and testing data will share similar proportions of healthy and high-risk data points as the full data set. 

Once the data is split, a logistic regression model is fed with the training data. After the model is trained, the model will attempt to predict the loan_status of the testing data. Then we can proceed to evaluate the accuracy of the model by comparing the predicted loan_status, to the actual.

#### Model 2

As healthy loans are over-represented in the training data, we use random over sampler method to ensure even distribution of healthy and high-risk loans in the training data. The random over-sampler creates duplicates of the high-risk data points to increase their number in the training data. This way, the training data contains 50% healthy loans and 50% high-risk loans. 

Once we have resampled the training data, we feed it to a logistic regression model as before, and follow the same steps stated above.

## Results 

#### Model 1

**Training Data**

- Precision rate of 100% for healthy loans. This means that all loans predicted to be healthy by the model were in fact, healthy loans. 
- Recall rate of 99% for healthy loans. This means that the model correctly labelled 99% of all healthy loans as healthy loans.

- Precision rate of 85% for high-risk loans. This means that 85% of the loans predicted to by high-risk were actually high-risk loans.
- Recall rate of 89% for high-risk loans. This means that the model correctly labelled 89% of all high-risk loans as high-risk loans

- The model had a weighted accuracy of 99%.


**Testing Data: True Test of Model Accuracy**

- Precision rate of 100% for healthy loans. This means that all loans predicted to be healthy by the model were in fact, healthy loans. 
- Recall rate of 100% for healthy loans. This means that the model correctly labelled all of the healthy loans as healthy loans.

- Precision rate of 87% for high-risk loans. This means that 87% of the loans predicted to by high-risk were actually high-risk loans.
- Recall rate of 89% for high-risk loans. This means that the model correctly labelled 89% of all high-risk loans as high-risk loans

- This model has a weighted accuracy of 99%, and a balanced accuracy score of **94.4%**

**Since the accuracy of the testing data is the same as the training data, we can conclude that there is no overfitting or underfitting in this model**

#### Model 2

Model 2 aims to overcome the over-representation of healthy loans in model 1, to make the model better trained at classifying high-risk loans as well. The training data is split 50-50 for healthy and high-risk data points.

**Training Data**

- Precision rate of 99% for healthy loans. This means that 99% of loans predicted to be healthy by the model were in fact, healthy loans. 
- Recall rate of 99% for healthy loans. This means that the model correctly labelled 99% of all healthy loans as healthy loans.

- Precision rate of 99% for high-risk loans. This means that 99% of the loans predicted to by high-risk were actually high-risk loans.
- Recall rate of 99% for high-risk loans. This means that the model correctly labelled 99% of all high-risk loans as high-risk loans

- The model had a weighted accuracy of 99%.

**Testing Data: True Test of Model Accuracy**

- Precision rate of 100% for healthy loans. This means that all loans predicted to be healthy by the model were in fact, healthy loans. 
- Recall rate of 100% for healthy loans. This means that the model correctly labelled all of the healthy loans as healthy loans.

- Precision rate of 87% for high-risk loans. This means that 87% of the loans predicted to by high-risk were actually high-risk loans.
- Recall rate of 100% for high-risk loans. This means that the model correctly labelled all high-risk loans, as high-risk.

- This model has a weighted accuracy of 100% and a balanced accuracy score of **99.6%**

**Since the accuracy of the testing data is almost the same as the training data, we can conclude that there is no overfitting or underfitting in this model**

## Summary

Overall, both models worked quite well with accuracy scores above 90%. However, Model 2 had a higher balanced accuracy score of 99.6% compared to 94.4% of Model 1. Thus, Model 2 is a better classifier of loan status.

From our results it is clear that it is more difficult to accurately classify high-risk loans. However, from our domain knowledge, we know that it is more important to be able to correctly predict high-risk loans as not doing so poses a danger to lenders. 

Here are the concluding recommendations:

- Use Model 2, where high-risk loans are over-represented for predicting loan status.
- If possible, feed the model with more training data on high-risk loans to improve accuracy.
- This model is good enough to run a pilot classifying project, where this model is the first step for predicting loan status. This way, the model can be evaluated with real time data, and improved upon as needed. 
- In this model, we used logistic regression, but it may be worthwhile to try other supervised learning models like Random Forest, KNN or Tensor Flow, to see if they yield better results. 
