# Loan Default Risk Prediction

## Overview

In consumer lending, every approved loan carries financial risk. When borrowers fail to repay, lenders face direct losses and long-term instability. Machine learning can help predict borrower risk before loan approval, enabling smarter lending decisions.

This project builds classification models to predict whether a borrower will:

- Fully repay a loan  
- Default (charged-off)

The goal is to reduce financial risk while supporting fair and responsible credit access.

---

## Business Objective

Defaulted loans increase losses and threaten lending sustainability.  
The core prediction task is a binary classification:

**Will a borrower fully repay the loan, or default?**

This model supports:

- risk reduction
- data-driven approvals
- improved lending fairness
- sustainable credit access

---

## Dataset

**File:** `loan_data.csv`  
**Rows:** 9,578  
**Features:** 14 borrower financial and credit attributes  

### Target Variable
- `not.fully.paid`
  - 0 = fully repaid
  - 1 = defaulted

### Key Features
- FICO score
- Debt-to-income ratio (DTI)
- Revolving credit utilization
- Credit history length
- Delinquencies
- Recent credit inquiries
- Loan purpose

---

## Exploratory Data Analysis

Correlation analysis and distribution plots revealed meaningful relationships between borrower attributes and loan outcomes.

### Key Insights
- Higher **debt-to-income ratio** increases default likelihood
- Higher **revolving credit utilization** correlates with risk
- Lower **FICO scores** strongly relate to default
- Some loan purposes (e.g., small business) show higher risk

These findings validate the relevance of selected features.

---

## Data Preparation

### Cleaning & Feature Selection
- Removed multicollinear or redundant features
- Encoded loan purpose using one-hot encoding
- Scaled numeric features
- Stratified train/test split to handle class imbalance

---

## Modeling Approach

### Models Evaluated
- Logistic Regression
- Random Forest Classifier
- XGBoost Classifier

### Evaluation Metrics
- Accuracy
- Precision & Recall
- ROC-AUC
- Confusion Matrix

ROC-AUC is emphasized because it measures risk-ranking ability, critical in lending decisions.

---

## Model Performance

### Logistic Regression (Tuned)
- Accuracy: **0.64**
- ROC-AUC: **0.67**
- Recall (defaults): **0.55**

**Insight:**  
Good at detecting risky borrowers but flags many safe borrowers as high risk.

---

### Random Forest (Tuned)
- Accuracy: **0.77**
- ROC-AUC: **0.67**
- Recall (defaults): **0.34**
- Higher precision for high-risk predictions

**Insight:**  
More selective and confident when identifying risky borrowers.

---

### XGBoost
- Accuracy: **0.66**
- ROC-AUC: **0.66**
- Recall (defaults): **0.55**

**Insight:**  
Detects risky borrowers well but offers limited improvement over simpler models.

---

## Feature Importance (Random Forest)

Top drivers of default risk:

- Revolving credit utilization
- FICO score
- Credit history length
- Debt-to-income ratio
- Recent credit inquiries

These align with real-world credit risk practices.

---

## Model Comparison Summary

| Model | Accuracy | ROC-AUC | Default Detection | Key Strength |
|------|------|------|------|------|
| Logistic Regression | 0.64 | 0.67 | High | Catches risky borrowers early |
| Random Forest | **0.77** | 0.67 | Moderate | Best balance & precision |
| XGBoost | 0.66 | 0.66 | High | Good recall, complex |

**Selected Model:** Random Forest  
Provides the best balance between risk control and business value.

---

## Example Predictions

Three hypothetical borrowers were evaluated:

| Borrower | Default Risk | Approval | Insight |
|----------|-------------|----------|--------|
| A | Low | Approved | Safe borrower |
| B | High | Re jected | High risk |
| C | Medium-High | Conditional | Monitor risk |

The model enables flexible decisions such as:

- conditional approvals
- adjusted interest rates
- additional verification

---

## Technologies Used

- Python  
- Pandas & NumPy  
- Matplotlib & Seaborn  
- Scikit-learn  
- XGBoost  

---

## Business Impact

This model helps lenders:

- reduce default losses
- improve approval accuracy
- balance risk and accessibility
- support responsible lending
- enhance decision transparency

---

## Limitations

- ROC-AUC ~0.67 indicates moderate predictive power
- Dataset lacks behavioral repayment history
- External economic factors are not included
- Threshold selection impacts approval fairness

---

## Future Improvements

- Incorporate repayment behavior & transaction history
- Add macroeconomic indicators
- Test gradient boosting ensembles & calibration
- Optimize decision thresholds for fairness & profitability
- Monitor model performance over time

---

## How to Run

### Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```

---

## Key Insights

- Borrowers with high debt-to-income ratios and credit utilization are more likely to default.
- Lower FICO scores strongly increase repayment risk.
- Random Forest provided the best balance between detecting risk and approving safe borrowers.
- Risk scoring enables flexible actions such as conditional approvals or adjusted interest rates.
