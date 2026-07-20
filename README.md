# lab_1-23MID0381-predictive-analysis

# House Price Prediction using Linear Regression

![Python](https://img.shields.io/badge/Python-3.12.13-blue.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.6.1-orange.svg)
![pandas](https://img.shields.io/badge/pandas-2.2.2-green.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

> **Advanced Predictive Analytics (Lab 01)**
> An end-to-end, reproducible, and leakage-safe machine learning workflow for estimating residential property values using statistical and machine learning models.

---

## Table of Contents

1. [Overview](#overview)
2. [Datasets](#datasets)
3. [Project Workflow](#project-workflow)
4. [Models Evaluated](#models-evaluated)
5. [Key Results](#key-results)
6. [Repository Structure](#repository-structure)
7. [How to Run](#how-to-run)

---

## Overview

This repository contains the implementation, exploratory data analysis (EDA), and technical reporting for predicting median district house values. The project follows a complete predictive analytics workflow, beginning with data exploration and preprocessing, progressing through baseline and advanced model development, and concluding with rigorous evaluation and diagnostic analysis.

Special emphasis is placed on reproducibility, prevention of data leakage, fair model comparison, and interpretable performance evaluation.

---

## Datasets

To satisfy the multi-dataset diagnostic requirements, two housing datasets were utilized.

### California Housing Dataset (Primary)

* **Samples:** 20,640
* **Features:** 8 numerical predictors
* **Target:** Median house value for each California census block

### UCI Real Estate Valuation Dataset (Secondary)

* **Samples:** 414
* **Features:** 6 predictors
* **Target:** House price per unit area (Sindian District, New Taipei City)

---

## Project Workflow

The project follows an industry-standard machine learning pipeline.

1. Established a reproducible environment using a fixed random seed (`SEED = 42`).
2. Performed an 80/20 train-test split before any preprocessing to eliminate data leakage.
3. Conducted exploratory data analysis (EDA) exclusively on the training data.
4. Built preprocessing pipelines using `ColumnTransformer`, `SimpleImputer`, `StandardScaler`, and `OneHotEncoder`.
5. Implemented baseline models including:

   * Naïve Mean Predictor
   * Simple Linear Regression
6. Trained and compared multiple regression algorithms.
7. Performed hyperparameter tuning using `GridSearchCV`.
8. Evaluated models with 5-fold cross-validation.
9. Conducted residual analysis, ablation studies, and segment-wise error analysis.
10. Selected the best-performing model based on unseen test-set performance.

---

## Models Evaluated

The following regression models were implemented and evaluated under identical validation protocols.

* Linear Regression (Simple)
* Multiple Linear Regression
* Ridge Regression
* Lasso Regression
* Decision Tree Regressor
* Random Forest Regressor

---

## Key Results

The **Random Forest Regressor** achieved the best predictive performance by effectively capturing non-linear relationships between housing characteristics and property values.

### Final Test Performance

| Metric       |   Score   | Description                        |
| :----------- | :-------: | :--------------------------------- |
| **MAE**      | **0.326** | Average absolute prediction error  |
| **RMSE**     | **0.504** | Penalizes larger prediction errors |
| **R² Score** | **0.806** | Proportion of variance explained   |

### Major Findings

* The final Random Forest model reduced RMSE by approximately **56%** compared to the naïve mean baseline (RMSE = 1.145).
* Ensemble methods consistently outperformed linear models due to their ability to capture complex, non-linear relationships.
* Prediction accuracy remained strong for low- and medium-priced homes but deteriorated for expensive properties because of target-value censoring at **5.0** in the California Housing dataset.
* Cross-validation demonstrated stable generalization performance with minimal variance across folds.

---

## Repository Structure

```text
House-Price-Prediction/
├── lab_01_23MID0381_Predictive_Analysis.ipynb   # Complete predictive analytics workflow
└── README.md                                   # Project documentation
```

---

## How to Run

### Prerequisites

The project was developed and tested using the following software versions.

| Software     | Version |
| :----------- | :-----: |
| Python       | 3.12.13 |
| pandas       |  2.2.2  |
| scikit-learn |  1.6.1  |

Install the required dependencies using:

```bash
pip install pandas==2.2.2 scikit-learn==1.6.1 numpy matplotlib seaborn joblib
```

### Running the Project

1. Clone or download this repository.

2. Open the notebook:

```text
lab_01_23MID0381_Predictive_Analysis.ipynb
```

using **Jupyter Notebook**, **JupyterLab**, or **Google Colab**.

3. Execute **Restart Kernel and Run All Cells** (or simply **Run All**) to reproduce the complete workflow.

The notebook will automatically perform:

* Data loading
* Exploratory Data Analysis (EDA)
* Data preprocessing
* Model training
* Hyperparameter tuning
* Cross-validation
* Residual diagnostics
* Model evaluation

No additional configuration is required.

---

## License

This project was developed as part of the **Advanced Predictive Analytics (Lab 01)** coursework and is intended for educational purposes.
