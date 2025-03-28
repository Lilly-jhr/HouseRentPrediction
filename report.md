# USA House Price Prediction Report

## 1. Problem Statement

The goal of this project is to develop a predictive model for house prices in the USA, leveraging a dataset with various property features. Accurate house price prediction is crucial for both buyers and sellers, enabling informed decisions regarding investment, pricing strategies, and overall market analysis. This report summarizes the data preprocessing steps, model development (including hyperparameter tuning for the Random Forest model), comparison of multiple regression models, and key insights derived from the analysis.

## 2. Data Preprocessing

The dataset underwent the following preprocessing steps:

*   **Missing Value Handling:** Numerical features with missing values were imputed using the mean of the respective columns. Rows with missing values in categorical features were dropped for simplicity.
*   **Feature Engineering:**
    *   `price_per_sqft`: Calculated the price per square foot by dividing the price by the living area, providing a normalized measure of property value.
    *   `age`: Determined the age of the property by subtracting the year built from the current year (2024).
    *   `renovation_age`: Calculated the time since the last renovation (or 0 if never renovated).
    *   `renovation_status`: Created a binary categorical feature indicating whether the property has been renovated.
    *   `basement_status`: Created a binary categorical feature indicating whether the property has a basement.
*   **Feature Transformation:**
    *   Numerical features were standardized using `StandardScaler` to ensure they have a mean of 0 and a standard deviation of 1.
    *   Categorical features were one-hot encoded using `OneHotEncoder` to convert them into a numerical format suitable for the models.

## 3. Model Comparison and Hyperparameter Tuning

The following regression models were trained and evaluated:

*   **Linear Regression:** A simple linear model used as a baseline, without hyperparameter tuning.
*   **Random Forest:** An ensemble of decision trees, robust to non-linear relationships and outliers. Hyperparameter tuning was performed using `GridSearchCV`. The following hyperparameters were tuned:
    *   `n_estimators`: Number of trees in the forest (values: [50, 100, 150]).
    *   `max_depth`: Maximum depth of the trees (values: [5, 10, 15]).
    *   `min_samples_split`: Minimum number of samples required to split an internal node (values: [2, 4, 6]).
    3-fold cross-validation was used to select the best combination of hyperparameters.
*   **XGBoost:** A gradient boosting algorithm, known for its high performance and ability to capture complex patterns.

The models were evaluated using the following metrics on the test set:

| Model              | RMSE      | R²        | MAE       |
| ------------------ | --------- | --------- | --------- |
| Linear Regression  | 64996.524 | 0.922     | 43211.740 |
| Random Forest      | 14750.388 | 0.996     | 6639.686  |
| XGBoost            | 17843.393 | 0.994     | 10502.448 |

The Random Forest model achieved superior performance, with an R-squared of 0.996 and the lowest RMSE and MAE, due to the effective hyperparameter tuning and its ability to capture complex non-linear relationships in the data.

## 4. Key Insights

*   **Most Important Features:** price_per_sqft and sqft_lot
*   **Hyperparameter Tuning Impact:** Tuning the `n_estimators`, `max_depth`, and `min_samples_split` parameters in Random Forest significantly improved the model's performance compared to the baseline Linear Regression.
*   **Model Selection:** The Random Forest model outperformed Linear Regression and XGBoost in this specific scenario, likely due to its better ability to handle the data's non-linearity and the effectiveness of the hyperparameter tuning.

### Limitations

*   This analysis is based on a specific dataset, and the results may not generalize to different regions or time periods.
*   Only the Random Forest model was hyperparameter tuned. Tuning XGBoost might lead to further improvements.
*   The range of hyperparameters explored during tuning was limited and may not have found the absolute optimal configuration.
