# Newspaper Subscription Churn Prediction

This project focuses on building a binary classification model to predict
customer churn for a newspaper subscription service. It was completed as a preliminary Machine Learning task as part of
the recruitment process for CERN.

---

## Dataset and Model

- **Dataset:** Newspaper subscription dataset  
  https://www.openml.org/search?type=data&sort=runs&id=44226&status=active
- **Model:** Logistic Regression

---

## Methodology

The project follows a complete and methodologically sound machine learning pipeline:

- Exploratory data analysis and identification of data quality issues
- Removal of non-informative and high-cardinality features
- Feature engineering of the *Nielsen Prizm* variable into interpretable components
- Stratified train-test split to preserve class distribution
- Preprocessing (imputation, scaling, and encoding) performed inside a single pipeline
  to prevent data leakage
- Hyperparameter tuning using GridSearchCV with stratified cross-validation

---

## Evaluation

Model performance was evaluated on a held-out test set using metrics appropriate
for imbalanced data:

- **F1-score**
- **ROC-AUC**

The final model achieved a ROC-AUC of approximately **0.84**, indicating good
discriminative ability between churned and retained customers.

---

## Conclusions

The results demonstrate that a carefully designed preprocessing pipeline combined
with interpretable modeling techniques can effectively capture meaningful patterns
in customer churn data. The project emphasizes methodological correctness and
robust evaluation rather than maximizing predictive performance.
