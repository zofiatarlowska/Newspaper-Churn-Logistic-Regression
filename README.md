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
### Dataset Characteristics and Class Imbalance
- The dataset exhibits a significant class imbalance, with approximately **19% churned** and **81% retained customers**.
- Due to this imbalance, accuracy alone was considered insufficient for evaluation, motivating the use of **F1-score and ROC-AUC** as primary performance metrics.
- Class imbalance was further addressed using **class-weighted Logistic Regression**.

### Data Quality and Preprocessing
- Several variables contained missing values (e.g. *Age range*, *Language*, *weekly fee*, *Nielsen Prizm*).
- To prevent data leakage, **no imputation was performed prior to the train-test split**.
- Missing values were handled exclusively within the preprocessing pipeline.

### Feature Selection and Dimensionality Reduction
- Identifier and non-informative features such as *SubscriptionID* and *State* were removed.
- High-cardinality location-based features (*Address*, *Zip Code*, *City*) were excluded to reduce dimensionality and avoid sparse feature representations.
- These steps improved model stability and interpretability.

### Feature Engineering (Nielsen Prizm)
- The *Nielsen Prizm* variable was decomposed into two interpretable features:
  - **Life_Stage** (categorical),
  - **Maturity_Level** (ordinal).
- The original *Nielsen Prizm* feature was removed after extraction to avoid redundancy.

### Data Splitting Strategy
- The dataset was split into training and test sets using an **80/20 stratified split**.
- Stratification ensured consistent class distribution across both sets.

### Encoding, Scaling, and Modeling
- Numerical features were scaled using **StandardScaler**.
- Categorical features were encoded using **One-Hot Encoding** with safe handling of unseen categories.
- All preprocessing steps were integrated into a single **Pipeline** together with the classifier to ensure methodological correctness.

### Model Training and Optimization
- **Logistic Regression** was selected due to its interpretability and suitability for binary classification.
- Hyperparameters were optimized using **GridSearchCV** with stratified cross-validation.
- The **F1-score** was used as the optimization metric.

---

## Final Results and Evaluation
The trained Logistic Regression model was assessed on an independent test set representing 20% of the available data. Due to the pronounced class imbalance,evaluation focused on metrics that better reflect minority-class performance.

The model achieved a **ROC-AUC of approximately 0.84**, indicating a strong ability to distinguish between customers who churned and those who remained subscribers across a range of decision thresholds.

Performance on the churn class shows a **recall of around 70%**, meaning that the majority of churned customers were correctly identified by the model. The corresponding **F1-score of approximately 0.53** reflects a balanced trade-off between precision and recall under imbalanced class conditions.

Overall accuracy reached approximately **76%**, which is lower than the majority-class baseline. This behavior is expected, as the model is explicitly optimized to improve detection of churned customers rather than maximizing overall accuracy.
---

## Conclusions

The results demonstrate that a carefully designed preprocessing pipeline combined with interpretable modeling techniques can effectively capture meaningful patterns in customer churn data. The project emphasizes methodological correctness and robust evaluation rather than maximizing predictive performance.
