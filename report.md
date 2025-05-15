Customer Churn Prediction – Detailed Report

1. Objective
The goal of this project is to predict whether a customer will churn (leave the company) using the Telco Customer Churn dataset from Kaggle.

2. Dataset Overview
- **Source:** Kaggle - Telco Customer Churn
- **Rows:** 7,043 customers
- **Columns:** 21 features including demographic, account, and service info
- **Target variable:** `Churn` (Yes/No)

3. Exploratory Data Analysis (EDA) & Data Preprocessing
- Checked for missing values: none significant except `TotalCharges` which had some blanks, handled by converting to numeric and imputing/filling as needed.
- Converted categorical variables to numeric using Label Encoding and One-Hot Encoding where appropriate.
- Scaled numerical variables (`MonthlyCharges`, `TotalCharges`, `tenure`) using StandardScaler for uniformity.
- Created a new feature `tenure_group` to bucket tenure into meaningful groups representing customer longevity.

4. Feature Engineering
- Added `tenure_group` to capture customer tenure length in months categorized into short, medium, and long tenure.
- This helped improve model’s understanding of customer loyalty.

5. Models Trained & Compared
We trained three models to compare performance:

 a) Random Forest Classifier
- Robust ensemble method
- Handles categorical and numerical features well
- Default hyperparameters initially

b) XGBoost Classifier
- Gradient boosting ensemble
- Often provides better accuracy with hyperparameter tuning
- Tuned parameters with GridSearchCV

 c) Deep Learning Model (Neural Network)
- Fully connected feed-forward network
- Used dropout and batch normalization for better generalization
- Optimized with Adam optimizer and binary cross-entropy loss
 6. Model Evaluation Metrics

| Model         | Accuracy | Precision (Churn) | Recall (Churn) | F1-Score (Churn) |
|---------------|----------|-------------------|----------------|------------------|
| Random Forest | 78%      | 0.62              | 0.49           | 0.54             |
| XGBoost       | 78%      | 0.60              | 0.53           | 0.56             |
| Deep Learning | **80%**  | **0.62**          | **0.59**       | **0.61**         |

- Accuracy is similar for Random Forest and XGBoost (~78%), but Deep Learning slightly outperforms both at 80%.
- Recall for churn class (customers who leave) is important — Deep Learning has the highest recall (0.59), indicating it finds more churners correctly.
- Precision values show the correctness of churn predictions; all models have similar precision (~0.60-0.62).

Sample Classification Report for Deep Learning Model

          precision    recall  f1-score   support

       0       0.85      0.87      0.86      1035
       1       0.62      0.59      0.61       374

accuracy                           0.80      1409



 7. Feature Importance & Interpretation
- **Contract Type:** Customers on month-to-month contracts are more likely to churn.
- **Tenure:** Longer tenure correlates with lower churn.
- **Monthly Charges:** Higher monthly charges tend to increase churn risk.
- **Internet Service Type:** Certain service types show higher churn.
- **Tech Support:** Lack of tech support leads to more churn.

Used SHAP values and feature importance plots (from Random Forest and XGBoost) to confirm these insights.

 8. Business Recommendations
- **Promote Long-Term Contracts:** Encourage customers to switch to 1- or 2-year contracts with incentives.
- **Improve Customer Support:** Invest in tech support and customer service to reduce dissatisfaction.
- **Target High-Risk Customers:** Use model churn probabilities to send personalized retention offers.
- **Flexible Billing Options:** Promote automatic payments and offer flexible billing to ease customer experience.
- **Monitor Monthly Charges:** Provide plans or discounts to customers with higher monthly charges to reduce churn risk.
- **Regular Model Updates:** Retrain models with new data regularly to capture changing customer behaviors.

9. Deliverables
- Jupyter Notebook containing:
  - Detailed EDA and preprocessing steps
  - Feature engineering process
  - Model training and hyperparameter tuning
  - Model evaluation and comparison
  - Model interpretation with SHAP/feature importance
- `report.md` summarizing the project, results, and business insights
- README.md explaining the project and usage instructions


