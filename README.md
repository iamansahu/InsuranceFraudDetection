# Insurance Fraud Detection

## Project Overview
Insurance fraud costs the industry billions of dollars annually, leading to increased premiums for genuine policyholders. This project aims to develop a Machine Learning (ML) model to predict fraudulent claims based on transactional data, automating fraud detection, improving accuracy, and reducing the manual workload for investigators.

## Dataset and Data Preprocessing
### Data Source
- 10,000+ insurance claims scraped from the CLUE website using BeautifulSoup.

### Feature Selection & Cleaning
- Initial dataset: 39 columns.
- Dropped non-relevant features (e.g., policy number, incident location, auto details).
- Missing values replaced with NaN and handled via categorical imputation.
- Final dataset: 26 features, including:
  - **Policy details**: policy_csl, policy_deductible, policy_annual_premium
  - **Insured details**: age, education level, occupation, relationship
  - **Incident details**: type, severity, authorities contacted, time of day, vehicles involved
  - **Claim details**: total claim amount, injury claim, vehicle claim, property claim
  - **Target Variable**: `fraud_reported` (Binary: Fraud or Not Fraud)

### Feature Engineering
- Categorical variables encoded using custom mappings (e.g., `incident_severity` mapped numerically from Trivial to Total Loss).
- One-hot encoding applied to categorical columns (e.g., occupation, relationship, authorities contacted).
- Removed highly correlated variables (e.g., age vs. months as customer, total claim amount vs. claim components).

## Model Development
### Models Implemented
#### Support Vector Machine (SVM)
- Hyperparameter tuning with `GridSearchCV`.
- Used `rbf` and `sigmoid` kernels.
- Performance was poor due to feature scaling and dataset imbalance.

#### XGBoost (Extreme Gradient Boosting)
- Outperformed SVM in fraud detection.
- Hyperparameter tuning on:
  - `n_estimators`: Number of boosting rounds.
  - `max_depth`: Maximum tree depth.
  - `criterion`: Gini or entropy.
- Final accuracy: **73.6% on test data**.

## Model Evaluation
- **Confusion Matrix**: Analyzed TP, FP, TN, FN.
- **Performance Metrics**:
  - **Accuracy**: 73.6%
  - **Precision**: Correctness of fraud predictions.
  - **Recall**: Ability to detect fraud cases.
  - **F1-score**: Balance between precision and recall.
  - **AUC-ROC Curve**: Assessed model's ability to distinguish between fraud and non-fraud claims.

## Impact & Business Value
- Automates claim verification, reducing manual workload.
- Detects fraudulent claims early, minimizing financial losses.
- Enhances customer experience by speeding up valid claim approvals.

## Tools & Technologies Used
- **Python**: Pandas, NumPy, Pandas, Scikit-learn, XGBoost
- **Web Scraping**: BeautifulSoup
- **Feature Engineering**: Feature-engine library
- **Model Tuning**: GridSearchCV
- **Data Visualization**: Seaborn, Matplotlib
