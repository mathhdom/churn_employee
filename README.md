# Identifying Employees Who May Leave the Company

The objective of this project is to develop a machine learning model to predict whether an employee will leave the company. Based on these predictions, the company can identify at-risk employees and implement preventive actions.

# Data

The data was obtained from a Kaggle dataset, accessible via the link below:

- link: [https://www.kaggle.com/datasets/kmldas/hr-employee-data-descriptive-analytics/code]

# Exploratory Data Analysis

Balancing:
- The target variable is imbalanced in the dataset. Around 76% of employees stay with the company, while 24% have already left.

Correlation:
- The correlation matrix shows that there are no strong linear relationships between the independent variables and the dependent variable ('left'). Therefore, tree-based algorithms can capture non-linear relationships, such as Random Forest.

Satisfaction Level:
- By evaluating satisfaction levels and comparing them with whether employees left or stayed, it is noticeable that employees with higher satisfaction tend to stay with the company, as confirmed by the hypothesis test.
- The Mann-Whitney test was applied because normality cannot be assumed in the data distribution, and also considering that the dataset is a limited sample from a specific time period. Therefore, it is not possible to claim that the entire dataset represents the entire population.

# Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- SciPy (non-parametric test)

# Modeling

Choice of Performance Metric:
- The goal is to increase recall performance, as the business problem emphasizes the importance of correctly predicting those who will leave the company to promote actions.
- It is preferable to take actions for individuals who would not leave the company than to fail to take action for those who will leave.

Preprocessing:
- Nominal variables such as Department were encoded using OneHotEncoder.
- The ordinal variable salary was encoded respecting its hierarchy (“low”, “medium”, “high”).
- The Nearmiss method was used to balance the classes by reducing the majority class.
- The K-Means algorithm was applied to create a categorical representation of the satisfaction_level variable, with the choice of 'k' based on the elbow method.

# Results

Initial Model:
- Algorithm: Random Forest.
- Accuracy: 94%
- Precision: 98%
- Recall: 76%
- ROC-AUC: 88%

Final Model (after optimizations):
- Algorithm: Random Forest.
- Accuracy: 97%
- Precision: 91%
- Recall: 96%
- ROC-AUC: 96%

# Conclusion

The project achieved its goal by significantly improving the recall of the final model compared to the initial model, enabling efficient classification of potential employees who may leave the company to implement mitigation actions.

It is noted that the model understands that the employee's department is not relevant for predicting whether they will leave the company.

The implementation of validations with real data is necessary to validate the impact of the preventive actions suggested by the model.

The application of other models, such as XGBoost, and the search for new variables may potentially improve performance.
