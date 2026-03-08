# Customer Churn Prediction

This Data Science project aims to develop a machine learning model to predict whether a customer will leave a telecommunications company. It focuses on maximizing the detection of customers with a high probability of churn.

## Project Description

Customer churn is a critical issue where the cost of retaining an existing customer is significantly lower than acquiring a new one. This project contains:

* Analysis and Modeling: EDA, feature engineering, and model training and selection (XGBoost, Random Forest, KNN).
* Model Optimization: The final model is optimized not only for accuracy but also prioritizing Recall (sensitivity) through the F2-Score.
* MLOps Deployment: The application was packaged with Docker and deployed on Render.

## Technologies Used

* Python 3
* Data manipulation: Pandas, NumPy
* Machine Learning: Scikit-learn, XGBoost.
* Visualization: Matplotlib, Seaborn.
* Interpretability: SHAP.
* Deployment: Streamlit, Docker, Render

## Modeling Methodology

1. Preprocessing
* Missing value imputation.
* Feature Scaling: Normalization with MinMaxScaler.
* Encoding: One-Hot Encoding and binary mapping.


2. Training results
The XGBoost model was selected for its ability to generalize and superior performance.

| Model | ROC AUC |
| --- | --- |
| XGBoost | 0.8428 |
| Random Forest | 0.8420 |
| KNN | 0.8136 |

3. Model decision threshold optimization
The decision threshold was adjusted to maximize the F2-Score (prioritizing recall over precision), given that a false negative is more expensive than a false positive.

* Optimal threshold: 0.3915
* Recall reached: 87.63%

## Model Explainability

SHAP values were used for model explainability. The key factors identified are:

* Increase in churn probability: Fiber Optic, high Monthly Charges, and Electronic Check payment.
* Decrease in churn probability: Two-year contracts and tenure.

## Deployment

Streamlit has been used to develop the application and Docker to package it.

The container encapsulates data preprocessing, the model (XGBoost), and the explainability logic (SHAP).

### Hosting on Render

The application is deployed on Render at the following link (it may take a while to start): [https://telecom-churn-app-deployment.onrender.com/](https://telecom-churn-app-deployment.onrender.com/)

The github repository for the deployment is: [https://github.com/Ivan-0612/telecom-churn-app-deployment](https://github.com/Ivan-0612/telecom-churn-app-deployment)

