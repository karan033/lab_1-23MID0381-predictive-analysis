# lab_1-23MID0381-predictive-analysis

# House Price Prediction using Linear Regression

![Python](https://img.shields.io/badge/Python-3.12.13-blue.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.6.1-orange.svg)
![pandas](https://img.shields.io/badge/pandas-2.2.2-green.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

> **Advanced Predictive Analytics (Lab 01)**
> An end-to-end, reproducible, and leakage-safe machine learning workflow to estimate property values based on attributes such as median income, house age, and geographical location.

---

## Table of Contents
1. [Overview](#overview)
2. [Datasets](#datasets)
3. [Project Workflow](#project-workflow)
4. [Models Evaluated](#models-evaluated)
5. [Key Results](#key-results)
6. [Repository Structure](#repository-structure)


---

## Overview
This repository contains the code, exploratory data analysis (EDA), and technical reporting for predicting median district house values. The goal of this project is to provide automated valuation estimates and property rankings for price discovery, establishing a robust statistical baseline while evaluating more complex, non-linear ensemble models.

## Datasets
To satisfy multi-dataset diagnostic requirements, two datasets were audited and utilized:

*   **California Housing Dataset (Primary):** 
    *   **Size:** 20,640 samples, 8 numeric predictors. 
    *   **Target:** Continuous median house value per census block.
*   **UCI Real Estate Valuation (Secondary):** 
    *   **Size:** 414 instances, 6 predictors. 
    *   **Target:** House price per unit area (Sindian Dist., New Taipei).

## Project Workflow
The analysis strictly adheres to an industry-standard predictive analytics pipeline:

1.  **Environment Setup:** Established a reproducible environment using a fixed random seed (`SEED = 42`).
2.  **Holdout Design:** Created an 80/20 train-test split prior to any data transformations to prevent data leakage.
3.  **Exploratory Data Analysis (EDA):** Visualized target distributions and feature correlations strictly on the training partition.
4.  **Preprocessing Pipeline:** Engineered a reusable `scikit-learn` `ColumnTransformer` integrating `SimpleImputer` (median) and `StandardScaler` for numerical data, alongside `OneHotEncoder` for categoricals.
5.  **Baseline Modeling:** Deployed a naive mean-prediction baseline and a Simple Linear Regression model using the strongest predictor (`MedInc`).
6.  **Validation & Tuning:** Evaluated models using 5-fold cross-validation (`KFold`) on the training set and tuned Ridge regression using `GridSearchCV`.
7.  **Diagnostics:** Conducted an ablation study (target log transformation), evaluated segment-level errors (by price and geography), and performed residual analysis.

## Models Evaluated
The following models were implemented and compared under identical validation protocols:
*   Linear Regression (Simple & Multiple)
*   Ridge Regression (L2 Regularization)
*   Lasso Regression (L1 Regularization)
*   Decision Tree Regressor
*   Random Forest Regressor

## Key Results
The **Random Forest Regressor** was selected as the final model as it significantly outperformed linear baselines by capturing non-linear spatial interactions.

### Final Test Metrics (Random Forest)
| Metric | Score | Note |
| :--- | :--- | :--- |
| **Test MAE** | `0.326` | Average absolute error in predictions. |
| **Test RMSE** | `0.504` | Penalizes larger valuation errors. |
| **Test R²** | `0.806` | Variance explained by the model. |

**Major Insights:**
*   **Baseline Improvement:** The tuned Random Forest model reduced the RMSE by approximately **56%** relative to the naive mean-prediction baseline (RMSE: 1.145).
*   **Segment Performance:** The model accurately predicts low/medium-priced homes (RMSE: 0.382) but struggles with highly-priced properties (RMSE: 0.760) due to a hard cap (target censoring) at the 5.0 mark in the raw dataset.

## Repository Structure

```text
House-Price-Prediction/
├── lab_01_23MID0381_Predictive_Analysis.ipynb  # Primary Jupyter Notebook
└── README.md                                   # Project documentation
