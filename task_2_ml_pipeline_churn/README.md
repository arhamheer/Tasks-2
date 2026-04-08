# Task 2: End-to-End ML Pipeline with Scikit-learn

## Overview

This task demonstrates building a production-ready machine learning pipeline from scratch using scikit-learn. The goal is to predict customer churn (whether a customer will cancel their service) using a structured ML pipeline that handles all preprocessing, training, and evaluation steps in a single, reproducible workflow.

This exemplifies industry best practices for ML development, showing how to build systems that are maintainable, testable, and deployable to production environments. The pipeline ensures consistency between training and inference by bundling preprocessing with the model.

## Problem Statement

Given historical customer data (demographics, services, account information), predict whether each customer will churn or not. This is a critical business problem for telecom, SaaS, and subscription companies, directly impacting revenue and customer retention strategies.

## What You'll Learn

- **ML Pipeline Construction:** Bundling preprocessing and models for end-to-end consistency
- **Feature Preprocessing:** Encoding categorical variables and scaling numerical features
- **Model Selection:** Comparing multiple algorithms (Logistic Regression, Random Forest)
- **Hyperparameter Tuning:** Using GridSearchCV for automated parameter optimization
- **Cross-Validation:** Validating model reliability across different data splits
- **Model Export:** Saving pipelines for production deployment
- **Evaluation Metrics:** Understanding precision, recall, F1-score, and AUC-ROC

## Dataset Details

- **Name:** Telco Customer Churn Dataset
- **Source:** Manually provided or loaded from GitHub
- **Size:** Typically 7,000+ customer records
- **Features:** 20 attributes including:
  - Demographics: Age, gender, senior citizen status
  - Services: Phone, internet, security, backup services
  - Account: Contract length, monthly charges, total charges
- **Target:** Churn (Yes/No - binary classification)
- **Challenge:** Imbalanced classes (lower churn rate in real data)

## Technical Architecture

### Components Used

1. **scikit-learn** - ML algorithms and pipeline infrastructure
2. **Pandas** - Data loading and manipulation
3. **Numpy** - Numerical operations
4. **joblib** - Saving/loading trained pipelines
5. **Matplotlib & Seaborn** - Visualization

### Algorithm Comparison

The pipeline trains and compares:
- **Logistic Regression:** Simple, interpretable baseline model
- **Random Forest:** Ensemble method catching complex patterns
- **Model Selection:** Choose best performer based on cross-validation scores

## Workflow / Implementation Steps

### 1. Data Loading and Exploration
- Load Telco churn dataset (CSV format)
- Examine feature distributions and data types
- Identify categorical vs numerical features
- Check for missing values
- Analyze churn distribution (class balance)

### 2. Feature Preprocessing Pipeline
The pipeline automatically:
- **Categorical Encoding:** Convert text categories to numbers (OneHotEncoder for categorical, LabelEncoder for binary)
- **Numerical Scaling:** Standardize numerical features to mean=0, std=1 (StandardScaler)
- **Missing Value Handling:** Fill or drop missing values
- **Feature Selection:** Keep relevant features

### 3. Train-Test Split
- Split data: 80% training, 20% testing
- Ensures model is evaluated on unseen data
- Prevents data leakage by fitting encoders on training data only

### 4. Model Training with Pipeline

The pipeline structure:
```
Raw Data -> Preprocessing -> Feature Scaling -> Model -> Predictions
```

Each model is trained within the pipeline:
- Training data goes through all preprocessing steps
- Features feed into the ML model
- Model learns patterns that predict churn

### 5. Hyperparameter Tuning (GridSearchCV)
- Define parameter grid (e.g., learning rate, tree depth)
- GridSearchCV automatically tests all combinations
- 5-fold cross-validation evaluates each combination
- Select parameters producing best mean CV score

### 6. Evaluation on Test Set
After selecting best model, evaluate final performance:
- **Accuracy:** Percentage of correct predictions
- **Precision:** Of predicted churners, how many actually churned
- **Recall:** Of actual churners, how many were identified
- **F1-Score:** Harmonic mean balancing precision and recall
- **Confusion Matrix:** Breakdown of correct/incorrect predictions
- **AUC-ROC:** Overall discrimination ability

### 7. Pipeline Persistence
- Save entire pipeline (preprocessing + model) to `.pkl` file
- Load and reuse for new customer predictions
- Ensures preprocessing matches training (no data leakage)

## What Gets Saved

After execution, the notebook produces:
- **Pipeline File:** `churn_pipeline.pkl` - complete preprocessing + model
- **Evaluation Report:** Accuracy, precision, recall, F1-score, AUC-ROC
- **Confusion Matrix:** Visual breakdown of predictions
- **ROC Curve:** Performance visualization
- **Feature Importance:** Which features most influence predictions (Random Forest)
- **Best Parameters:** The hyperparameters that performed best

## Expected Performance

- **Deployment Accuracy:** 80-85% on new customer data
- **Precision:** 65-75% (when predicting churn, usually correct)
- **Recall:** 50-60% (catches majority of churners)
- **F1-Score:** 0.75-0.85 (good balance)
- **AUC-ROC:** 0.85+ (strong discrimination ability)
- **Training Time:** <1 minute

## Key Technologies & Libraries

| Technology | Purpose | Version |
|-----------|---------|---------|
| scikit-learn | ML algorithms and pipeline | 1.3.0 |
| Pandas | Data handling | 2.0.0 |
| Numpy | Numerical operations | 1.24.0 |
| joblib | Model serialization | 1.3.0 |
| Matplotlib/Seaborn | Visualization | 3.7.0/0.12.0 |

## Pipeline Reusability Example

Once trained and saved, the pipeline works like this:

```python
import joblib

# Load the saved pipeline
pipeline = joblib.load('churn_pipeline.pkl')

# New customer data (raw, like training data)
new_customer = pd.DataFrame({
    'age': [35],
    'monthly_charges': [89.50],
    'contract': ['Month-to-month'],
    # ... other features
})

# Get prediction (preprocessing happens automatically)
prediction = pipeline.predict(new_customer)  # 'Yes' or 'No'
probability = pipeline.predict_proba(new_customer)  # Confidence scores
```

## Installation and Execution

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run the notebook:
   ```bash
   jupyter notebook task_2_notebook.ipynb
   ```

3. Execute cells sequentially to:
   - Load and explore data
   - Build and train pipeline
   - Optimize hyperparameters
   - Evaluate on test set
   - Save for production

## Practical Applications

- **Customer Retention:** Identify high-risk customers early
- **Resource Allocation:** Focus retention efforts on likely churners
- **Pricing Strategy:** Adjust offers based on churn probability
- **Business Intelligence:** Understand reasons for churn
- **A/B Testing:** Measure campaign effectiveness on churn rates

## Best Practices Demonstrated

1. **Pipeline Pattern:** Prevents train-test mismatch errors
2. **Cross-Validation:** Robust performance estimation
3. **Hyperparameter Tuning:** Data-driven model optimization
4. **Model Persistence:** Reproducible, deployable systems
5. **Evaluation Metrics:** Appropriate metrics for business problem

## References

- scikit-learn Pipeline: https://scikit-learn.org/stable/modules/compose.html
- GridSearchCV: https://scikit-learn.org/stable/modules/grid_search.html
- Model Selection: https://scikit-learn.org/stable/model_selection.html
- Telco Dataset: https://www.kaggle.com/blastchar/telco-customer-churn

## Troubleshooting

- **Memory Issues:** Reduce dataset size or use smaller models
- **Slow GridSearch:** Reduce parameter grid or use RandomizedSearchCV
- **Poor Performance:** Check data quality, feature engineering, or try different models

---

**Task Type:** Binary Classification  
**Difficulty:** Intermediate  
**Setup Date:** April 7, 2026  
**Expected Duration:** 1-1.5 hours
