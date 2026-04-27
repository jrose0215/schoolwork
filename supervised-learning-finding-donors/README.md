# Supervised Learning: Finding Donors for CharityML

## Overview
Applied and compared three supervised learning algorithms to predict whether an individual earns more than $50,000 annually using 1994 U.S. Census data. The goal mirrors a real-world non-profit use case: identifying likely donors to maximize outreach efficiency. The best-performing model was then optimized using grid search.

## Research Question
**Which individuals are most likely to earn above $50,000 and therefore be viable donor candidates for CharityML?**

## Dataset
`census.csv` — demographic records from the 1994 U.S. Census including age, education, occupation, marital status, capital gains/losses, and hours worked per week. Target label: income (>50K or <=50K).

## Project Workflow

### 1. Data Exploration
Calculated class distribution — roughly 24.8% of individuals earn above $50K — and established a naive predictor baseline (accuracy: 0.2478, F-score: 0.2917) to benchmark model performance against.

### 2. Data Preprocessing
- Applied log transformation to skewed features (`capital-gain`, `capital-loss`)
- Normalized all numerical features using MinMaxScaler
- One-hot encoded all categorical variables (103 total features after encoding)
- Split data 80/20 into training and test sets

### 3. Model Evaluation
Trained and compared three classifiers at 1%, 10%, and 100% of training data:

| Model | Accuracy | F-score |
|-------|----------|---------|
| Logistic Regression | 0.8576 | ~0.68 |
| Random Forest | — | ~0.70 |
| **AdaBoost** | **0.8576** | **~0.73** |

AdaBoost was selected as the best model based on highest F-0.5 score on the full test set.

### 4. Model Tuning
Optimized AdaBoost using GridSearchCV, tuning `n_estimators` and `learning_rate`:

| Metric | Unoptimized | Optimized |
|--------|-------------|-----------|
| Accuracy | 0.8576 | **0.8651** |
| F-score | 0.7246 | **0.7396** |

### 5. Feature Importance
Extracted and ranked feature importances from the final AdaBoost model. Top 5 features: `capital-loss`, `age`, `capital-gain`, `hours-per-week`, `education-num`. A reduced model using only these 5 features still significantly outperformed the naive baseline (accuracy: 0.8385, F-score: 0.6920), demonstrating that a small feature subset retains most predictive power.

## Tools & Skills
- **Language:** Python
- **Libraries:** pandas, numpy, matplotlib, scikit-learn
- **Techniques:** Log transformation, MinMax scaling, one-hot encoding, naive baseline benchmarking, model comparison, GridSearchCV hyperparameter tuning, feature importance extraction
- **Models:** Logistic Regression, Random Forest, AdaBoost
- **Metrics:** Accuracy, F-beta score (β=0.5)

## Files
| File | Description |
|------|-------------|
| `finding_donors.ipynb` | Full notebook with preprocessing, model training, tuning, and feature analysis |
