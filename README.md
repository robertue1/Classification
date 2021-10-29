# Reducing customer churn for EuroBank


## Abstract

For this project, the main goal is to create a classification algorithm, capable of determining which clients of a financial institution are likely to close their
account. With this information, the bank, could offer those clients a reduction on their monthly fees, or some others benefits to incentive them to keep them as users. To reach the goal, historic data [*from the bank*](https://www.kaggle.com/kmalit/bank-customer-churn-prediction/data) is used, in order to develop a baseline predicting model. From there, I evaluated more complex models and solutions tailored to deal with the imbalanced present in the data. The end result will be an interpretable model and a *black box* model, capable of providing better results.

## Design

To achieve the goal of the project, the baseline model will help us guide our future steps. 



## Data

Data set contains 10.000 data points, for unique clients of the bank, including:
Salary, balance, age, country of residency, number of products, if user has a credit card and a column indicating if the client has closed their account. 

## Algorithms

*Feature Engineering*
1. Mapping latitude and longitude to 3-dimensional coordinates so nearby continuous values would also be close in reality
2. Converting categorical features to binary dummy variables
3. Combining particular dummies and ranges of numeric features to highlight strong signals and illogical values for waterpoint status identified during EDA
4. Selecting subsets of the total unique values for categorical features that were converted to dummies, according to the number of samples they were associated with and their contribution to certain statuses

*Models*
  
Logistic regression, k-nearest neighbors, and random forest classifiers were used before settling on random forest as the model with strongest cross-validation performance. Random forest feature importance ranking was used directly to guide the choice and order of variables to be included as the model underwent refinement.

*Model Evaluation and Selection*
  
The entire training dataset of 59,400 records was split into 80/20 train vs. holdout, and all scores reported below were calculated with 5-fold cross validation on the training portion only. Predictions on the 20% holdout were limited to the very end, so this split was only used and scores seen just once.

The official metric for DrivenData was classification rate (accuracy); however, class weights were included to improve performance against F1 score and provide a more useful real-world application where classification of the minority class (functional needs repair) would be essential.

**Final random forest 5-fold CV scores:** 15 features (7 numeric) with class weights
   - Accuracy 0.797
   - F1 0.791 micro, 0.679 macro
   - precision 0.792 micro, 0.722 macro
   - recall 0.797 micro, 0.658 macro

**Holdout** 
   - Accuracy: 0.802  
   - F1: 0.795 micro, 0.685 macro  
   - Precision: 0.796 micro, 0.725 macro  
   - Recall: 0.802 micro, 0.664 macro

## Tools
- Numpy and Pandas for data manipulation
- Scikit-learn for modeling
- Matplotlib and Seaborn for plotting



## Communication
In addition to the slides and visuals presented, [Tanzania Waterpoints](https://public.tableau.com/profile/arjun#!/vizhome/TanzaniaWater/TanzaniaWaterpoints) will be embedded on my personal website and blog.

<img src="dashboard.png" width=500>
