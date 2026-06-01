# Week-4-Credit-Risk-Probability-Model-for-Alternative-Data---Interim-Submission
# Credit Risk Probability Model for Alternative Data

## Project Overview

This project aims to develop an end-to-end credit risk scoring system for Bati Bank in partnership with an eCommerce platform. The objective is to enable a Buy-Now-Pay-Later (BNPL) service by assessing the likelihood that a customer will default on future credit obligations.

Since the available transaction dataset does not contain a direct default label, the project will construct a proxy risk target using customer behavioral patterns derived from transaction history. The resulting model will estimate risk probability, generate a credit score, and support future loan approval and pricing decisions.

---

# Business Problem

Bati Bank intends to expand its digital lending capabilities by offering credit to eCommerce customers. Traditional credit scoring models rely on historical loan repayment records; however, such information is unavailable in this dataset.

Therefore, the challenge is to extract meaningful risk signals from transaction behavior and develop a predictive system capable of identifying high-risk and low-risk customers.

The final solution should support:

* Credit approval decisions
* Credit limit determination
* Loan pricing strategies
* Risk monitoring and portfolio management

---

# Credit Scoring Business Understanding

## 1. Basel II and Model Interpretability

The Basel II Accord emphasizes risk measurement, transparency, documentation, and regulatory compliance. Financial institutions must be able to explain how risk scores are generated and demonstrate that modeling decisions are based on measurable evidence.

This requirement strongly influences model selection because highly interpretable models are easier to audit, validate, and justify to regulators. Every transformation, feature engineering step, and prediction must be documented and reproducible.

As a result, model explainability becomes nearly as important as predictive performance.

---

## 2. Why a Proxy Variable Is Necessary

The dataset does not contain a direct indicator showing whether a customer defaulted on a loan. Since supervised machine learning requires labeled target variables, a proxy measure must be created.

The proposed approach uses customer transaction behavior through Recency, Frequency, and Monetary (RFM) analysis. Customers exhibiting low engagement, infrequent transactions, and low spending activity may be considered higher risk compared with active customers.

The proxy target will therefore classify customers into high-risk and low-risk segments based on behavioral clustering.

### Business Risks of Proxy-Based Targets

Although proxy variables allow model development, they introduce several risks:

* The proxy may not perfectly represent actual default behavior.
* Customers may be incorrectly classified.
* Biases introduced during clustering may affect model performance.
* Predictions should be interpreted as risk estimates rather than direct default probabilities.

Therefore, all assumptions used to construct the proxy target must be clearly documented.

---

## 3. Model Trade-Offs in a Regulated Environment

### Logistic Regression with WoE

Advantages:

* Highly interpretable
* Easy to explain to regulators
* Stable performance
* Transparent feature contribution

Disadvantages:

* May fail to capture complex nonlinear relationships
* Lower predictive performance in some cases

### Gradient Boosting Models

Advantages:

* Strong predictive performance
* Handles nonlinear relationships effectively
* Often achieves higher ROC-AUC scores

Disadvantages:

* Reduced interpretability
* More difficult to explain to regulators
* Increased model complexity

### Recommended Approach

A balanced strategy is to evaluate both interpretable and high-performance models. If a more complex model significantly outperforms simpler alternatives, explainability tools such as SHAP should be used to improve transparency while maintaining predictive accuracy.

---

# Project Objectives

1. Explore transaction-level customer behavior.
2. Engineer meaningful credit-risk features.
3. Create a proxy target variable using RFM analysis.
4. Train and compare multiple classification models.
5. Track experiments using MLflow.
6. Deploy the best model through a FastAPI service.
7. Automate testing and deployment through CI/CD.

---

# Current Progress (Interim Submission)

Completed:

* Repository initialization
* Project structure setup
* Business understanding analysis
* Initial Exploratory Data Analysis (EDA)

In Progress:

* Feature engineering
* RFM segmentation
* Proxy target construction

Planned:

* Model training
* MLflow tracking
* FastAPI deployment
* Docker containerization
* CI/CD automation

---

# Tools and Technologies

* Python
* Pandas
* NumPy
* Scikit-Learn
* MLflow
* FastAPI
* Docker
* GitHub Actions
* DVC
* SHAP

---

# Dataset

The project uses transaction-level records from the Xente eCommerce platform containing customer activity, transaction values, channels, products, timestamps, and fraud indicators.

The dataset will be transformed into a customer-level analytical dataset suitable for credit risk modeling.

---

# Expected Deliverables

* EDA Notebook
* Feature Engineering Pipeline
* RFM-Based Proxy Target
* Credit Risk Classification Models
* MLflow Experiment Tracking
* FastAPI Risk Scoring Service
* Dockerized Deployment
* Final Medium-Style Report
