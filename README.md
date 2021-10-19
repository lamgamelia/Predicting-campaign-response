# Predicting campaign response
 **Predicting customer response on marketing campaign**

 The dataset (Source: https://www.kaggle.com/rodsaldanha/arketing-campaign) consists of customer information and their responses (all or null) on 5 campaigns conducted. There is no further information provided on the time period or company that conducts the campaign

 ## Project Intro/Objective
 
 The project will use the customer information available as features to train a classification model. Model can be used to increase response rate or reduce expenses by reducing target response group for efficient marketing campaign

## Methods Used

* Data Munging
* EDA
* Feature Engineering
* Forward Feature Selection
* Linear Regression
* Lasso Regression
* Logistic Regression

## Technologies

* Python
* Pandas, jupyter
* Sklearn

## Project Description

The dataset includes features such as education, marital status, income, family members and products bought by customers. It also implies a cost of $3 per target customer and revenue of $11 per response. 

Worksteps:
1. Data cleaning involves filling null values in income field using the mean of customers brouped by education. 
2. Feature engineering:
    * Converting categorical features (i.e. education, marital_status)\
    Note that marital_status may be converted using one-hot encoding instead of label encoding
    * Parse the date of membership field into datetime data type and convert into number of 'days_membership' relative to the first customer's registration date
    * Drop irrelevant features (e.g. ID and constants such as cost and revenue)
3. Feature selection:
    * Lasso Regression did not give significant reduction in features with only 'MntWines' being the feature dropped
    * Manual forward feature selection by observing the AUC plot across different no of features selected. This allows us to determine 15 features to be adopted, afterwhich no significant improvement in model accuracy.
4. Predictive modelling using logistic regression:
    * Data set is slighly imbalance with only 14% of positive responses, split train test data set with stratification and use LogisticRegressionCV for built-in cross validation
    * Apply standard scaling transformation on features
    * Evaluate the performance of model using confusion matrix and AUC score from the ROC Curve\
    sklearn's plot_confusion_matrix function uses default probability of 50%. From ROC Curve it can be observed that Best Threshold = 0.155034\
    Confusion matrix is re-generated using model fit with the Best Threshold. This improves TPR metric significantly
5. Business application includes 
    * Observing important features of customers with high coefficient values that will determine response/no response, such as the recency of registration and responses in past campaigns
    * Cumulative gain curve is useful in observing the marginal improvements in response rate as more customers are targeted. It is observed that ~70% of target responses can be achieved with only ~20% of the population targeted
    * Using simple profit computation, it is also observed that at 20% of the current population targeted, profitability is maximum. Meanwhile, profit will turn negative when more than 50% of the population is targeted. Hence only the top 20% population should be targeted for efficiency and maximum profitability.
    Refer to attached .ppt for more detailed business applications.


