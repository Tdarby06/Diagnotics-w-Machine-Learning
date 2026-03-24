# 🔬 Automate Mechanical Biopsy Diagnostics with Machine Learning

## Overview

This project develops a supervised machine learning classification tool to predict whether breast tumor cells are **Malignant** or **Benign** using FNA biopsy data. The goal is to automate and improve the specificity and sensitivity of FNA diagnostics — reducing cost, time, and patient complication rates compared to Core Needle Biopsy (CNB).

---

## Problem Statement

Fine-Needle Aspiration (FNA) and Core Needle Biopsy (CNB) are two common, cost-effective biopsy techniques. While FNA is less invasive, its diagnostic accuracy has traditionally relied on manual interpretation. Key challenges include:

- Differentiating tumor cells with similar structure and size
- Reducing subjectivity and variability in diagnosis
- Scaling diagnostic throughput without increasing clinical burden

This project addresses these challenges by applying machine learning classification models to FNA tissue mass measurements.

---

## Dataset

The dataset contains FNA breast tissue mass measurements with **30 numeric predictor variables** computed from cell nuclei, across three categories:

| Category | Features |
|----------|----------|
| **Mean** | radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension |
| **Standard Error** | radius_se, texture_se, perimeter_se, area_se, smoothness_se, compactness_se, concavity_se, concave_points_se, symmetry_se, fractal_dimension_se |
| **Worst** | radius_worst, texture_worst, perimeter_worst, area_worst, smoothness_worst, compactness_worst, concavity_worst, concave_points_worst, symmetry_worst, fractal_dimension_worst |

**Target variable:** `diagnosis` — `M` (Malignant) or `B` (Benign)

---

## Exploratory Data Analysis

EDA was performed to understand distributions and separability between malignant and benign cases across all 30 features. Boxplot visualizations revealed clear distributional differences in many features (e.g., radius, area, concavity), confirming strong predictive signal in the dataset.

---

## Models

Four supervised classification algorithms were implemented and compared:

| Model | Description |
|-------|-------------|
| **Decision Tree** | Partitions data into malignant/benign branches based on predictor variable thresholds |
| **Random Forest** | Ensemble of decision trees trained on random data/feature subsets; predictions aggregated for final output |
| **K-Nearest Neighbors (KNN)** | Classifies new samples based on proximity to known training clusters |
| **Logistic Regression** | Models the log-odds of malignancy (1) vs. benign (0) as a linear function of predictors |

---

## Results

All models were evaluated on **Accuracy**, **Sensitivity** (true positive rate — malignant correctly identified), and **Specificity** (true negative rate — benign correctly identified).

| Metric | Decision Tree | Random Forest | KNN | Logistic Regression |
|--------|:---:|:---:|:---:|:---:|
| **Accuracy** | 92.11% | **97.37%** | 95.61% | 92.98% |
| **Sensitivity** | 96.88% | **100%** | 93.75% | 90.62% |
| **Specificity** | 90.24% | **96.34%** | 96.34% | 93.90% |

### ✅ Recommended Model: Random Forest

The Random Forest model achieved the highest performance across all three metrics, including **100% sensitivity** — meaning zero malignant tumors were missed in testing. Random Forest parameter tuning confirmed stable performance across varying numbers of predictors (stabilizing beyond ~15 predictors).

> Using practical ML classification techniques, we assert there is a successful pathway for FNA prediction yielding specificity and sensitivity results **above 96%**.

---
