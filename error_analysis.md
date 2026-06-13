# Error Analysis

## Objective

The purpose of this analysis is to understand where the churn prediction model makes mistakes and evaluate the business impact of those errors.

Two types of prediction errors were analyzed:

1. False Positives
2. False Negatives

---

# False Positives

## Definition

False Positives are customers predicted to churn who ultimately did not churn.

### Business Impact

* Unnecessary retention spending
* Additional campaign costs
* Reduced campaign efficiency

### Potential Reasons

* Customer re-engaged after scoring
* Campaign response not fully captured
* Temporary inactivity misinterpreted as churn risk

---

## False Positive Customer Examples

| Customer ID | Predicted Probability | Key Signals                | Interpretation                       |
| ----------- | --------------------- | -------------------------- | ------------------------------------ |
| ACTUAL_ID_1 | 0.84                  | High recency, low sessions | Customer returned despite inactivity |
| ACTUAL_ID_2 | 0.79                  | Multiple support tickets   | Complaint resolved successfully      |
| ACTUAL_ID_3 | 0.76                  | Low engagement             | Customer resumed purchasing          |
| ACTUAL_ID_4 | 0.73                  | Declining frequency        | Customer responded to campaign       |
| ACTUAL_ID_5 | 0.71                  | High return rate           | Customer remained active             |

### Summary

Most false positives were customers showing temporary disengagement but who later re-engaged with the brand.

---

# False Negatives

## Definition

False Negatives are customers predicted as safe who ultimately churned.

### Business Impact

* Lost revenue
* Lost customer lifetime value
* Missed retention opportunities

### Potential Reasons

* Hidden dissatisfaction
* Product quality issues
* Competitive switching behavior
* Rapid engagement decline

---

## False Negative Customer Examples

| Customer ID  | Predicted Probability | Key Signals             | Interpretation              |
| ------------ | --------------------- | ----------------------- | --------------------------- |
| ACTUAL_ID_6  | 0.21                  | Moderate activity       | Churn occurred unexpectedly |
| ACTUAL_ID_7  | 0.24                  | Good purchase history   | Sudden disengagement        |
| ACTUAL_ID_8  | 0.27                  | Few complaints          | Hidden dissatisfaction      |
| ACTUAL_ID_9  | 0.31                  | Strong historical spend | Competitor migration        |
| ACTUAL_ID_10 | 0.35                  | Average engagement      | Unobserved churn drivers    |

### Summary

False negatives represent the highest business risk because these customers churned without receiving retention intervention.

---

# Error Comparison

| Error Type     | Business Cost |
| -------------- | ------------- |
| False Positive | Moderate      |
| False Negative | High          |

---

# Business Recommendation

The company should prioritize recall over precision because the cost of missing a churner is higher than the cost of contacting a customer who would have remained active.

A slightly lower prediction threshold is therefore justified to reduce false negatives.

---

# Key Takeaways

1. False negatives create the greatest revenue risk.
2. Support-ticket activity remains an important churn indicator.
3. Customer inactivity is the strongest churn signal.
4. Hidden dissatisfaction may not be fully captured by current features.
5. Future model iterations should incorporate richer engagement signals.
