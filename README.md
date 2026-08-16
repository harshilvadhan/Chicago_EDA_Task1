# Chicago Crime Dataset — Exploratory Data Analysis

Exploratory Data Analysis (EDA) on a sample of the Chicago crime dataset, completed as **ML Task 1**.

**Created by:** Harshil Vadhan (Roll No. D061, SAP ID 60009250122)

## Overview

This project analyzes ~12,500 crime records from Chicago to understand data quality, crime patterns, and the relationship between crime type and arrest outcomes — laying the groundwork for a classification model (Task 2) that predicts whether a reported crime results in an arrest.

## Contents

| File | Description |
|---|---|
| `chicago_eda.ipynb` | Full Jupyter notebook: data quality checks, univariate & bivariate analysis, temporal and location-based patterns, with code and inline commentary |
| `chicago_crime_dataset.csv` | Source dataset used for the analysis |

## Key Findings

- **Data quality:** No duplicate records, no Year/Date inconsistencies, no invalid coordinates. Missing location data (~1.4%) is concentrated in `NARCOTICS` and `DECEPTIVE PRACTICE` cases — not random.
- **Arrest rate varies enormously by crime type** (9%–100%), driven by how a crime is typically discovered rather than its severity. `Primary Type` is the strongest expected predictor for arrest classification.
- **Temporal patterns:** Crime dips sharply overnight (3–6 AM); apparent peaks at midnight/noon are largely a data-logging artifact from imprecise timestamps rather than true behavioral spikes.
- **Location patterns:** Crime is moderately concentrated across districts. District-level arrest rate correlates weakly with crime volume (r = -0.23) — it's driven more by crime-type mix than by how much crime occurs there.

Full details and supporting visualizations are in the notebook.

## Tools

Python, pandas, matplotlib, seaborn, Jupyter Notebook

## Next Steps

This EDA feeds into **ML Task 2**: a classification model predicting arrest outcome, using engineered features informed by the patterns found here (crime type, time-of-day binning, day-of-week, district).
