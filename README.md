# Credit-Card-Fraud-Detection-System

##  Project Overview

This project builds an end-to-end machine learning system to detect fraudulent credit card transactions. The dataset is highly imbalanced, making this a realistic and challenging problem in financial risk modeling.

The goal is to accurately identify fraudulent transactions while minimizing false positives to avoid disrupting legitimate customers.


##  Objectives

* Detect fraudulent transactions in an extremely imbalanced dataset (~0.17% fraud rate)
* Optimize model performance using **precision-recall trade-offs**
* Reduce false positives while maintaining high fraud detection
* Build an interpretable, production-ready ML pipeline


##  Dataset

* Source: Kaggle – Credit Card Fraud Detection Dataset
* Transactions: 284,807
* Fraud Cases: 492 (0.172%)
* Features:

  * **V1–V28**: PCA-transformed features (confidential)
  * **Time**: Seconds elapsed between transactions
  * **Amount**: Transaction value
  * **Class**: Target variable (1 = Fraud, 0 = Normal)


##  Project Workflow

### 1. Exploratory Data Analysis (EDA)

* Checked class imbalance
* Analyzed feature distributions
* Correlation analysis (heatmap)


### 2. Data Preparation

* Train-test split using stratification
* No leakage between training and test data


### 3. Baseline Model

* Logistic Regression with class weighting
* Identified high recall but extremely low precision


### 4. Model Improvements

* Applied **SMOTE** to handle class imbalance
* Trained:

  * Random Forest
  * XGBoost (final model)


### 5. Threshold Tuning

* Evaluated models using threshold = **0.8**
* Optimized trade-off between:

  * Fraud detection (Recall)
  * False positives (Precision)


### 6. Evaluation Metrics

Due to class imbalance, accuracy was not used.

Key metrics:

* Precision
* Recall
* F1 Score
* ROC-AUC
* PR-AUC (Primary metric)



##  Model Performance (Threshold = 0.8)

| Model               | Precision | Recall   | F1 Score | ROC-AUC  | PR-AUC   |
| ------------------- | --------- | -------- | -------- | -------- | -------- |
| Logistic Regression | 0.24      | 0.89     | 0.38     | 0.97     | 0.71     |
| Random Forest       | *0.95*    | 0.79     | 0.86     | 0.97     | 0.88     |
| XGBoost             | 0.91      | *0.82*   | *0.86*   | *0.98*   | *0.88*   |


##  Final Model Selection

**XGBoost (Threshold = 0.8)** was selected as the final model because:

* Highest **PR-AUC (0.8788)**
* Better **recall** than Random Forest
* Strong balance between fraud detection and false positives


##  Business Impact

At the selected threshold:

* High fraud detection rate (~82%)
* Very low false positives
* Improved customer experience by reducing unnecessary transaction blocks

This demonstrates a practical balance between **risk management and user experience**, which is critical in financial systems.



##  Model Explainability (SHAP)

SHAP (SHapley Additive Explanations) was used to interpret model predictions.

### Key Insights:

* Most important features: **V14, V4, V12, V10**
* Fraud is driven by complex interactions between PCA-transformed features
* Transaction **Amount** and **Time** have low importance

This improves:

* Transparency
* Trust in model decisions
* Interpretability for stakeholders


##  Key Learnings

* Accuracy is misleading in imbalanced datasets
* PR-AUC is a better metric for fraud detection
* Threshold tuning is critical for real-world deployment
* Tree-based models outperform linear models in complex datasets
* Explainability is essential in financial applications


##  Tech Stack

* Python
* Pandas, NumPy
* Scikit-learn
* XGBoost
* Imbalanced-learn (SMOTE)
* SHAP
* Matplotlib / Seaborn


##  Project Structure


fraud-detection/
│
├── data/
├── notebooks/
│   └── fraud_detection.ipynb
├── models/
├── reports/
├── README.md




##  Future Improvements

* Hyperparameter tuning (GridSearch / Optuna)
* Real-time fraud detection API (FastAPI)
* Model deployment (Docker / Cloud)
* Feature engineering with temporal patterns


##  Author

**Chibueze S. Imediegwu**
Data Scientist | Machine Learning Engineer



##  If You Found This Useful

Give this repo a star ⭐
