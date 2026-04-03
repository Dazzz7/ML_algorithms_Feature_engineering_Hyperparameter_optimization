# Suicide Attempts Analysis in Shandong, China
Project Overview

This project analyzes suicide attempts in Shandong, China, focusing on identifying the key factors contributing to suicide and predicting outcomes using machine learning models. Through Exploratory Data Analysis (EDA), feature engineering, and predictive modeling, this study highlights demographic, occupational, seasonal, and behavioral patterns associated with suicidal behavior.

Details:
## Exploratory Data Analysis (EDA)
1. Dataset Overview:
- Dataset contains demographic information (Age, Sex, Education, Urban/Rural), occupation, methods of suicide, hospitalization status, and outcome (Died or Alive).
- Handled missing values:
Age: filled with mean value
Month: backward fill + most frequent value
Categorical “unknown” values replaced with the most frequent category

2. EDA Insights:
- Gender: Males had higher suicide mortality than females.
- Age: Individuals aged 40–60 were most affected.
- Occupation: Farmers and homemakers had higher suicide rates.
- Education: Less-educated individuals had higher mortality.
- Urbanization: Non-urban residents were at higher risk.
- Methods of Suicide: Pesticides and hanging were the most common methods.
- Seasonality: Male suicides peaked in spring/summer; female suicides peaked in winter.
  
3. Visualizations Used:
-Countplots, bar charts, heatmaps, pairplots, and boxplots
-Correlation heatmaps revealed relationships between numerical variables

## Feature Engineering
- One-Hot Encoding applied to categorical variables (Sex, Occupation, Method, Education, Urban, Hospitalised)
- Combined with numerical features (Age, Year, Month) to create the final feature matrix
- Addressed missing/unknown values and normalized numerical features using StandardScaler for machine learning models
  
## Machine Learning Models

### 1. Logistic Regression
- Hyperparameters:
random_state=6 for reproducibility
Default C=1.0, penalty='l2'
- Performance:
Test Accuracy: 91%
F1-score: 91%
Precision: 87% (Died), 97% (Alive)
Recall: 85% (Died), 96% (Alive)
- Feature Importance:
Age, occupation, education, and method were the most significant predictors
- ROC-AUC: ~0.92

Optimization Notes:

Standardizing data improved model convergence and stability
Performance was robust across train-test splits (20–30% test size)

### 2. Decision Tree Classifier
- Hyperparameters Tested:
Default depth vs max_depth=5
Criterion: gini (default) and entropy
- Performance:
Default tree: F1-score 87%
Max-depth 5: F1-score 90%
Observed improvement in precision for Alive class (~99%)
- Feature Importance:
Occupation (farming), method (pesticides, hanging), and age were most impactful
- ROC-AUC: ~0.91
- Observations:
Pruning the tree with max_depth reduced overfitting while slightly sacrificing true positive prediction

### 3. Random Forest Classifier
- Hyperparameters Tested:
n_estimators=100, max_depth=5
random_state=0 for reproducibility
- Performance:
F1-score 90%
Precision: 84% (Died), 100% (Alive)
Recall: 81% (Died), 100% (Alive)
- Feature Importance:
Top features: Age, Occupation, Method, Education, Hospitalization
- ROC-AUC: ~0.93
- Optimization Notes:
Limiting max_depth prevented overfitting
Increasing n_estimators marginally improved stability but increased computation time
Random Forest outperformed Decision Tree in terms of ROC-AUC and robustness

## ROC Curve Comparison

All three models were compared using ROC curves to evaluate the trade-off between true positive rate (sensitivity) and false positive rate.

Logistic Regression: ROC-AUC ~0.92
Decision Tree: ROC-AUC ~0.91
Random Forest: ROC-AUC ~0.93

Observation: Random Forest provided the best overall performance while maintaining interpretability of feature importance.

## Tools & Libraries
Python Libraries: pandas, numpy, matplotlib, seaborn, scikit-learn
Machine Learning Models: Logistic Regression, Decision Tree, Random Forest
Visualization: Count plots, bar plots, heatmaps, pairplots, ROC curves

## Conclusion
This project provides actionable insights into suicidal behavior in Shandong, China, highlighting vulnerable populations and predictive features. The analysis can guide preventive strategies and targeted interventions to reduce suicide rates in high-risk groups.
Suicide is strongly associated with age, occupation, education, and method.
Seasonal and urban/rural factors influence suicide trends.
Machine learning models can accurately predict outcomes, with Random Forest providing the best performance.

# Live Demo:
https://colab.research.google.com/drive/11kl8MjWFSHhAnDYSm8QMK3zq2KgBJiY_#scrollTo=GSjv_INk7oRJ
