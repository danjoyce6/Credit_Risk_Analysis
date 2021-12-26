# Credit_Risk_Analysis

## Overview
The purpose of this analysis was to analyze and predict credit risk from a variety of machine learning models on the credit card dataset from LendingClub and determine the best model.  Various machine learning models were used including oversampling methods using RandomOverSampler and SMOTE algorithms, undersampling methods using the ClusterCentroids algorith, a combinational approach of over and undersampling using the SMOTEENN algorithm, and the BalancedRandomForestClassifier and EasyEnsembleClassifer that reduce bias to predict credit risk.

## Results
The LoanStats_2019Q1.csv file was cleaned and the get_dummies feature from Pandas was used to create dummy variable for all of the objet variable in the dataset.  The target variable was our y variable and represented the loan status for all machine learning models. The X variable was all of the other features in the dataset.  The data was split into training and testing sets using the train_test_split function from sklearn.model_selection module.  These variables were used on all of the following machine learning models with various sampling techniques.  Prior to any resmapling there were 68470 low risk credit applications and 347 high risk credit applications.
  - Random Oversampling Model
  - The RandomOverSampler model from imblearn was used to resample the data to create equal amounts of low risk and high risk applications.  After resampling there were 51353 low risk and high risk applications in the y resampled dataset.  The model was fit using the lbfgs solver and random state 1.  The balanced accuracy score for this model was 0.64145.  A confusion matrix was generated for this model in the following image.  Results showed a precision value of 0.01 for high risk classification while the recall or sensitivity was 0.67.  The sensitivity or recall of detecting a high risk application is 67% for this model. The low precision is not as much of a concern, we would prefer if the test misclassified more low risk applications so that no high risk applications are missed by the model.  The balanced accuracy score of 64.0% represents a moderate ability of the model to correctly predict high risk credit applications.
  - ![image](https://user-images.githubusercontent.com/88444529/147415364-8a9cf52c-ef52-4bb6-b5ba-26fee8c2e5e1.png)
  - SMOTE Oversampling
  - The SMOTE model from imblearn was used to resample the data to create equal amounts of low risk and high risk applications.  After resampling there were 51353 low risk and high risk applications in the y resampled dataset.  The model was fit using the lbfgs solver and random state 1.  The balanced accuracy score for this model was 0.64145.  A confusion matrix was generated for this model in the following image.  Results showed a precision value of 0.01 for high risk classification while the recall or sensitivity was 0.61.  The sensitivity or recall of detecting a high risk application is 61% for this model. The low precision is not as much of a concern, we would prefer if the test misclassified more low risk applications so that no high risk applications are missed by the model.  The balanced accuracy score of 64.1% represents a moderate ability of the model to correctly predict high risk credit applications. 
  - ![image](https://user-images.githubusercontent.com/88444529/147415356-bb7b7277-1d46-4239-ae43-a8920b1dee73.png)
  - ClusterCentroids Undersampling
  - The ClusterCentroids model from imblearn.under_sampling module was used to undersample the majority population in the y variable.  The data was resampled and then fit to linear regression model and had the model predict new y values.  Folowing resampling, there were 259 high risk and low risk classifications in the y_resampled variable.  The balanced accuracy score for the ClusterCentroids methods was .5021, indication almost a flip of a coin chance that the model could correctly predict high risk applications.  The recall or sensitivity for this model was 0.59, which is similar to the sensitivity for both the SMOTE and RandomOverSampler models.  The precision of Positive Predictive Value was also 0.01 for this model.  
  - ![image](https://user-images.githubusercontent.com/88444529/147415559-000179ad-6f3e-4f2d-b6ab-3ae877345943.png)
  - SMOTEENN (Over and Under Sampling)
  - The SMOTEENN model from imblearn.combine was then ran and the data was over and undersampled used the SMOTEENN method with a random state of 0.  The resampled data was fit and there were 68460 high risk applications and 63011 low risk applications in the y_resampled variable, representing the new over and under sampled data.  Y prediction values were then made for this model and a logistic regression model was generated for a random state of 1 and solver of lbfgs.  The balanced accuray score for this model 64.2% which represents a moderate ability of the model to predict true positive high risk applications.  The models sensitivity or recall was 0.72 for this model, or 72% of all high risk applications were found by the model.  The precision for this model was similarly low for high risk applications with a value of 0.01.  The values for all of these tests can be seen in the following image.
  - ![image](https://user-images.githubusercontent.com/88444529/147415748-35a8ba81-ca99-461b-88ce-a4639a755dd8.png)
  - Balanced Random Forest Classifier
  - The BalancedRandomForestClassifier ensemble model was then used to make decision trees from imblearn.ensemble.  The model was made and then fit to the X_train and y_train variables and predictions from the model were made.  A confusion matrix, imbalanced classification report, balanced accuracy score, and feature importance were generated for the model and displayed in the image below.  The accuracy score for this model was 75.6%, which represents a good ability of this model to predict the true high risk credit applications.  The sensitivity of this model was 0.62, or the ability of the model to detect 62% of all of the true positive high risk applications.  The precision of this model was also higher than the previous models with 0.03.  The most important features in this model were the roral_rec_prncp (0.074), total_pymnt_inv (0.0669), and last_pymnt_amnt (0.0610).  The full list of features can be seen in the github repository as well.
  - ![image](https://user-images.githubusercontent.com/88444529/147416150-f626397c-970c-4d8e-9989-2a30763519c9.png)
  - Easy Ensemble and AdaBoost Classifier
  - The EasyEnsembleClassifier was then used on a random state of 1 and with 100 estimators to fit the X_train and y_train data from the imblearnen.ensemble module.  The accuracy score, confusion matrix, and classification report were then generated for this final model.  The accuracy score of this model was 95.1%, which represented an excellent ability of the model to detect true positive high risk applications.  The sensitivity or recall was also very good with 0.86, or the ability of 86% of all true high risk applications to be detected by the model.  The recall of this model was also higher than the rest with 0.08.  The full list of values can be seen in the following image for the EasyEnsembleClassifier model.
  - ![image](https://user-images.githubusercontent.com/88444529/147416302-da6b92ba-fca0-44c4-ba14-a63cc103413a.png)
