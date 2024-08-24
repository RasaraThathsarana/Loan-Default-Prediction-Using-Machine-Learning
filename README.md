# Loan Default Prediction Using Machine Learning

## CS3111 - Introduction to Machine Learning
### Lab 01 - Feature Engineering
#### Dr. R.T. Uthayasanker | February 16, 2024
#### Index: 210170G | Name: W.A.R.T. Fonseka

- [Lab Report](210170G_report.pdf)
- [Python Notebook](210170G_notebookipynb)
- you can find dataset here [here](https://drive.google.com/drive/folders/13ia5PyRPJiJ3571jJ-j17xXgc-MWQkSX?usp=sharing)

## Project Overview
This project is part of the **CS3111 - Introduction to Machine Learning** course. The objective of this lab is to build a machine learning model to predict loan defaults using a dataset provided by a finance company in the United States. The primary focus is on feature engineering, data preprocessing, and model development using the XGBoost algorithm.

## Dataset
The dataset includes information on previous loan applicants and whether they defaulted or not. The data is split into three files:
- `train.csv`: Training data with 145 features.
- `valid.csv`: Validation data for model evaluation.
- `X_test.csv`: Test data for final predictions (without target labels).

## Steps in the Project

### 1. Data Cleaning
- **Duplicate Removal**: Ensured no duplicate rows were present in the training data.
- **Missing Value Handling**: Removed features with more than 50% missing values, reducing features from 145 to 87.
  - Filled missing values using domain-specific methods, including calculated values and specific indicators like `-1` or `Jan-1960` for datetime features.
- **Data Transformation**: Converted certain features, like `issue date` to `issue year` and calculated elapsed time from datetime features.

### 2. Feature Encoding
- **Label Encoding**: Applied to features such as `term`, `home_ownership`, `purpose`, etc.
- **Ordinal Encoding**: Applied to features such as `sub_grade`, `emp_length`, and `verification_status`.
- **Custom Encoding**: Encoded features like `Employer Title` and `title` based on their presence or absence.

### 3. Correlated Feature Removal
- Removed highly correlated features, reducing the feature count further to 57.

### 4. Feature Selection
- Used Recursive Feature Elimination (RFE) to select the 8 most important features:
  1. `loan_amnt`
  2. `term`
  3. `issue_d`
  4. `total_rec_late_fee`
  5. `recoveries`
  6. `last_pymnt_d`
  7. `last_pymnt_amnt`
  8. `debt_settlement_flag`

### 5. Model Development
- Developed an XGBoost Classifier model.
- Applied GridSearchCV for hyperparameter tuning, achieving optimal values:
  - `colsample_bytree`: 0.9
  - `learning_rate`: 0.3
  - `max_depth`: 6
  - `n_estimators`: 200
  - `subsample`: 0.9

### 6. Model Evaluation
- Achieved an accuracy of 99% on the validation dataset.

### 7. SHAP Analysis for Explainable AI
- Used SHAP (SHapley Additive exPlanations) to interpret the model's predictions.
- Visualized feature contributions with waterfall and bar plots.

## Conclusion
The project successfully built a robust machine learning model with high accuracy for predicting loan defaults. Through rigorous feature engineering and data preprocessing, the model was able to generalize well to unseen data. The SHAP analysis provided insights into the model's decision-making process, ensuring transparency and interpretability.

## Files in the Repository
- **`train.csv`**: Training data file.
- **`valid.csv`**: Validation data file.
- **`X_test.csv`**: Test data file.
- **`DataDictionary.xlsx`**: Data dictionary providing details on the features.
- **`Lab_Report.pdf`**: Detailed report on the feature engineering and model development process.

## Usage
To reproduce the results, you can follow the steps in the provided Jupyter notebook (`Lab_Report.ipynb`). Ensure you have the necessary libraries installed (e.g., XGBoost, SHAP).

## License
This project is for educational purposes and follows the guidelines set by the course instructor.
