# 🏥 EHR Research-Readiness Prediction System

## 📌 Project Overview

This project implements a machine learning framework to predict whether Electronic Health Record (EHR) data is research-ready based on structured documentation features. The goal is to automate quality screening of EHR datasets and support healthcare research efficiency.

The system evaluates documentation density, clinical record completeness, and structured feature distributions to classify records into:

-  Research Ready
-  Not Research Ready

---

## 📊 Dataset Description

The dataset contains structured healthcare documentation metrics, including:

- Number of visits
- Number of observations
- Number of conditions
- Number of medications
- Number of procedures
- Derived ratio features (e.g., observations per visit)

Since a real research-ready label was not available, a constructed research-readiness indicator was generated using weighted feature scoring and controlled noise injection to simulate real-world variability.

---

## ⚙️ Methodology

### 1️⃣ Data Preprocessing
- Missing value handling
- Feature engineering (ratio-based features)
- Log transformation:
  
  X' = log(1 + X)

- Standardization (for Logistic Regression):

  Z = (X - μ) / σ

- Removal of identifier and derived variables to prevent data leakage
- Stratified train-test split (70%-30%)

---

### 2️⃣ Target Construction

A weighted richness score was computed:

R = w1·visits + w2·observations + w3·conditions + w4·medications + w5·procedures

Controlled Gaussian noise was added:

R' = R + ε

Binary classification label was generated using the median threshold.

---

### 3️⃣ Models Implemented

- Logistic Regression (L2 regularization, C=0.5)
- Decision Tree (max_depth=4)
- Random Forest (n_estimators=300, max_depth=4)

---

### 4️⃣ Model Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC Curve (AUC)
- 5-Fold Cross-Validation (Mean & Standard Deviation)

---


## 🔍 Key Insights

- Documentation density significantly influences research readiness.
- Linear relationships dominate predictive structure.
- Controlled noise prevented artificial separability.
- Cross-validation confirmed model stability.

---



