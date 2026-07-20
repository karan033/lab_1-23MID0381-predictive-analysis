# lab_1-23MID0381-predictive-analysis
```markdown
# House Price Prediction using Linear Regression

## Overview
This repository contains the code, analysis, and report for predicting median district house values using the California Housing dataset[cite: 1, 2]. Developed as part of the "Advanced Predictive Analytics" (Lab 01) coursework, this project builds a reproducible, leakage-safe machine-learning workflow to estimate property values based on attributes such as median income, house age, and geographical location[cite: 1, 2].

## Datasets
This project audits and utilizes two datasets to satisfy multi-dataset requirements[cite: 1, 2]:
*   **California Housing Dataset (Primary):** Contains 20,640 samples and 8 numeric predictors[cite: 1, 2]. The target variable is the continuous median house value for California census blocks[cite: 1, 2].
*   **UCI Real Estate Valuation (Secondary):** Contains 414 instances and 6 predictors, targeting the house price per unit area in Sindian Dist., New Taipei[cite: 1, 2].

## Project Workflow
The analysis strictly follows an end-to-end predictive analytics pipeline[cite: 2]:
1.  **Environment Setup & Data Loading:** Establishing a reproducible environment with a fixed random seed (42) and loading the datasets[cite: 1, 2].
2.  **Data Audit & Splitting:** Performing data quality checks and creating an 80/20 train-test holdout split prior to any data transformations[cite: 1].
3.  **Exploratory Data Analysis (EDA):** Visualizing target distributions and numerical correlations exclusively on the training set to prevent data leakage[cite: 1, 2].
4.  **Preprocessing Pipeline:** Building a reusable `scikit-learn` pipeline integrating `SimpleImputer` (median strategy) and `StandardScaler` for numerical features, and `OneHotEncoder` for categoricals[cite: 1].
5.  **Baseline Modeling:** Establishing a naive mean-prediction baseline and a Simple Linear Regression baseline utilizing the strongest predictor, median income (`MedInc`)[cite: 1].
6.  **Model Comparison:** Evaluating models using 5-fold cross-validation (`KFold`) strictly on the training set[cite: 1].
7.  **Hyperparameter Tuning:** Tuning the Ridge regression model using `GridSearchCV`[cite: 1].
8.  **Diagnostics & Analysis:** Conducting an ablation study applying a target log transformation, calculating segment-level errors (by price brackets and coastal/inland location), and performing residual analysis[cite: 1].

## Models Evaluated
The following regression models were implemented and compared[cite: 1]:
*   Linear Regression[cite: 1]
*   Ridge Regression[cite: 1]
*   Lasso Regression[cite: 1]
*   Decision Tree Regressor[cite: 1]
*   Random Forest Regressor[cite: 1]

## Key Results
The **Random Forest Regressor** was selected as the final model, as it significantly outperformed the linear baselines and effectively captured non-linear spatial interactions[cite: 1, 2]. 
*   **Test MAE:** 0.326[cite: 1]
*   **Test RMSE:** 0.504[cite: 1]
*   **Test R²:** 0.806[cite: 1]

The Random Forest model reduced the RMSE by approximately 56% compared to the naive mean-prediction baseline (RMSE: 1.145)[cite: 1, 2]. Segment-level analysis demonstrated that the model performs well on low/medium-priced homes (RMSE: 0.382) but struggles with highly-priced properties (RMSE: 0.760) due to a hard cap (target censoring) at the 5.0 mark in the raw dataset[cite: 1, 2].

## Repository Structure
*   `lab_01_23MID0381_Predictive_Analysis.ipynb`: The primary Jupyter Notebook containing the end-to-end execution of the modeling workflow[cite: 1].
*   `REGNO_Lab01_Results.csv`: Exported final test results and model comparisons[cite: 1].
*   `cross_validation_results.csv`: Exported 5-fold CV metrics[cite: 1].
*   `ablation_results.csv`: Evaluation metrics comparing the baseline Random Forest to a log-transformed variant[cite: 1].
*   `segment_results.csv`: Error metrics broken down by price thresholds and geographical location[cite: 1].
*   `REGNO_Lab01_Model.joblib`: The serialized, deployment-ready Random Forest pipeline[cite: 1].
*   `run_metadata.json`: Metadata tracking the random seed, dataset shape, and selected model[cite: 1].

## Dependencies
To run this notebook, the following environment/libraries are required[cite: 1]:
*   Python 3.12.13[cite: 1]
*   pandas 2.2.2[cite: 1]
*   scikit-learn 1.6.1[cite: 1]
*   numpy[cite: 1]
*   matplotlib[cite: 1]
*   seaborn[cite: 1]
*   joblib[cite: 1]

```
