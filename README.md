# Credit Risk Analysis
The following project uses Jupyter Notebooks and Pandas on a mock dataset to evaluate machine learning models.


# Overview of the Project

Fast Lending is a peer-to-peer lender that would like to use machine learning to make lending decisions faster and with better risk prediction.  The purpose of this project was to test how various machine learning models performed on the loan dataset provided.

Each of the models were trained on 75% of the dataset and then tested on the remaining 25%.  All models received the same initial training and testing data.  Then the models were applied to the data.  Various performance metrics of each model were captured and results are shown below.

Because the number of loans in the low-risk class far outnumbered those in the high-risk class, various resampling methods were used to address this class imbalance.  These methods are designed to help improve the models' performance at predicting high-risk loans.


# Results

## Naïve Random Oversampling

* Balanced Accuracy – 0.67
* Precision High Risk Loans - 0.01
* Precision Low Risk Loans - 1.00
* Recall High Risk Loans – 0.70
* Recall Low Risk Loans – 0.63


## SMOTE 
Synthetic Minority Oversampling TEchnique

* Balanced Accuracy – 0.66
* Precision High Risk Loans - 0.01
* Precision Low Risk Loans - 1.00
* Recall High Risk Loans – 0.63
* Recall Low Risk Loans – 0.69


## Undersampling

* Balanced Accuracy – 0.54
* Precision High Risk Loans - 0.01
* Precision Low Risk Loans - 1.00
* Recall High Risk Loans – 0.69
* Recall Low Risk Loans – 0.40


## SMOTEENN
Combination Over & Undersampling, Synthetic Minority Oversampling TEchnique & Edited Nearest Neighbors

* Balanced Accuracy – 0.68
* Precision High Risk Loans - 0.01
* Precision Low Risk Loans - 1.00
* Recall High Risk Loans – 0.77
* Recall Low Risk Loans – 0.58


## Balanced Random Forest Classifier

* Balanced Accuracy – 0.79
* Precision High Risk Loans - 0.03
* Precision Low Risk Loans - 1.00
* Recall High Risk Loans – 0.70
* Recall Low Risk Loans – 0.87


## Easy Ensemble AdaBoost Classifier

* Balanced Accuracy – 0.93
* Precision High Risk Loans - 0.09
* Precision Low Risk Loans - 1.00
* Recall High Risk Loans – 0.92
* Recall Low Risk Loans – 0.94


*Comprehensive results from each model are available below in the appendix.*


# Summary

## Discussion of Results

There was a large variance seen between the performance of the various models.  In general, as more advanced models were utilized, performance improved.  In some areas, all models performed well.  On the other hand, all struggled in other areas.  The ensemble models both performed at higher levels than other models.  


## Balanced Accuracy

The balanced accuracy rate evaluates the ratio of how accurate the model’s predictions were ranging from 0.00 (meaning no, or almost no, predictions were correct) to 1.00 (meaning every, or nearly every, prediction was correct).

The overall balanced accuracy rate ranged from 0.54 (undersampling) – 0.93 (Easy Ensemble AdaBoost Classifier).  While the accuracy rate is important, it is only one factor to consider.


## Low-Risk Loans

All models achieved very solid performance on low-risk loans.  This is especially true of precision, meaning almost all loans predicted to be low risk were indeed low risk.  All models achieved 1.00 precision for low-risk loans.  In other words, there were few false negatives in our tests.

The recall, or sensitivity, scores trended lower.  This score is representative of how many loans that were actually low risk were predicted as such by the model.  Here performance ranged from 0.40 (undersampling) – 0.94 (Easy Ensemble AdaBoost Classifier).


## High-Risk Loans

Our primary goal, however, is to predict high risk loan applications.  In the dataset provided, 68,470 loans (99.5%) were low risk while 347 (0.05%) were high risk.

When looking at high-risk loans, our models did not perform as well.  The testing dataset contained 101 high-risk loans.  The precision of correctly predicting high-risk loans was very low, ranging from 0.01 (four models) to 0.09 (Easy Ensemble AdaBoost Classifier).  In other words, even the best model predicted far more high-risk applications than there were in reality.  That model, Easy Ensemble AdaBoost Classifier, predicted 1,076 high-risk loans but only 93 of those were actually high risk.  There were 983 false positives and the model missed 8 loans that were actually high risk.

Performance on recall was better for all models, especially for high-risk loans.  Performance ranged from 0.69 (undersampling) – 0.92 (Easy Ensemble AdaBoost Classifier).  For the top scoring model, this means that of those loans that were actually high risk, the model successfully identified 92% as such, missing 8% of the high-risk loans.


## Recommendation for Model to Adopt

Overall, the Easy Ensemble AdaBoost Classifier performed better than any other model.  It had the highest performance in all categories reviewed (other than low risk precision where all models tied with 1.00).  It is recommended that this model be utilized to help streamline the lending process, leading to improved turnaround times and enhanced risk prediction.  

However, manual processing will still be required.  Despite it having the top performance, Easy Ensemble AdaBoost Classifier generated a large number of false positives in testing.  This means that the model predicted the loans to be high risk but they were actually low risk.  Given this high number of missed predictions, it is recommended that all applications that are predicted to be high risk should still be closely scrutinized before final approval.  

However, given the high recall performance on low-risk loans, it likely makes sense to greatly reduce any manual processing steps for those loans the model predicts to be low risk.  In our testing dataset, more than 99% of the loans were low risk.  While the model will invariably miss predicting a small percentage of loans that will actually be high risk (missing 8% in our testing), the efficiency gain of reducing manual processing on the nearly 94% that were predicted as low risk may outweigh the few that might be caught with a higher level of manual scrutiny.  

If the model is adopted for more automation, it is recommended that a regular process be developed to continue to train and test the model with expectations of, over time, better performance.  If a decrease in performance is noted, it is recommended that another comprehensive review of various models be conducted.


# Appendix

## Naïve Random Oversampling

![Naive Random Oversampling](https://user-images.githubusercontent.com/82730954/130366779-7f87660e-6087-4acb-b5be-e23379884b63.png)

## SMOTE
Synthetic Minority Oversampling TEchnique

![SMOTE](https://user-images.githubusercontent.com/82730954/130366786-a07c1377-dc5e-404c-82c5-9ec45ddb129c.png)

## Undersampling

![Undersampling](https://user-images.githubusercontent.com/82730954/130366796-bbcfb3d6-6559-4ffe-a35d-15cd9e15be1f.png)

## SMOTEENN
Combination Over & Undersampling, Synthetic Minority Oversampling TEchnique & Edited Nearest Neighbors

![SMOTEENN](https://user-images.githubusercontent.com/82730954/130366800-2d4b88fe-7e87-4e7d-bcdd-444f124dab49.png)

## Balanced Random Forest Classifier

![BalancedRandomForestClassifier](https://user-images.githubusercontent.com/82730954/130366805-27b0a117-a421-4c31-aa46-5e2b5ed6cdc4.png)

## Easy Ensemble AdaBoost Classifier

![EasyEnsembleAdaBoostClassifier](https://user-images.githubusercontent.com/82730954/130366810-87cca60a-286e-454c-b430-46726e30cf5b.png)
