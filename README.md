# Customer Churn Prediction

This project **aims** at building a predictive model to forecast customer churn of a Telecom company (here and below referred to as the Project Owner). At-risk customers might be offered special conditions, discounts, and promotional codes by the marketing team of the Project Owner.

Customers' personal information, tariffs, and agreements details are provided by the Project Owner.

In order to pursue this aim, the following objectives are addressed.

**Objectives**

* Understand the data
* Select appropriate modeling techniques
* Evaluate the models using ROC-AUC metrics. The threshold value posed by the Project Owner is 0.82
* Assess the significance of the features

## General Info on the Project Owner Services

The Project Owner company offers two main types of services.

Fixed telephone connection with a single or multiple landline.
Internet connection through DSL (digital subscriber line) or fiber optic.
In addition to the main services, several extra options are available

Internet security, i.e. anti-virus software (DeviceProtection) and the ability to block suspicious websites (OnlineSecurity)
Dedicated technical support line (TechSupport)
Cloud services for data backups (OnlineBackup)
Streaming TV and movies catalog (StreamingMovies)
The subscription fee can be paid on a monthly, yearly, or biennial basis. There are various payment methods available, and customers have the option to choose paperless billing.

## DNA Restrictions

This project was executed as a final graduation work at Yandex Practicum Course on Data Science. Due to DNA Restrictions, the date is the property of the Project Owner and the online course organizer. The outcomes of this project are publicly available for read-only.

# Conclusions Summary

As a result of this project, I have developed a predictive model aimed at anticipating customer churn for the Telecom company (The Project Owner). This model will be used to prevent customer churn since it can identify at-risk customers. Based on this data, the marketing team of the Project owner can offer special conditions, discounts, or promotional codes for those customers and thus prevent churn. 

## Data Preprocessing

As part of the data preprocessing, we addressed several issues, including handling missing data and performing necessary data type replacements. We observed that it is better to represent the contract duration in days than to operate with the start and end days of the contract. The target feature was also identified, which indicates whether or not a contract was terminated.

## Data Preparation

After data preprocessing, we prepared the data to select features and target features, which were then encoded, scaled, etc. depending on the requirement of a particular model. For example, scaling was applied only for the LogisticRegretion, as generally required for a linear model. Encoding was performed only for the RandomForest model. Gradient boosting models, such as CatBoost and LGBM, do not require such prior feature processing.

## Choosing the Best Model

Using GridSearchCV and RandomizedSearchCV the best set of parameters was found for the following models: LogisticRegression, RandomForestClassifier, CatBoost, LGBM. 

### Testing results

Based on validation results, the following models were selected for testing: CatBoost (as a primary one) and LGBM.

**Model: CatBoost**
ROC_AUC with cross-validation: 0.86
Confusion matrix:[[1144 148],[ 75 391]]
Recall: 0.84
Precision: 0.73
CPU times: total: 46.9 ms
Wall time: 22.5 ms

**Model: LGBM**
ROC_AUC with cross-validation: 0.83
Confusion matrix: [[1101 191],[ 89 377]]
Recall: 0.81
Precision: 0.66
CPU times: total: 125 ms
Wall time: 36.8 ms

## Final Model and Feature Importance
Based on the ROC-AUC metrics, considering cross-validation on the training set, the CatBoost and the LGBM models were marked as promising models. Finally, the Catboost model ('reg_lambda': 1, 'learning_rate': 0.25, 'iterations': 800, 'depth': 3) was chosen as the best model in this work. On the test sample, the model achieved an ROC-AUC value of 0.86, surpassing the threshold posed by the customer.

Furthermore, a feature importance study revealed that the most influential features are duration and monthly_charges. This information can be Based on the ROC-AUC metrics, considering cross-validation on the training set, the CatBoost and the LGBM models were marked as the promising models. Finally, the Catboost model ('reg_lambda': 1, 'learning_rate': 0.25, 'iterations': 800, 'depth': 3) was chosen as the best model in this work. On the test sample, the model achieved an ROC-AUC value of 0.86, surpassing the threshold posed by the customer.

Furthermore, a feature importance study revealed that the most influential features are duration and monthly_charges. This information can be leveraged to develop effective customer retention strategies. By focusing on these significant features, appropriate steps can be taken to stop customer churn.
