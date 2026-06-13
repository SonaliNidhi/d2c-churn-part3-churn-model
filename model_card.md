# Model Card

## Model Name

D2C Customer Churn Prediction Model

---

## Business Objective

Predict whether a customer is likely to churn within the next 60 days so that retention teams can prioritize interventions and improve customer retention outcomes.

---

## Intended Use

This model is designed to:

* Identify customers at high risk of churn
* Prioritize retention campaigns
* Support CRM decision-making
* Assist marketing and customer-success teams

---

## Data Used

Primary Dataset:

* rfm_modeling_snapshot.csv

Feature Categories:

* Purchase behavior
* Customer engagement
* Support activity
* Campaign interactions
* RFM metrics
* Loyalty information

Only information available on or before the snapshot date was used.

No future or post-snapshot information was included in model training.

---

## Target Variable

churn_next_60d

Values:

* 1 = Customer churned within 60 days
* 0 = Customer retained

---

## Model Approach

### Baseline Model

Logistic Regression

Purpose:

Provide a simple and interpretable benchmark.

### Final Model

Random Forest Classifier

Purpose:

Capture non-linear customer behavior patterns and improve predictive performance.

### Optional Benchmark

XGBoost Classifier

Used for performance comparison.

---

## Performance

### Validation Metrics

| Metric    | Value |
| --------- | ----- |
| Accuracy  | XX    |
| Precision | XX    |
| Recall    | XX    |
| F1 Score  | XX    |
| ROC-AUC   | XX    |
| PR-AUC    | XX    |

### Selected Threshold

0.40

Business Justification:

The cost of missing a potential churner is higher than the cost of contacting a customer who would have stayed.

Therefore recall was prioritized.

---

## Key Predictive Features

Top features identified through feature importance and SHAP analysis:

* recency_days
* frequency_180d
* monetary_180d
* ticket_count_90d
* sessions_30d
* campaign_clicks_30d

---

## Strengths

* Uses multiple customer behavior signals
* Captures engagement patterns
* Includes support interactions
* Supports proactive retention efforts

---

## Limitations

* Snapshot-based model
* Cannot observe competitor activity
* Cannot capture all dissatisfaction drivers
* Performance may degrade as customer behavior changes

---

## Ethical Risks

Potential risks include:

* Over-targeting customers
* Biased retention prioritization
* Misinterpretation of predictions

Mitigation:

* Human review for high-value customers
* Regular monitoring and retraining
* Use predictions as decision support only

---

## Monitoring Requirements

Track:

* Data drift
* Feature drift
* Prediction distribution
* Churn rate drift
* Model performance degradation

Retraining should be considered if ROC-AUC decreases significantly or if feature distributions change materially.

---

## When This Model Should Not Be Used

This model should not be used for:

* Credit decisions
* Employment decisions
* Legal decisions
* Pricing discrimination
* Service denial

The model is intended solely for customer-retention prioritization.

---

## Responsible Use Statement

Model predictions should be treated as risk indicators rather than final decisions. Business teams should combine model outputs with customer context and professional judgment before taking action.
