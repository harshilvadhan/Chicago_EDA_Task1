Chicago Crime Dataset — EDA & Classification Model

Exploratory Data Analysis and a classification model on a sample of the Chicago crime dataset, completed as ML Task 1 (EDA) and ML Task 2 (Classification Model Development) for the Technical and ML enrollment track (S4DS).

Author: Harshil Vadhan (Roll No. D061, SAP ID 60009250122)

Overview

This project analyzes ~12,500 crime records from Chicago to understand data quality and crime patterns (Task 1), then builds a classification model predicting whether a reported crime results in an arrest (Task 2).

Contents
File	Description
chicago_eda.ipynb	Full Jupyter notebook: Task 1 (data quality checks, univariate & bivariate analysis, temporal/location patterns) followed by Task 2 (feature engineering, model building, evaluation, cross-validation)
chicago_crime_dataset.csv	Source dataset used for the analysis
Task 1: Exploratory Data Analysis — Key Findings
Data quality: No duplicate records, no Year/Date inconsistencies, no invalid coordinates. Missing location data (~1.4%) is concentrated in NARCOTICS and DECEPTIVE PRACTICE cases(not random).
Arrest rate varies enormously by crime type (9%–100%), driven by how a crime is typically discovered rather than its severity.
Temporal patterns: Crime dips sharply overnight (3–6 AM); apparent peaks at midnight/noon are largely a data-logging artifact from imprecise timestamps rather than true behavioral spikes.
Location patterns: Crime is moderately concentrated across districts. District-level arrest rate correlates weakly with crime volume (r = -0.23) — it's driven more by crime-type mix than by how much crime occurs there.
Task 2: Classification Model — Key Results

Goal: Predict whether a reported crime results in an arrest (Arrest: True/False).

Features used: Primary Type, District, Domestic, Hour, DayOfWeek, Month, Location Description — selected and engineered based on Task 1 findings. Redundant location columns (Ward, Beat, Community Area) were dropped in favor of District alone to avoid diluting the location signal.

Approach:

Stratified 80/20 train/test split to preserve the 33.5% arrest rate in both sets
Leak-free preprocessing pipeline (one-hot encoding fit only on training data)
Two models trained: Logistic Regression (linear baseline) and Random Forest
Evaluated on precision, recall, F1, and ROC-AUC (accuracy alone is misleading given class imbalance)
Validated with 5-fold stratified cross-validation

Results:

Model	Mean ROC-AUC (5-fold CV)	Recall (Arrest)	Precision (Arrest)
Logistic Regression	0.842	0.51	0.78
Random Forest (final)	0.850	0.40	0.91

Final model: Random Forest — chosen for its consistently higher ROC-AUC across all CV folds and its ability to capture non-linear feature interactions (e.g. District's effect on arrest is mediated by its crime-type mix, not a standalone effect). Logistic Regression remains a reasonable alternative if recall on the Arrest class is the priority.

Full details, code, and visualizations are in the notebook.

Tools

Python, pandas, scikit-learn, matplotlib, seaborn, Jupyter Notebook
