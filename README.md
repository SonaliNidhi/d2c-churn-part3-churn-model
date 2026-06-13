# D2C Customer Churn Prediction

## Project Objective

The objective of this project is to predict whether a customer will churn within the next 60 days and provide actionable insights that support customer retention strategies.

Target Variable:

churn_next_60d

---

## Dataset

Source:

rfm_modeling_snapshot.csv

The dataset contains customer-level behavioral, transactional, engagement, and support features generated as of the snapshot date.

Important:

Only information available on or before the snapshot date was used for model training.

No post-snapshot information was included as model features.

---

## Leakage Prevention

The project explicitly prohibits the use of future information.

The following controls were implemented:

* Only snapshot-safe features were used.
* Post-snapshot transactions were excluded.
* Target-window information was never used as input.

---

## Data Split

The dataset provides predefined splits:

| Split      | Purpose             |
| ---------- | ------------------- |
| Train      | Model Training      |
| Validation | Threshold Selection |
| Test       | Final Evaluation    |

---

## Features Used

Examples:

* recency_days
* frequency_180d
* monetary_180d
* category_diversity_180d
* ticket_count_90d
* sessions_30d
* campaign_clicks_30d
* loyalty_tier

---

## Models

### Baseline Model

Logistic Regression

### Advanced Model

Random Forest Classifier

### Optional Bonus Model

XGBoost Classifier

---

## Evaluation Metrics

The following metrics were used:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* PR-AUC

---

## Threshold Selection

Multiple probability thresholds were evaluated.

The final threshold was selected based on the trade-off between:

* Precision
* Recall
* Business impact

A lower threshold was preferred because missing a likely churner is more costly than contacting a non-churner.

---

## Model Explainability

Feature importance analysis was performed using:

* Random Forest Feature Importance
* SHAP Values

Generated Outputs:

* feature_importance.png
* shap_summary.png

---

### Threshold Selection

Multiple decision thresholds were evaluated using the validation dataset.

Observations:

- Lower thresholds increase recall but reduce precision.
- Higher thresholds increase precision but reduce recall.
- A threshold of 0.40 provides a balanced trade-off between precision and recall.
- From a business perspective, missing a churner (False Negative) is more costly than contacting a customer who would have stayed (False Positive).

Therefore, 0.40 was selected as the operational threshold.

## Repository Structure

d2c-churn-part3-churn-model/

├── README.md

├── churn_model.ipynb

├── model.pkl

├── metrics.json

├── error_analysis.md

├── model_card.md

├── requirements.txt

└── outputs/

---

## Generated Outputs

### Model Artifact

model.pkl

### Metrics

metrics.json

### Evaluation Charts

* roc_curve.png
* pr_curve.png
* confusion_matrix.png

### Explainability Charts

* feature_importance.png
* shap_summary.png

---

## Error Analysis

Error analysis includes:

* False Positives
* False Negatives
* Minimum 10 customer examples
* Business impact assessment

See:

error_analysis.md

---

## Model Documentation

A detailed model card is provided:

model_card.md

The model card includes:

* Intended Use
* Limitations
* Ethical Considerations
* Monitoring Requirements
* Responsible Usage Guidelines

---

## How to Run

Install dependencies:

pip install -r requirements.txt

Launch google colab 

colab

Open:

churn_model.ipynb

Run all cells sequentially.

---

## Deliverables

* Churn Prediction Model
* Saved Model Artifact
* Evaluation Metrics
* Error Analysis
* Explainability Analysis
* Model Card
