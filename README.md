# Air Quality Prediction Using Machine Learning

## 1. Problem Statement
This project predicts carbon monoxide concentration (CO(GT))
using air-quality sensor measurements and machine learning
regression algorithms.

## 2. Dataset
Source: UCI Machine Learning Repository - Air Quality Dataset
https://archive.ics.uci.edu/dataset/360/air+quality

Original dataset: 9,357 records and 15 columns.
After removing records with missing target values, 7,674 records
were available for model training and evaluation.

## 3. Technologies Used
- Python
- Pandas and NumPy
- Scikit-learn
- Matplotlib and Seaborn
- Joblib
- Jupyter Notebook

## 4. Methodology
1. Loaded and explored the dataset.
2. Replaced -200 sensor readings with missing values.
3. Removed rows where the target CO(GT) was missing.
4. Created an Hour feature from the recorded Time.
5. Grouped hours into Night, Morning, Afternoon and Evening.
6. Applied one-hot encoding to the TimeOfDay feature.
7. Split the data into 80% training and 20% testing.
8. Used median imputation for missing numeric input values.
9. Trained a mean baseline, Linear Regression and Random Forest.
10. Evaluated models using MAE, RMSE and R-squared.
11. Used 5-fold cross-validation to assess model performance.
12. Used permutation importance to examine feature contributions.
13. Saved the selected model, evaluation results and charts.

## 5. Data Preprocessing and Feature Engineering
- Replaced invalid -200 sensor readings with missing values.
- Removed rows with missing target values.
- Used median imputation for missing input features.
- Excluded CO(GT) from the input features to prevent target leakage.
- Extracted Hour from Time and created a TimeOfDay category.
- Used one-hot encoding to convert TimeOfDay categories into numeric
  columns suitable for machine learning.
- StandardScaler was used in the separate Linear Regression
  preprocessing pipeline, if that pipeline was executed successfully.
- Random Forest does not normally require feature scaling.

## 6. Model Comparison

                      MAE    RMSE      R2
Baseline           1.1155  1.4448 -0.0022
Linear Regression  0.2892  0.4549  0.9006
Random Forest      0.2303  0.3689  0.9347

## 7. Best Model
Selected model: Random Forest

MAE: 0.2303
RMSE: 0.3689
R-squared: 0.9347

The model with the lowest test RMSE was selected as the best model.
The mean baseline provides a reference for measuring improvement.

## 8. Cross-Validation
Five-fold cross-validation was performed using a Random Forest
regression pipeline on the training data.

Latest recorded RMSE scores:
- Fold 1: 0.4374
- Fold 2: 0.4385
- Fold 3: 0.3937
- Fold 4: 0.4105
- Fold 5: 0.3826

Mean cross-validation RMSE: 0.4126
Standard deviation: 0.0226

The mean RMSE summarizes performance across the five folds.
The standard deviation indicates variation between fold scores.

Note: These cross-validation values must be refreshed if the
features or training data have changed since they were calculated.

## 9. Feature Importance
Permutation importance estimates how much prediction performance
changes when an input feature is shuffled.

The feature-importance chart identifies the most useful features
for prediction in the evaluated model. Importance indicates
predictive usefulness, not causation.

## 10. Evaluation Charts
- outputs/model_comparison.png: compares model performance.
- outputs/actual_vs_predicted.png: compares actual and predicted values.
- outputs/residuals.png: displays prediction errors.
- outputs/feature_importance.png: displays permutation importance.

## 11. Saved Model and Results
- models/best_air_quality_model.joblib: selected best model.
- models/scaled_linear_regression.joblib: scaled Linear Regression
  model, if it was saved by the notebook.
- outputs/model_comparison.csv: model evaluation results.
- outputs/feature_importance.csv: feature-importance results.

- The trained Random Forest model is saved locally as `models/best_air_quality_model.joblib`. Because the file exceeds GitHub's browser upload limit, it is not included in this repository upload. Run the notebook to retrain the model and generate the saved file.

## 12. Limitations and Assumptions
- Missing sensor readings may affect prediction quality.
- Median imputation assumes the median is a reasonable replacement
  for missing input measurements.
- TimeOfDay is a simplified grouping and does not capture every
  temporal pattern.
- A random train-test split does not measure future forecasting
  performance.
- Cross-validation on training data does not replace independent
  external testing.
- Performance may decrease when sensor conditions differ from
  those represented in the training dataset.
- Extreme pollution levels or unusual sensor readings may produce
  larger prediction errors.
- This model is for educational purposes and is not a validated
  real-time pollution monitoring or warning system.

## 13. Conclusion
The project compares a mean baseline, Linear Regression and
Random Forest for predicting CO(GT). Evaluation metrics, residual
analysis and feature importance help assess model performance.
Time-based validation and external testing are recommended before
any real-world deployment.
