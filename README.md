# Student Performance Prediction Project

## Project Overview
This project aims to predict student performance (final grade G3) and classify students as 'Pass' or 'Fail' based on various demographic, social, and school-related features. The dataset is sourced from the UCI Machine Learning Repository, focusing on student performance in secondary education in two Portuguese schools.

## Key Steps:
1.  **Data Preprocessing**: Handling categorical features, creating a target variable for classification, and splitting data for training and testing.
2.  **Exploratory Data Analysis (EDA)**: Visualizing data distributions, correlations, and relationships between features and target variables.
3.  **Model Training**: Developing both regression and classification models to predict G3 and pass/fail status, respectively.
4.  **Feature Importance**: Identifying the most influential features for predictions.
5.  **Interactive Frontend**: A user-friendly interface to predict student performance based on input features.

## Data Preprocessing Summary
-   **Data Loading**: Used `ucimlrepo` to fetch the 'Student Performance' dataset.
-   **Target Variable Creation**: Created a binary `pass_fail` variable (1 for G3 >= 10, 0 otherwise).
-   **Handling Categorical Features**: Applied `LabelEncoder` for binary categorical variables and `pd.get_dummies` (one-hot encoding) for multi-category nominal variables.
-   **Data Splitting**: Split data into training and testing sets (80/20 ratio, `random_state=42`) for both regression (predicting G3) and classification (predicting pass/fail, with stratification).
-   **Feature Scaling**: Numerical features were scaled using `StandardScaler`.

## Exploratory Data Analysis (EDA) Summary
Key visualizations revealed:
-   Distribution of `G3` scores, showing common grade ranges.
-   Proportion of students passing vs. failing.
-   Correlation heatmap of numerical features, highlighting relationships.
-   Top 10 features most correlated with `G3` (excluding `G1` and `G2`), with `failures` showing a strong negative correlation and `higher` a positive one.
-   Box plots illustrated the impact of `studytime`, `failures`, and `absences` on `G3`.
-   Insights into gender-wise average `G3` and the influence of parental education levels.

## Model Architecture and Results

### Regression Models (Predicting G3)
-   **Models Evaluated**: Linear Regression, Random Forest Regressor, Gradient Boosting Regressor.
-   **Metrics**: Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R-squared (R2) score.
-   **Best Model**: **Gradient Boosting Regressor** achieved the highest R2 score of **0.2246**, indicating it best explains the variance in `G3`.

### Classification Models (Predicting Pass/Fail)
-   **Models Evaluated**: Logistic Regression, Random Forest Classifier, Gradient Boosting Classifier, Support Vector Machine (SVM).
-   **Metrics**: Accuracy, Precision, Recall, F1-score, and Confusion Matrix.
-   **Best Model**: **Support Vector Machine (SVM)** achieved the highest F1-score of **0.8966**, demonstrating a strong balance between precision and recall for classifying pass/fail status.

All trained models (`best_regression_model.joblib` and `best_classification_model.joblib`) were saved using `joblib`.

## Feature Importance Summary
-   **Random Forest Feature Importances**: For both regression and classification, `failures` consistently appeared as a highly important feature. For classification, `higher` (desire for higher education) and `school` also played significant roles.
-   **SHAP (SHapley Additive exPlanations) Summary Plot**: Generated for the best classification model (SVM), the SHAP plot provided deeper insights into how each feature influences the model's output, indicating which features drive predictions towards 'pass' or 'fail'.

## Interactive Frontend (ipywidgets)
An interactive user interface was developed using `ipywidgets` to allow real-time predictions based on user-inputted student information. This frontend:
-   Provides various input widgets (radio buttons, dropdowns, sliders) for student features.
-   Transforms input data to match model training format.
-   Uses the best regression model to predict `G3` and the best classification model to predict pass/fail status.
-   Displays predicted `G3`, pass/fail status, and classification confidence with a visual progress bar.

## Conclusion
This project successfully developed and evaluated machine learning models for student performance prediction. The Gradient Boosting Regressor and SVM were identified as the best-performing models for regression and classification tasks, respectively. Feature importance analysis provided valuable insights into critical factors influencing student outcomes. The interactive frontend serves as a practical tool for quick assessment, demonstrating the real-world application of the developed models.
