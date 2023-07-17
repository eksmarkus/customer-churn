# Findings Summary

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
